# Komunikacja Bluetooth w ProteGO

Niniejszy dokument opisuje pełną specyfikację urządzenia komunikującego się po
Bluetooth Low Energy zgodnego z aplikacją ProteGO. Zawarte są również
informacje o ograniczeniach napotkanych na platformach iOS oraz Android, które
wpłynęły na ostateczną implementację.

Aplikacje rozgłaszają się identyfikatorami `beacon_id`. Aplikacja zmienia
`beacon_id` co godzinę. Aplikacja uzupełnia pulę identyfikatorów `beacon_id`
tak aby mieć zapas na kolejne 21 dni za każdym uruchomieniem funkcji API
`/get_status`.

Podstawowe założenia:

* Możliwość wymieniania się `beacon_id` w czasie działania aplikacji oraz w tle.
* Przesyłanie tylko `beacon_id` oraz informacji o mocy sygnału.

## Format ramki rozgłoszeniowej (Advertisement Data)

Urządzenie ProteGO powinno rozgłaszać następujące dane:

* Flags (CSS v9, Part A, 1.3) (wymagane)
* Tx Power (CSS v9, Part A, 1.5) (opcjonalne)
* Manufacturer Specific Data (CSS v9, Part A, 1.4) (opcjonalne, patrz uwaga #2))
    * Pierwsze 2 bajty to Company ID o wartości `0x08AF`
    [(Polidea)](https://www.bluetooth.com/specifications/assigned-numbers/company-identifiers/)
    zapisane w formacie little-endian.
    * Kolejny bajt to wersja. Stała wartość `0x00` dla ProteGO.
    * Kolejne 16 bajtów to `beacon_id`.
* 16-bit UUID (CSS v9, Part A, 1.0) (wymagane)
    * Dwubajtowa wartość `FD6E`
    [(ProteGO)](https://www.bluetooth.com/specifications/assigned-numbers/16-bit-uuids-for-members/) zapisana w formacie little-endian.

Przykładowa ramka może wyglądać następująco:

```
02 01 1A | 02 0A 0C | 03 03 6E FD | 13 FF AF 08 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15 16 |
```

Oznaczająca:

* Flags:
    * LE General Discoverable Mode
    * Simultaneous LE and BR/EDR (Controller)
    * Simultaneous LE and BR/EDR (Host)
* Tx Power:
    * 12 dB
* UUID:
    * 16 bitowe, zarezerowane UUID o wartości `FD6E` (ProteGO)
* Manufacturer Specific Data:
    * Company Id `08AF` (Polidea)
    * Wersja `00` (ProteGO)
    * 16 bajtowy `beacon_id` `01020304050607080910111213141516`

Zakładając, że wszystkie powyższe pola są zawarte limit 31 bajtów dla
Advertisement Data jest wyczerpany.

### Uwagi

1. W momencie wygaśnięcia `beacon_id`, aplikacja powinna zaprzestać rozgłaszania
   się ze starym `beacon_id` i rozpocząć nowe rozgłaszanie.

2. iOS pozwala jedynie na rozgłaszanie lokalnej nazwy (tylko gdy aplikacja jest
   aktywna) oraz UUID rozgłaszanego serwisu. W momencie gdy aplikacja przechodzi
   do tła "rozgłaszane" jest tylko UUID w formacie znanym urządzeniom Apple
   (tzw. overflow UUID).

3. Wcześniej rozważano użycie pola `Service Data`, które nie wymaga rejestracji
   UUID, jednak napotkano problem w wykrywaniu takich urządzeń w tle przez
   aplikację iOS.

4. Podanie pola UUID jest wymagane, gdyż iOS bez niego nie jest w stanie
   wykrywać urządzeń w tle.

5. Android w momencie połączenia z `GattServer` natychmiast generuje nowy MAC
   address co zmienia zawartość rozgłoszenia. Dlatego też by ograniczyć napływ
   nowych, sztucznych kontaktów, wymagane jest zawarcie unikalnego (na czas
   jednej godziny) pola w manufacturer data.

6. Na chwilę obecną tylko telefony z Androidem pozwalają na rozgłaszanie
   własnego Manufacturer Specific Data (iOS pozwala tylko na UUID i to z
   ograniczeniami). Takie połączenie powinno być traktowane jako jednorazowe,
   gdyż kolejne połączenie będzie miało inny MAC address. Na podstawie zawartego
   `beacon_id` w Manufacturer Specific Data można agregować urządzenia z innym
   MAC address.

## Format tabeli atrybutów (GATT)

Ze względu na ograniczenia po stronie aplikacji iOS, do specyfikacji dodano
serwis oraz charakterystykę ProteGO, która pozwala na odebranie oraz przesłanie
swojego `beacon_id`:

* Serwis ProteGO:
    * 16 bitowe UUID: `FD6E`
    * 128 bitowe UUID: `0000FD6E-0000-1000-8000-00805F9B34FB`
    * Zarezerwowane dla aplikacji ProteGO.

* Charakterystyka ProteGO:
    * 128 bitowe UUID: `89a60001-4f57-4c1b-9042-7ed87d723b4e`
    * Obsługuje operacje: `Read`, `Write`, `WriteWithoutResponse`.
    * Format danych to 16 bajtowy `beacon_id`.

### Uwagi

1) W momencie gdy `beacon_id` stracił ważność lub aplikacja go nie posiada
   wszystkie operacje powinny zwrócić: `ReadNotPermitted` lub `WriteNotPermitted`
   w zależności od rodzaju zapytania.

2) Inne aplikacje mają możliwość zapisania swojego `beacon_id` poprzez operację
   `Write`. Jest to użyteczne w momencie, gdy dane urządzenie nie obsługuje roli
   rozgłoszeniowej.

## Uwagi implementacyjne dla GATT serwera (moduł rozgłaszający)

1) Gdy aplikacja jest aktywna, rozgłaszanie powinno być włączone z możliwie
   niskimi parametrami mocy rozgłaszania.

2) Gdy aplikacja pracuje w tle, rozgłaszanie powinno zostać ograniczone, tak aby
   zużycie baterii było jak najmniejsze oraz planer systemu operacyjnego nie
   usunął aplikacji ze względu na duże zużycie zasobów.

3) W momencie wygaśnięcia `beacon_id`, rozgłaszanie z jego wartością powinno
   zostać przerwane.

4) Ze względu na ograniczenia związane z rozgłaszaniem na iOS oraz możliwością
   braku obsługi rozgłaszania po stronie Androida zalecane jest przyjmowanie
   połączeń w celu wymiany `beacon_id` poprzez charakterystykę ProteGO.

5) Charakterystyki nie powinny przechowywać żadnych wartości.

## Uwagi implementacyjne dla GATT klienta (moduł skanujący)

1) W momencie, gdy wykryto urządzenie z poprawnym `beacon_id` w ramce
  rozgłoszeniowej:
    * Jeżeli aplikacja także wspiera rozgłaszanie, można zapisać informacje
      o kontakcie oraz zrezygnować z wykonania połączenia (założenie, że druga
      strona także mogła zeskanować kontakt – nie są znane przypadki urządzeń
      które wspierają rolę peryferium `BLE Peripheral` lecz nie wspierają
      centrali `BLE Central`).

    * Jeżeli aplikacja nie wspiera rozgłaszania, należy połączyć się z serwerem
      i wymienić `beacon_id`.

    * Do wykrytego urządzenia z `beacon_id` należy się łączyć maksymalnie raz.
      Na chwilę obecną są to tylko telefony z Androidem, które dla każdego
      połączenia generują inny MAC address.

2) W momencie, gdy wykryto urządzenie bez `beacon_id` ale z UUID ProteGO:

    * Należy połączyć się z urządzeniem
  
    * Odkryć serwisy oraz charakterystyki ProteGO.

    * Pobrać wartość `beacon_id` poprzez odczyt charakterystyki ProteGO.

    * Przesłać swój `beacon_id` poprzez zapis do charakterystyki ProteGO.
      (opcjonalnie)

3) W momencie, gdy wykryto inne urządzenie:

    * Można spróbować połączyć się z urządzeniem by zobaczyć, czy zawiera ono
      serwisy oraz charakterystyki ProteGO.

    * Sytuacja ta ma miejsce w przypadku iOS działającego w tle (urządzenie
      rozgłaszające) oraz Androida (urządzenie skanujące).

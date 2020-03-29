# Specyfikacja API serwerowego

## Format API

Parametry do każdej funkcji API przesyłamy w formacie JSON poprzez wywołanie POST. Każda z funkcji zwraca wynik w postaci JSON.

## Parametry wspólne

Każdy wywołanie zawiera zawsze następujące parametry:

`platform` : `string ("ios"|"android")`

`os_version` : `string`

`device_type` : `string`

`app_version` : `int`

`api_version` : `int`

`user_id` : `string`

`lang` : `string`

Objaśnienie:

`platform` - identyfikator platformy. Aktualnie `“android”` lub `“ios”`

`os_version` - wersja systemu operacyjnego platformy

`device_type` - typ urządzenia (np. `"iPhone X"` lub `"Android Galaxy"`)

`app_version` - numer wersji zainstalowanej aplikacji 

`api_version`  - wersja API którą wspiera aplikacja (domyślnie 1)

`user_id` - identyfikator użytkownika przyznany przez serwer. Może być pusty jeśli użytkownik nie jest jeszcze zarejestrowany.

`lang` - dwuliterowy identyfikator języka  telefonu

## Funkcja `/check_version`

Aplikacja sprawdza czy do poprawnego jej działania jest wymagana aktualizacja aplikacji.

### Parametry:
standardowe

### Wynik:

`upgrade_required` : `bool`

`upgrade_url` : `string`

Jeśli `upgrade_required` jest `true` to aplikacja informuje użytkownika, że do dalszego działania musi zainstalować nowszą wersję. `upgrade_url` zawiera w takiim wypadku `url` do odpowiedniego App Store do którego należy przekierować użytkownika. Jeśli `upgrade_required` jest `false`, aplikacja zostaje uruchomiona.

## Funkcja `/register`

Aplikacja rejestruje nowe urządzenie

### Parametry:
standardowe

`msisdn` : `string (max 15 cyfr)`

### Wynik:
`registration_id` : `uuid`

Serwer zwraca błąd jeśli msisdn nie jest z Polski (nie zaczyna się od 48). 
Serwer generuje kod rejestracyjny, wysyła go wiadomością SMS na podany numer przez bramkę SMS. Zapamiętuje datę i czas rozpoczęcia procesu rejestracji, numer telefonu i  wysłany kod. Należy zrobić zabezpieczenia przed nadużywaniem serwisu.

### Funkcja `/confirm_registration`

Aplikacja potwierdza rejestrację.

### Parametry:

standardowe

`registration_id` : `uuid`

`code` : `string`

`registration_id` - identyfikator rejestracji zwrócony przez `/register`

`code` - kod SMS odebrany przez użytkownika

### Wynik:

`user_id` : `uuid`

`error_msg` : `string`

Serwer sprawdza czy istnieje bieżąca rejestracja zgodna z parametrami. Jeśli tak, rejestruje użytkownika, zapisuje i zwraca `user_id`. Jeśli nie, zwraca `error_msg`.

## Funkcja `/get_status`

Sprawdzenie swojego statusu i pobranie `beacon_ids`.

### Parametry:

standardowe

`last_beacon_date` : `string`

`last_beacon_date` to data i godzina najstarszego `beacon_id` które jest już przechowywane na urządzeniu.

### Wynik:

`status` : `string`

`beacon_ids` : `[ {“date”: date, “beacon_id”:beacon_id}, ...]`

`date` : `data i godzina w formacie "YYYYmmddHH"`

Serwer zwraca status użytkownika: `"greeen"`, `"orange"` lub `"red"`.  Jeśli nie minęło 14 dni od zainstalowania aplikacji, status jest pomarańczowy (`"orange"`).

Serwer zwraca identyfikatory którymi ma się rozgłaszać w określonych dniach i godzinach na 7 dni do przodu. Każdy `beacon_id` to identyfikator do rozgłaszania. Każdy `date` to data i godzina w formacie `YYYYmmddHH` określająca którym  identyfikatorem `beacon_id` powinien rozgłaszać się telefon w dniu i godzinie określonej przez `date`. Serwer zwraca tylko nowe identyfikatory biorąc pod uwagę `last_beacon_date`

## Funkcja `/send_encounters`

Wysłanie listy napotkanych urządzeń.

### Parametry:
`proof` : `string`
`encounters` : `[{“encounters_date”: datetime, “beacon_id”, “signal_strength”}, …]`

`proof` - `wynik skanowania QR code TBD`
`encounters` - `lista napotkanych urządzeń`
`encounter_date` - `data i godzina spotkania`
`beacon_id` - `id napotkanego urządzenia`
`signal_strength` - `siła sygnału przy napotkaniu urządzenia`

# Dane przechowywane na serwerze

## GCP Datastore

### `Users`

`platform` : `string ("ios"|"android")`

`os_version` : `string`

`device_type` : `string`

`app_version` : `int`

`api_version` : `int`

`user_id` : `uuid`

`lang` : `string`

`msisdn` : `string`

`reg_date` : `datetime`

`last_status_requested` : `datetime`

`status` : `string`


### `Registrations`
`registration_date` : `datatime`

`registration_id` : `uuid`

`msisdn` : `string`

`code` : `string`

`is_expired` : `bool`

## GCP BigQuery

### `Beacons`

`user_id` : `uuid`

`beacon_id` : `uuid`

`date` : `string w formacie YYYYmmddhh w czasie CET`

### `Encounters`

`user_id` : `uuid`

`beacon_id` : `uuid`

`encounter_date` : `datetime`

`signal_strength` : `float`




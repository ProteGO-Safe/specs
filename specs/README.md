# Podstawowy opis aplikacji Anna

## Rodzaje użytkowników

**Użytkownik**

Każda osoba instalująca aplikację

**Lekarz**

Lekarz, diagnostyk lub pracownik GIS, który przekazuje informację Użytkownikowi o tym, że zdiagnozowano u niego SARS-CoV-2 i inicjuje przekazanie danych o dwutygodniowej historii spotkanych osób na serwer centralny.

**Administrator**

Administrator systemu

## Działanie aplikacji

### Instalacja i sprawdzenie wersji

Użytkownik instaluje i uruchamia aplikację.

### Każde uruchomienie

W przypadku braku dostępu do Internetu, aplikacja informuje o tym i nie pozwala przejść dalej.

Po uruchomieniu, aplikacja sprawdza czy zainstalowana wersja jest najnowsza i w przeciwnym wypadku Użytkownik proszony jest o zainstalowanie nowszej wersji i przekierowany jest do odpowiedniego sklepu z aplikacjami.

### Pierwsze uruchomienie

W przypadku kiedy aplikacja uruchamiana jest po raz pierwszy (nie mamy `user_id`), następuje rejestracja aplikacji. Użytkownikowi pokazywane są ekrany startowe:

* Powitanie w aplikacji
* Akceptacja regulaminu. Regulamin jako link otwierany w przeglądarce.
* Wyjaśnienie jak działa aplikacja (może być kilka ekranów)
* Prośba o włączenie Bluetooth. Aplikacja nie przechodzi dalej bez włączenia Bluetooth (chyba że nie da się skutecznie sprawdzić stanu Bluetooth, wtedy przechodzi).
* Prośba o podanie numeru telefonu. Na stałe umieszczony jest przedrostek +48.
* Po potwierdzeniu, użytkownik otrzymuje wiadomość SMS na podany numer i wpisuje 6-cyfrowy kod z wiadomości.

### Kolejne uruchomienie

Aplikacja sprawdza czy Bluetooth jest włączony. Jeśli nie, użytkownik proszony jest o włączenie Bluetooth. Aplikacja nie pozwala pójść dalej bez włączenia Bluetooth (chyba że nie da się skutecznie sprawdzić stanu Bluetooth, wtedy tylko przypomina i przechodzi).

Aplikacja odpytuje serwer i pokazuje Użytkownikowi jeden z trzech statusów:

* W przypadku jeśli wykryto interakcje z osobą zakażoną - Czerwony

    Mogłeś przebywać blisko osób u których wykryliśmy SARS-Cov-2. Zadzwoń do najbliższego GIS. Poddaj się domowej kwarantannie.
* W przypadku zainstalowania aplikacji mniej niż 2 tygodnie temu - Pomarańczowy
    
    Nie mamy wystarczających danych aby określić czy przebywałeś w okolicach osób zakażonych. Kontynuuj używanie aplikacji. Obowiązuje Cię zachowanie ostrożności i ograniczenie wyjść do minimum.
* W przeciwnym wypadku - Zielony
   
    Zachowaj standardową ostrożność. Zgodnie z naszymi informacjami nie przebywałeś w obszarach o podwyższonym ryzyku.

### Działanie w tle

Aplikacja działa w tle i na bieżąco zapisuje informacje o wykrytych urządzeniach. Zapisy starsze niż 2 tygodnie są na bieżąco kasowane. W przypadku jeśli aplikacja zostanie wyłączona podejmuje próbę włączenia się ponownie.

### Okno O Aplikacji

Użytkownik może otworzyć okno O Aplikacji. Znajdzie tam następujące dane:
* Logo aplikacji, jej wersję
* Identyfikator użytkownika (Jest to pierwsza połowa `user_id`, 8 pierwszych bajtów w formacie hex np. `Identyfikator użytkownika: a8098c1af86e11da`)
* Liczbę różnych spotkanych użytkowników aplikacji w ciągu ostatnich 2 tyg np. `Wykryłeś 24 identyfikatory aplikacji w ciągu ostatnich 2 tygodni`.
* Liczbę różnych spotkanych użytkowników aplikacji w ciągu ostatnich 24h np. `Wykryłeś 3 identyfikatory aplikacji w ciągu ostatnich 24 godzin`.
* Przycisk `Jestem chory. Prześlij dane aby ostrzec innych`, który kieruje do wysyłki danych.
* Przycisk `Zgłoś błąd` -> kieruje do https://github.com/anna-app/specs/blob/master/CONTRIBUTING.md
* Przycisk wyślij do nas e-mail.
* Gdzieś małym drukiem przycisk `Pokaż licencje używanych komponentów`

### Wysyłanie danych na serwer

W przypadku zdiagnozowania u użytkownika zakażenia SARS-CoV-2, lekarz prosi użytkownika o otwarcie aplikacji i zeskanownie kodu QR identyfikującego lekarza. Następnie urządzenie prosi o wprowadzenie identyfikatora pacjenta lub badania i historia spotkanych urządzeń jest wysyłana na serwer.
Aplikacja nie zapamiętuje tego, że Użytkownik wysyłał dane. Działa dalej tak jak poprzednio.

### Kody QR dla lekarzy
Administrator systemu generuje kody QR i przesyła je w postaci plików pdf do wydruku do lekarzy wraz z instrukcją jak przesyłać dane z aplikacji na serwer.

### Administracja

Administrator systemu otrzymuje informacje o tym, że Użytkownik przesłał dane dotyczące napotkanych urządzeń. Weryfikuje zgodność danych (nr telefonu i id pacjenta) z rejestrami medycznymi. Oznacza Użytkownika jako chorego.

Administrator otrzymuje informacje o nr telefonów użytkowników z którym mógł spotkać się chory i dacie spotkania. Manualnie zatwierdza zmianę ich statusu w aplikacji. Przekazuje numery telefonu do GIS.






# Podstawowy opis aplikacji ProteGO

## Rodzaje użytkowników

**Użytkownik**

Każda osoba instalująca aplikację

**Lekarz**

Lekarz, diagnostyk lub pracownik GIS, który przekazuje informację Użytkownikowi o tym, że zdiagnozowano u niego SARS-CoV-2 i instruuje jak przekazać dane o dwutygodniowej historii spotkanych osób na serwer centralny.

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
* Wyjaśnienie jak działa aplikacja (może być kilka ekranów)
* Prośba o włączenie Bluetooth. Aplikacja nie przechodzi dalej bez włączenia Bluetooth (chyba że nie da się skutecznie sprawdzić stanu Bluetooth, wtedy przechodzi).
* Prośba o podanie numeru telefonu. Na stałe umieszczony jest przedrostek +48. Informacja o tym, że rejestrując się ackeptuje się regulamin
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
* Identyfikator użytkownika (Jest to pierwsza połowa `user_id`, 8 pierwszych bajtów w formacie hex np. `Identyfikator użytkownika: a809-8c1a-f86e-11da`)
* Przycisk `Wyślij dane`, który kieruje do wysyłki danych.

[Wysyłanie danych na serwer](data_sharing.md)







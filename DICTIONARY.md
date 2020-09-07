### Użytkownik Końcowy

Osoba fizyczna posiadająca pełną zdolność do czynności prawnych, która po zainstalowaniu i zaakceptowaniu Regulaminu i Polityki Prywatności korzysta z STOP COVID - ProteGO Safe. 

### Użytkownik Chory

Użytkownik Końcowy, który jest Osobą Chorą oraz dokonał weryfikacji w STOP COVID - ProteGO Safe poprzez wprowadzenie Kodu PIN otrzymanego od Centrum Kontaktu.

### Centrum Kontaktu

Jednostka powiadamiająca telefonicznie o wyniku testu na COVID-19 oraz przekazująca Kod PIN Użytkownikom Aplikacji i udzielająca informacji związanych z COVID-19.

### Kod PIN

Generowanie losowo i aktywne przez pół godziny alfanumeryczne hasło przekazywane Użytkownikowi, który jest Osobą Chorą przez konsultanta Centrum Kontaktu. Kod PIN może być wprowadzony do STOP COVID - ProteGO Safe celem anonimowego potwierdzenia, że Urządzenie należy do Osoby Chorej i zainicjowania procesu analizy Ryzyka Zagrożenia oraz powiadomienia w ramach Ekspozycji na Koronawirusa.

### Diagnosis Key lub Klucz Diagnostyczny

Zbiór Kluczy Dziennych pobieranych przez Użytkowników Końcowych, który zawiera anonimowe informacje inicjujące proces analizy narażenia na zarażenie COVID-19 w ramach Modułu Analitycznego. Klucz Diagnostyczny jest przekazywany na Serwer STOP COVID - ProteGO Safe po wpisaniu do Aplikacji Kodu PIN przez Użytkownika będącego Osobą Chorą, a następnie do innych Użytkowników Końcowych w celu analizy Ryzyka Zagrożenia oraz ewentualnego przekazania informacji czy nastąpiła Ekspozycja na Koronawirusa.

### Tymczasowe Identyfikatory

 Losowe, okresowe (dziesięciominutowe) i alfanumeryczne identyfikatory rozgłaszane przez moduł Bluetooth.

 ### Poziom Zagrożenia

 Liczba z przedziału 1-8 przypisywana do każdego z ostatnich 14 Kluczy Dziennych (dni) przesyłanych na Serwer STOP COVID - ProteGO Safe, która pozwala na określenie jak duże zagrożenie stwarzał Użytkownik Chory w danym dniu.

 ### Ryzyko Zagrożenia
 
 Liczba z zakresu 0-4096 określająca, jaka jest potencjalna możliwość zagrożenia zakażenia od Użytkownika Chorego.

 ### Algorytm Oceny Ryzyka

 Model obliczający Ryzyko Zagrożenia, który bierze pod uwagę: długość spotkania, ilość dni, które minęły od spotkania, średnią siłę sygnału Bluetooth (adekwatną do odległości pomiędzy urządzeniami), Poziom Zagrożenia określony dla Użytkownika Chorego.

 ### Ekspozycja na Koronawirusa

 Kontakt Użytkownika Końcowego z Użytkownikiem Chorym potwierdzony wynikiem Algorytmu Oceny Ryzyka.

 ### Exposure Notification (EN) API lub Moduł Analityczny

 Funkcjonalność STOP COVID - ProteGO Safe umożliwiająca zapisywanie, tworzenie historii oraz analizowanie spotkania Urządzenia Użytkownika z innymi Urządzeniami Użytkowników STOP COVID - ProteGO Safe. Exposure Notification API jest oparte o Privacy-Preserving Contact Tracing API wytworzone oraz udostępnione przez Google oraz Apple. Szczegóły dotyczące Privacy-Preserving Contact Tracing API można odnaleźć tutaj: https://www.google.com/covid19/exposurenotifications/. Informacje generowane przez Exposure Notification API wraz z wynikami pracy są przechowywane lokalnie na Urządzeniu przez 14 dni. Exposure Notification API umożliwia Użytkownikowi zachowanie anonimowości.

 ### Osoba Chora lub Chory

 Osoba fizyczna, która uzyskała pozytywny wynik testu na COVID-19. Osoba Chora nie musi być Użytkownikiem.

 ### Konfiguracja Ryzyka

 Odpowiednie ustawienie i parametryzacja Algorytmu Oceny Ryzyka.

 ### Urządzenie

 Elektroniczne urządzenie za pośrednictwem, którego Użytkownik uzyskuje dostęp do STOP COVID - ProteGO Safe (tablet, smartphone itp.) z aktywnym modułem Bluetooth, systemem Android 5.0 lub wyższym z dostępem do sklepu Google Play albo z systemem iOS w wersji nie niższej niż 13.5 z dostępem do sklepu AppStore. Moduł Analityczny będzie działał jedynie w Urządzeniach z systemem Android 6.0 wspierających technologię BLE lub wyższym albo z systemem iOS w wersji nie niższej niż 13.5.

 ### Serwer STOP COVID - ProteGO Safe

 Infrastruktura chmurowa utrzymywana przez Operatora Chmury Krajowej służąca do przekazania Klucza Diagnostycznego do Urządzeń Użytkowników. Klucze Diagnostyczne nie są przechowywane na Serwerze STOP COVID - ProteGO Safe.

 ### Progressive Web App (PWA)

 Aplikacja internetowa uruchamiana tak jak zwykła strona internetowa, ale umożliwiająca stworzenie wrażenia działania jak natywna aplikacja mobilna (lub aplikacja desktopowa).

 ### Progressive Local App (PLA)

 Robocza nazwa stworzona przez jednego z developerów STOP COVID - ProteGO Safe. Pochodzi od nazwy PWA czyli Progressive Web App. Słowo "web" zostało zastąpione słowem "local", gdyż w odróżnieniu od klasycznej implementacji PWA, PLA znajduje się w obrębie urządzenia i nie wymaga internetu do działania.

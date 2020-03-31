# Przesyłanie danych z aplikacji ProteGO na serwer

Aplikacja zbiera i przechowuje na telefonie identyfikatory innych urządzeń na których również zainstalowana jest aplikacja i które znajdują się w pobliżu. Identyfikatory są losowe, zmieniają się co godzinę i nie pozwalają ujawnić do kogo należy napotkane urządzenia. Aplikacja przechowuje informacje z ostatnich 2 tygodni. Starsze informacje są usuwane na bieżąco.

Pracownicy GIS / Centralnego Rejestru Zakażeń (CRZ) mogą sprawdzić w systemie ProteGO czy nowo-zakażona osoba jest użytkownikiem aplikacji ProteGO. Sprawdzenie następuje na podstawie numeru telefonu chorego. System ProteGO pokazuje również czy i kiedy chory przesłał swoje dane dotyczące napotkanych urządzeń.

W przypadku jeśli osoba zakażona jest użytkownikiem ProteGO, pracownik GIS/CRZ dzwoni do niej lub wysyła wiadomość SMS z prośbą o przesłanie danych z ProteGO do systemu centralnego. Przykład wiadomości:

```Dziękujemy za korzystanie z aplikacji ProteGO. Prześlij informację o osobach które były w pobliżu, aby ostrzec je przed ewentualnym zakażeniem. Nikt nie dowie się o Twojej chorobie. Otwórz Protego i wybierz O aplikacji -> Prześlij dane. Dziękujemy.```

Pracownik GIS/CRZ wie kto z chorych przesłał dane, więc może wysyłać przypomnienia.

Po przesłaniu danych chorego, na serwerze dochodzi do zamiany anonimowych identyfikatorów urządzeń na numery telefonów użytkowników aplikacji. Pracownik GIS/CRZ ma dostęp do 2-tygodniowej historii wszystkich użytkowników, którzy byli w pobliżu zakażonej osoby. Dla każdego użytkownika, który był w pobliżu, może zobaczyć jego numer telefonu oraz daty, częstotliwość kontaktów i siłę sygnału (bliskość). Na tej podstawie pracownik decyduje z którymi użytkownikami się skontaktować.

# Przesyłanie danych z aplikacji ProteGO na serwer

Aplikacja zbiera i przechowuje na telefonie identyfikatory innych urządzeń na których również zainstalowana jest aplikacja i które znajdują się w pobliżu. Identyfikatory są losowe, zmieniają się co godzinę i nie pozwalają ujawnić do kogo należy napotkane urządzenia. Aplikacja przechowuje informacje z ostatnich 2 tygodni. Starsze informacje są usuwane na bieżąco.

Pracownicy GIS / Centralnego Rejestru Zakażeń (CRZ) do każdej nowo-zakażonej osoby wysyłają prośbę i instrukcję przesłania danych z aplikacji ProteGO. Wiadomości wysyłane są do wszystkich zakażonych, ponieważ nie wiadomo kto jest użytkownikiem aplikacji. Przykład wiadomości:

```Jeśli jesteś użytkownikiem ProteGO, prześlij informacje o osobach które były w pobliżu, aby ostrzec je przed ewentualnym zakażeniem. Nikt nie dowie się o Twojej chorobie. Otwórz Protego i wybierz O aplikacji -> Prześlij dane. Wprowadź kod 1234-5678 i potwierdź wysyłkę. Dziękujemy.```

Po przesłaniu danych chorego pracownik GIS/CRZ ma dostęp do 2-tygodniowej historii wszystkich użytkowników, którzy byli w pobliżu zakażonej osoby. Każdy użytkownik reprezentowany jest przez losowy, anonimowy identyfikator. Dla każdego użytkownika (identyfikatora), który był w pobliżu, może zobaczyć daty, częstotliwość kontaktów i siłę sygnału (bliskość). Na tej podstawie pracownik decyduje, którym użytkownikom zmienić status. Pracownik może również zadecydować, że z którymś z użytkowników nieanonimowych należy skontaktować się telefonicznie np. poprzez wysłanie wiadomości SMS lub wykonanie automatycznego połączenia telefonicznego.

Powyższy proces z czasem może być (pół)automatyczny.

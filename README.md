# Aplikacja ProteGO Safe

## Spis treści

1. [Wprowadzenie](#wprowadzenie)
2. [Grupy ryzyka zarażenia SARS-CoV-2](#grupy-ryzyka-zarażenia-sars-cov-2)
3. [Anonimowość i bezpieczeństwo](#anonimowość-i-bezpieczeństwo)
5. [Dalsze założenia](#dalsze-założenia)
6. [Zakres funkcjonalności wersji 2.0](#wykonana-zakres-funkcjonalności-wersji-20)
7. [Zakres funkcjonalności wersji 3.0](#wykonana-zakres-funkcjonalności-wersji-30)
9. [Zakres funkcjonalności wersji 4.0](#w-trakcie-zakres-funkcjonalności-wersji-40)
10. [Najczęściej zadawane pytania](FAQ.md)
11. [Chcę pomóc, zgłosić błąd, mam pomysł](CONTRIBUTING.md)

## Wprowadzenie 
Celem aplikacji mobilnej ProteGO Safe jest dostarczenie narzędzia asystującego i chroniącego użytkownika i jego bliskich przed rozprzestrzenianiem się COVID-19, a docelowo także pomoc w przejściu z ogólnopolskiego lockdownu do selektywnej kwarantanny osób, które były narażone na ryzyko zakażenia COVID-19.

Od 13.03.2020 trzy zespoły: ProteGO (bluetooth tracing), SafeSafe (diagnostyka i profilaktyka) i Sigma Connectivity (bluetooth tracing) tworzyły swoje rozwiązania dla aplikacji mobilnych, które w założeniu miały przyspieszyć ten proces. Ministerstwo Cyfryzacji połączyło te zespoły i nadało nową nazwę dla aplikacji - ProteGO Safe. Aplikacja przygotowywana jest dla Głównego Inspektora Sanitarnego, który ma największe kompetencje w specyfikowaniu założeń projektowych tak, aby aplikacja stanowiła efektywne narzędzie w walce z pandemią COVID-19. Minister Cyfryzacji i GovTech Polska z uwagi na swoje doświadczenie pełnią nadzór nad pracami projektowymi.

Aplikacja jest budowana zgodnie z zasadami wynikającymi z ogólnego rozporządzenia o ochronie danych osobowych (RODO), w tym minimalizacji danych, privacy by design, privacy by default, prawidłowości, integralności oraz poufności. Wzięto także pod uwagę wytyczne Europejskiej Rady Ochrony Danych Osobowych, Komisji Europejskiej oraz Toolbox opracowany w ramach sieci eHealth działającej przy Komisji Europejskiej. Wszystkie zaangażowane strony przykładają szczególną wagę do zapewnienia najwyższych standardów prywatności. Przyjęte rozwiązania zapewniają wsparcie organów zdrowia w walce z pandemią, wykorzystując przy tym możliwie minimalny zestaw danych koniecznych dla osiągnięcia tego celu.

Główny Inspektor Sanitarny w porozumieniu z Ministrem Cyfryzacji zdecydował się wstrzymać dalsze rozwijanie standardu Open Trace w modelu dążącym do rozproszenia systemu, z uwagi na zaawansowane prace nad narzędziem, które zapewni lepsze pokrycie przy zachowaniu modelu rozproszonego  - „Privacy-Preserving Contact Tracing” przygotowywane przez konsorcjum Google i Apple (o roboczej nazwie „Exposure Notification”).

Zespół ProteGO Safe został zaproszony do testów rozwiązania Exposure Notification, dzięki czemu możemy wdrożyć rozwiązanie, które od początku jest projektowane jako system rozproszony i dzięki temu umożliwia ochronę prywatności użytkowników aplikacji tracingowych opartych o ten standard. 

ProteGO Safe nie wymaga podania żadnych danych osobowych na jakimkolwiek z etapów korzystania z Aplikacji. ProteGO Safe nie zbiera też danych osobowych. Wszystkie informacje przetwarzane przez ProteGO Safe zbierane i przetwarzane są w taki sposób, aby uniemożliwić identyfikację użytkowników.

Obecnie dostępna jest podstawowa funkcjonalność ProteGO Safe, która umożliwia dokonanie triażu tj. samooceny ryzyka zarażenia chorobą COVID-19. Funkcjonalność triażu dostarczana jest przez API Infermedica wykorzystywane również przez portal pacjent.gov.pl. Funkcjonalność ta jest w trakcie przepisywania na moduł, który będzie działał lokalnie (offline czyli nie po API). 

Druga kluczowa funkcjonalność, która będzie oparta o Exposure Notification API umożliwia tzw. Bluetooth tracing. Jeśli użytkownik wyrazi stosowną zgodę – Aplikacja, wykorzystując wbudowany w urządzenie mobilne moduł Bluetooth rozgłaszać będzie generowany losowo, w pełni anonimowy klucz, który zamieniany będzie co 10 minut oraz jednocześnie skanuje otoczenie w poszukiwaniu innych telefonów na których zainstalowana jest aplikacja i zapisuje historię spotykanych anonimowych kluczy urządzeń, a także ocenia “jakość” kontaktów z użyciem Exposure Notification API opracowanego przez Google oraz Apple.

“Jakość” kontaktów oceniana jest na podstawie konfiguracji (parametrów) ustalonych przez lokalne Health Authority, zawierających m.in. określenie tego, jaki wpływ na wynik analizy ma długość samego spotkania, a jaki wpływ ma odległość w czasie od tego spotkania (ile dni od niego minęło), czy fizyczna odległość między użytkownikami. W oparciu o parametry moduł analityczny dostarczony przez G+A podaje wynik odpowiadający ryzyku ekspozycji na wirusa. 

Poza szacowanym ryzykiem zwracane są również informacje, nt.: długości spotkania, które odnotowywane są co 5 minut. Z powodów bezpieczeństwa i prywatności górna granica rejestrowania czasu to 30 minut.

Dane te przechowywane są wyłącznie na urządzeniach użytkowników Aplikacji i nie są przesyłane na żaden serwer centralny, co zapewnia API Exposure Notification opracowane przez konsorcjum Google i Apple. Aplikacja usuwa dane zgromadzone na urządzeniu po 14 dniach od dnia ich zapisania w Aplikacji lub w każdej chwili na żądanie użytkownika (stosowna opcja w ustawieniach).

W kolejnej wersji aplikacji (4.1) funkcjonalności związane z zapobieganiem COVID-19 zostaną rozszerzone. 

Na chwilę obecną, od początku epidemii a bez związku z posiadaniem lub nie aplikacji, każda z osób, u której zdiagnozowano chorobę COVID-19 jest telefonicznie informowana o wyniku testu przez upoważnionego przedstawiciela organu zdrowia. W nieodległej przyszłości ten upoważniony przedstawiciel organu zdrowia informując o pozytywnym wyniku testu na COVID-19 zapyta także, czy osoba chora ma zainstalowaną aplikację ProteGO Safe i chce ostrzec innych ludzi, którzy przebywali w jej otoczeniu zgodnie z parametrami wyznaczonymi przez GIS. Jeśli tak, upoważniony przedstawiciel organu zdrowia proponuje użytkownikowi aplikacji wysłanie swojej historii Diagnosis Key (tylko osoby zarażonej - bez historii spotkanych urządzeń) z ostatnich maksymalnie 14 dni na serwer, z którego dane zostaną rozesłane dalej na urządzenia użytkowników końcowych aplikacji. 

Dzięki temu na urządzeniu użytkownika końcowego po otrzymaniu paczki DiagnosisKey anonimowego-chorego, zainicjowany zostanie proces analizy napotkanych urządzeń z zainstalowaną aplikacją ProteGO Safe. Moduł analityczny najpierw sprawdzi, czy aplikacja “widziała się” z zarażonym Diagnosis Key. 

Jeżeli doszło do takiego kontaktu, aplikacja na podstawie m.in. okresu spotkania, odległości między urządzeniami, a także innymi czynnikami wskazanymi w  wytycznych GIS, zdecyduje, czy użytkownik końcowy aplikacji powinny otrzymać informacje o potencjalnym zagrożeniu. 

Następnie aplikacja wyświetli dalsze komunikaty (w tym precyzyjny numer telefonu do kontaktu z Centrum Kontaktu) jak postępować w przypadku bycia w Wysokiej Grupie Ryzyka zarażenia się SARS-CoV-2. 


## Grupy ryzyka zarażenia SARS-CoV-2

Każdy użytkownik może po włączeniu aplikacji sprawdzić jaki jest jego spersonalizowany status: 
- Zielony - niska grupa ryzyka - można swobodnie wychodzić, zachowując obowiązujące regulacje i profilaktykę. 
- Pomarańczowy - średnia grupa ryzyka - Test Oceny Ryzyka lub potencjalny kontakt z osobą chorą wskazują na konieczność samoobserwacji. 
- Czerwony - wysoka grupa ryzyka - należy skontaktować się z GIS lub skontaktować się z lekarzem.

Kod aplikacji jest publicznie dostępny na znanej i otwartej licencji GPL-3.0. 

  
## Anonimowość i bezpieczeństwo

W jaki sposób ProteGO Safe w wersji 4.0 opartej o Exposure Notifications zadba o anonimowość użytkowników i bezpieczeństwo danych?

System rozproszony:
1) Dane przechowywane są na urządzeniach użytkowników. Wszystkie informacje (wpisy w Dzienniku Zdrowia), a także historia spotykanych urządzeń są przechowywane na urządzeniach użytkowników i tam analizowane. 
2) Dane wprowadzane do ProteGO Safe umożliwiają zachowanie anonimowości użytkowników. Nie jest konieczna rejestracja, ani podawanie jakichkolwiek danych identyfikujących. Oprócz instalacji aplikacji użytkownik podaje jedynie swoją nazwę, która może być dowolna i jej jedyny cel to komfort użytkownika. 
3) Tylko osoby zweryfikowane medycznie jako chore na COVID-19 będą mogły zainicjować proces wysłania swoich Diagnosis Key (wcześniej wymagany jest kontakt osoby chorej z Centrum Kontaktu - warunek niezbędny. Kontakt ten jest wykonywany dobrowolnie przez osobę chorą, Centrum Kontaktu nie posiada takich danych nie ma więc możliwości skontaktować się z taką osobą), aby można było wysłać ostrzeżenie dla innych użytkowników.
 
## Dalsze założenia
- Numery telefonów osób u których wykryto chorobę COVID-19 są w Polsce przetwarzane przez upoważnione do tego organy zdrowia - nie ma zatem potrzeby angażowania aplikacji ProteGO Safe w ich pozyskiwanie, a tym bardziej przechowywanie.
- Zakładamy potrzebę interoperacyjności - wymiany danych z innymi projektami w Europie i kraju a to wymaga modelu federacyjnego, bezpiecznego standardu wymiany danych między systemami do CT oraz możliwości rozszerzenia modelu podstawowego. 
- Potrzebne jest dalsze rozwijanie części informacyjno-edukacyjnej aplikacji ProteGO Safe.

Projekt jest rozwijany na zlecenie MC przez konsorcjum firm: Tytani24 Sp. z o.o. (lider), The Coders Sp. z o.o. , Webini Sp. z o.o. , Sigma Connectivity Sp. z o.o. , 25wat Sp. z o.o. , Klimas Legal, Mobile Flag, HOLDAPP wspierane przez wszystkich chętnych kontrybutorów.

Poniżej opis wersji Aplikacji:


## [wykonana] Zakres funkcjonalności wersji 2.0
- Użytkownik anonimowo, bez podawania danych umożliwiających jakąkolwiek identyfikację instaluje Aplikację na telefonie z systemem operacyjnym Android i iOS (czeka na publikację), 
- Użytkownik otwiera Aplikację i wyświetlają mu się informacje o sposobie jej działania i potrzebnych zgodach/uprawnieniach (akceptacja Regulaminu i Polityki Prywatności). 
- Użytkownik uzupełnia metrykę zdrowia. Użytkownik wypełnia pierwszy test oceny ryzyka (triaż). 
- Użytkownik dostaje pierwszy wynik klasyfikacji swojego stanu zdrowia (triaż).
- Użytkownik odbiera notyfikacje push przypominające o potrzebie wypełnienia testu oceny ryzyka. 
- Aplikacja prowadzi użytkownika przez porady i zalecenia związane z jego stanem zdrowia na podstawie oceny ryzyka (triażu). 
- Użytkownik może wypełniać dowolną ilość razy dziennie: test oceny ryzyka (triaż) i dziennik zdrowia. 
- Po trzech dniach, w których użytkownik przynajmniej raz dziennie wypełnił test oceny ryzyka w Aplikacji wyświetla się odznaka “Dbam o siebie i bliskich”. 
- W przypadku Aplikacji dla systemu iOS - użytkownik musi wyrazić zgodę na “Pozwolenie na wysyłanie notyfikacji”.

Zakres:
- Celowy i pożądany brak synchronizacji z Google Analytics.
- Brak rejestracji użytkownika w Aplikacji przy użyciu numeru telefonu.
- Dane z modułów: Metryka, test oceny ryzyka i dziennik zdrowia są zapisywane lokalnie na telefonie.

## [wykonana] Zakres funkcjonalności wersji 3.0
Użytkownik pobiera lub aktualizuje aplikację ProteGO Safe 3.0 z modułem OpenTrace i nie ma w niej możliwości (i widoku) podania numeru telefonu (użytkownik nie podaje numeru telefonu w aplikacji - nie zbieramy tych danych w żaden sposób). 

Serwer przyznaje aplikacji (a nie numerowi telefonu) UID czyli zanonimizowany unikatowy numer danej instalacji (aplikacji) - przez co jest w stanie komunikować się z aplikacją. Dla każdego UID backend generuje TempID (zapisuje na urządzeniu tablicę z listą numerów TempID na 2 tygodnie do przodu, które aplikacja będzie zmieniać co 15 minut). TempID służą do anonimizacji użytkowników w module tracingowym (kontakt Bluetooth).

Na początku korzystania z aplikacji użytkownik jest proszony o wyrażenie zgody na: 
- Android: "Korzystanie z usługi lokalizacja" (żeby skanować inne urządzenia w okolicy trzeba mieć zgodę na “Lokalizację”. W praktyce jest to wymagane do korzystania z modułu bluetooth. Aplikacja nie korzysta z geolokalizacji urządzenia za pośrednictwem GPS). 
- iOS: “Pozwolenie na używanie modułu Bluetooth”. Po wyrażeniu zgody, aplikacja uruchamia moduł OpenTrace, który działa w tle (tylko w systemie Android, w systemie iOS możliwości działania Bluetooth w aplikacji działającej “w tle” są bardzo ograniczone), również po opuszczeniu aplikacji i zablokowaniu ekranu (na tyle na ile pozwala na to system operacyjny). 

Moduł bluetooth nie działa przy wyłączonej aplikacji. Moduł OpenTrace rozgłasza TempID przy użyciu Bluetooth. TempID aplikacji jest rotowane tj. zmieniane co 15 minut zgodnie z bazą zapisaną na urządzeniu - ilość kodów określona jest w parametrach. Częstotliwość pobierania nowej listy TempID jest również określana jako parametr w konfiguracji. 

Moduł OpenTrace skanuje otoczenie w celu wykrycia innych użytkowników i zapisuje dane: timestamp, msg (TempID), siła sygnału bluetooth. Dane te są zapisywane wyłącznie w lokalnej pamięci telefonu.

## [w trakcie] Zakres funkcjonalności wersji 4.0
Wersja 4.0 opiera się o implementację Exposure Notification API opracowane przez Google i Apple (G+A) w miejsce dotychczas stosowanego OpenTrace.

Zakres funkcjonalności dla wersji 4.0:
- Użytkownik pobiera aplikację lub aktualizuję ją do wersji 4.0 korzystającą z API G+A.
- Zgodnie z wymogami dotyczącymi korzystania z API: urządzenie użytkownika rozgłasza w sposób ciągły tymczasowe identyfikatory (TemporaryExposureKey), które pobierane są z poprzednio wygenerowanej przez użytkownika puli kluczy, zmienianych po upływie określonego czasu. Nasłuchuje jednocześnie na identyfikatory nadawane przez inne urządzenia.
- Wszelkie identyfikatory są generowane w sposób uniemożliwiający ich powiązanie z konkretnym urządzeniem lub użytkownikiem.
- Dane dotyczące kontaktu usuwane są z urządzenia użytkownika po upływie 14 dni [parametr].
- Aplikacja przynajmniej raz na dobę pobiera identyfikatory użytkowników pozytywnie zweryfikowanych przez Generalny Inspektorat Sanitarny jako zakażonych i porównuje je z identyfikatorami zapisanymi na urządzeniu użytkownika, dokonując w razie potrzeby ich analizy i oceny ryzyka kontaktu.
- W przypadku dłuższej nieobecności użytkownika końcowego, po włączeniu aplikacji pobierane są wszystkie DiagnosisKey chorych, z ostatnich 2 tygodni, których aplikacja nie posiada.
- Analiza danych dotyczących bezpośredniości kontaktu przeprowadzana jest jedynie lokalnie na urządzeniu użytkownika końcowego.
- W przypadku wykrycia kontaktu z chorym i ocenie siły tego kontaktu, użytkownik otrzymuje odpowiednie powiadomienie push.
- W zależności od tego, do jakiej kategorii dany kontakt zostanie zakwalifikowany, użytkownik otrzymuje odpowiednie powiadomienie push.

## ProteGO Safe and it's documentation is licensed under
Kod aplikacji jest publicznie dostępny na znanej i otwartej licencji GPL-3.0. Link do repozytorium GitHub: https://github.com/ProteGO-Safe
[GNU General Public License v3.0](./LICENSE)

Permissions of this strong copyleft license are conditioned on making available complete source code of licensed works and modifications, which include larger works using a licensed work, under the same license. Copyright and license notices must be preserved. Contributors provide an express grant of patent rights.

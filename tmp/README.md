# Aplikacja ProteGO Safe

## Spis treści

1. [Wprowadzenie](#wprowadzenie)
2. [Grupy ryzyka zarażenia Sars-Cov-2](#grupy-ryzyka-zarażenia-sars-cov-2)
3. [Anonimowość i bezpieczeństwo](#anonimowość-i-bezpieczeństwo)
4. [Grupy ryzyka zarażenia Sars-Cov-2](#grupy-ryzyka-zarażenia-sars-cov-2)
5. [Dalsze założenia](#dalsze-założenia)
6. [Zakres 2.0](#zakres-20)
7. [Zakres 3.0](#zakres-30)
8. [Zakres 3.1](#zakres-31)
9. [Zakres 3.2](#zakres-32)
10. [Najczęściej zadawane pytania](FAQ.md)
11. [Chcę pomóc, zgłosić błąd, mam pomysł](CONTRIBUTING.md)

## Wprowadzenie 
Celem aplikacji mobilnej ProteGO Safe jest dostarczenie narzędzia asystującego i chroniącego użytkownika i jego bliskich przed rozprzestrzenianiem się COVID-19, a docelowo także pomoc w przejściu z ogólnopolskiego lockdownu do selektywnej kwarantanny osób, które były narażone na ryzyko zakażenia COVID-19.

Od 13.03.2020 trzy zespoły: ProteGO (bluetooth tracing), SafeSafe (diagnostyka i profilaktyka) i Sigma Connectivity (bluetooth tracing) tworzyły swoje rozwiązania dla aplikacji mobilnych, które w założeniu miały przyspieszyć ten proces.
Obecnie zespoły te połączyły siły i przyjęły dla aplikacji nową i wspólną nazwę - ProteGO Safe. Aplikacja przygotowywana jest dla Głównego Inspektora Sanitarnego, który jest administratorem danych osobowych. Minister Cyfryzacji i GovTech Polska z uwagi na swoje doświadczenie pełnią nadzór nad pracami projektowymi.

Aplikacja jest budowana zgodnie z zasadami wynikającymi z ogólnego rozporządzenia o ochronie danych osobowych (RODO), w tym minimalizacji danych, privacy by design, privacy by default, prawidłowości, integralności oraz poufności. Wzięto także pod uwagę wytyczne Europejskiej Rady Ochrony Danych Osobowych, Komisji Europejskiej oraz Toolbox opracowany w ramach sieci eHealth działającej przy Komisji Europejskiej. Wszystkie zaangażowane strony przykładają szczególną wagę do zapewnienia najwyższych standardów prywatności. Przyjęte rozwiązania zapewniają wsparcie organów zdrowia w walce z pandemią, wykorzystując przy tym możliwie minimalny zestaw danych koniecznych dla osiągnięcia tego celu.

ProteGO Safe korzysta z rozwiązań OpenTrace wdrożonych z sukcesem w Singapurze. Z konsultacji podczas sieci eHealth Komisji Europejskiej wynika, że prace nad aplikacją ProteGO Safe są koncepcyjnie zbliżone do aplikacji tracingowych wdrażanych w Norwegii i Czechach. Należy przy tym odnotować, że np. w Czechach do korzystania z aplikacji wymagane jest zarejestrowanie się przy wykorzystaniu swojego numeru telefonu. ProteGO Safe nie wymaga takiego uwierzytelnienia.

Aplikacja stara się zrównoważyć potrzebę zachowania prywatności obywateli z potrzebą zbierania informacji o tym kogo mogły spotkać i zarazić osoby dotknięte chorobą COVID-19. Aplikacja może być używana anonimowo. Rejestracja ani jakiekolwiek uwierzytelnienie nie jest wymagane aby korzystać z funkcji ProteGO Safe ( wyjątek - konieczność potwierdzenia autentyczności osoby, która chce wysłać dane z urządzenia).

Podstawowa funkcjonalność aplikacji umożliwia dokonanie triażu tj. samooceny ryzyka zarażenia chorobą COVID-19. Funkcjonalność triażu dostarczana jest przez API Infermedica wykorzystywane również przez portal pacjent.gov.pl.

Druga kluczowa funkcjonalność umożliwia tzw. Bluetooth tracing. Jeśli użytkownik zaznaczy stosowną opcję -aplikacja, wykorzystując wbudowany w urządzenie mobilne moduł Bluetooth skanuje otoczenie w poszukiwaniu innych telefonów na których zainstalowana jest aplikacja i zapisuje historię spotykanych anonimowych identyfikatorów (tzw. TempID) urządzeń. Tymczasowe ID urządzeń nie umożliwia identyfikacji urządzenia tj. aplikacja nie przetwarza danych szczegółowych zapisując jedynie model urządzenia dla wsparcia predykcji ryzyka zarażenia w oparciu o moc odbieranego sygnału i tzw. kalibrację. 

Dane te przechowywane są wyłącznie na urządzeniach użytkowników Aplikacji i nie są przesyłane na żaden serwer centralny. Aplikacja usuwa dane zgromadzone na urządzeniu po 2 tygodniach od dnia ich zapisania w Aplikacji lub w każdej chwili na żądanie użytkownika (stosowna opcja w ustawieniach).

W kolejnej wersji aplikacji funkcjonalności związane z zapobieganiem COVID-19 zostaną rozszerzone. Obecnie każda z osób u której zdiagnozowano chorobę COVID-19 jest telefonicznie informowana o wyniku testu przez upoważnionego przedstawiciela organu zdrowia. W nieodległej przyszłości ten upoważniony przedstawiciel organu zdrowia informując o pozytywnym wyniku testu na COVID-19 zapyta także, czy osoba chora ma zainstalowaną aplikację ProteGO Safe. Jeśli tak, upoważniony przedstawiciel organu zdrowia zaproponuje użytkownikowi aplikacji zweryfikowanie aplikacji poprzez podanie upoważnionemu przedstawicielowi organu zdrowia kodu z aplikacji. Dzięki temu użytkownik będzie mógł anonimowo przesłać historię napotkanych urządzeń na serwer. Dane, o ile taka będzie wola użytkownika, trafiają na serwer gdzie algorytm na podstawie ich analizy (długości, częstości, bliskości zgodnie ze standardami WHO i wytycznymi GIS) zdecyduje, które z osób, z którymi spotykał się chory na COVID-19 powinny otrzymać informacje o potencjalnym zagrożeniu. Po analizie serwer prześle na te wybrane urządzenia komunikat o możliwym kontakcie z osobą chorą na COVID-19. Komunikat ten nie będzie zawierał żadnych danych osoby, która zweryfikowała swoje urządzenie jako urządzenie osoby chorej na COVID-19 (ponieważ takie dane nie są zbierane na żadnym etapie).

Podejście wykorzystywane w aplikacji to tzw. podejście mieszane (hybrid/mixed). Nie jest to rozwiązanie w 100% zdecentralizowane, gdyż w celu analizy m.in. “jakości” kontaktu pomiędzy urządzeniami aplikacja potrzebuje wykonać taką operację na serwerze centralnym (opt-in). Takie podejście jest podyktowane potrzebą rozszerzenia wykorzystywania aplikacji o urządzenia starsze, na których taka analiza byłaby trudna lub niemożliwa. Podejście mieszane jest obecnie przedmiotem dyskusji w sieci eHealth. Sam Europejski Inspektor Ochrony Danych stwierdził wprost, że nawet w przypadku rozwiązań zdecentralizowanych “w pełni”, jakiś serwer zewnętrzny jest zaangażowany w operacje przetwarzania. Aplikacja ProteGO Safe stara się przetwarzać na serwerze absolutne minimum danych tak, aby zapewnić większe wsparcie aplikacji przez urządzenia użytkowników oraz uwiarygodnić przekazanie informacji o kontakcie z urządzeniem osoby chorej na COVID-19. Serwer aplikacji oraz serwer rejestru osób zakażonych COVID-19 są od siebie niezależne.

## Grupy ryzyka zarażenia Sars-Cov-2

Każdy użytkownik może po włączeniu aplikacji sprawdzić jaki jest jego spersonalizowany status:
Zielony - niska grupa ryzyka - można swobodnie wychodzić, zachowując obowiązujące regulacje i profilaktykę.
Pomarańczowy - średnia grupa ryzyka - Test Oceny Ryzyka lub potencjalny kontakt z osobą chorą wskazują na konieczność samoobserwacji.
Czerwony - wysoka grupa ryzyka - należy skontaktować się z GIS.
Kod aplikacji jest publicznie dostępny na znanej i otwartej licencji GPL-3.0. Link do repozytorium GitHub: https://github.com/ProteGO-Safe
  
## Anonimowość i bezpieczeństwo

W jaki sposób ProteGO Safe troszczy się o anonimowość użytkowników i bezpieczeństwo danych?

Decentralizacja:
1) Co do zasady dane przechowywane są  na urządzeniach użytkowników. Wszystkie informacje dotyczące zdrowia (wpisy w Dzienniku Zdrowia), a także historia spotkanych urządzeń (Temp ID) są przechowywane na urządzeniach użytkowników. Na serwer zewnętrzny (API Infermedica) przekazywana jest anonimowa informacja związana z triażem (samooceną stanu zdrowia/ Test Oceny Ryzyka). 
2) Dane wprowadzane do ProteGO Safe umożliwiają zachowanie anonimowości użytkowników. Oprócz instalacji aplikacji użytkownik podaje jedynie swoją nazwę, która może być dowolna i jej jedyny cel to komfort użytkownika. Nie jest konieczna rejestracja, ani podawanie jakichkolwiek danych identyfikujących. 
3) Tylko osoby zweryfikowane medycznie jako chore na COVID-19 będą mogły wysłać swoje dane na serwer (wymagany kontakt ze strony Centrum Kontaktu - warunek niezbędny) aby można było wysłać ostrzeżenie dla innych użytkowników.
 
Centralizacja:
1) Serwer będzie dokonywał analizy, które z nadesłanych spotkań kwalifikują się do wysłania powiadomienia o zmianie statusu ryzyka i przekaże to powiadomienie do tak wytypowanych urządzeń.
2) Tylko Serwer ProteGO Safe generuje UID i listy Temp ID do rotacji identyfikatorów tymczasowych.
  
Dodatkowo, celem zapewnienia prywatności, wykorzystywane rozwiązania backendowe (serwerowe) będą odizolowane od siebie, zarówno na poziomie infrastruktury, systemu operacyjnego jak i oprogramowania. Taki zabieg zapewnia również swoistą decentralizację po stronie infrastruktury. Pierwszy backend służy do analizy spotkań i klasyfikacji wysyłania powiadomień ProteGO Safe, drugi - do obsługi OP-Backend będzie stanowił wsparcie dla operatorów Centrum Kontaktu, a trzeci - dla operatorów IN-Backend, czyli obsługi Instytucji w programie kodów QR. 

W celu przekazywania wiadomości do użytkowników konieczny jest centralny rejestr zawierający unikatowe i losowe ciągi znaków, które są rotowane (zmieniane) co określony czas. W ten sposób możliwe będzie wysłanie wiadomości poprzez aplikacje do użytkowników i tą drogą ma następować przekierowanie wiadomości o podniesionym ryzyku. Ta część jest zatem centralnym pośrednikiem w dostarczaniu wiadomości ogólnych i powiadomień dla wyselekcjonowanych użytkowników. Nie jest to natomiast w żadnym wypadku centralny serwer. W modelu OpenTrace, który służy ProteGO Safe za wzór zastosowano przetwarzanie danych oparte o tak zwane Cloud Functions albo inaczej - funkcja jako usługa. Są to mikroprogramy z dostępem do odczytu wyselekcjonowanych danych i zapisu wyników w wybrane miejsce. Określona funkcja może w jakimś miejscu zapisać wynik, ale nie może odczytać tego co zapisała. Inna funkcja wywoływana jest na tak zwane zdarzenie utworzenia danych i ona z kolei ma prawo odczytać określony typ danych i wykonać na nich anonimowe operacje, ale nie może zmienić danych początkowych. Z uwagi na zastosowanie usługi chmurowej nie jest konieczne administrowanie i ochrona serwera fizycznego, czy też maszyny wirtualnej. 
 
Reasumując, zpseudonimizowane dane są rozproszone a anonimowy rejestr użytkowników jest centralny. Analiza sygnałów o spotkaniach na serwerze (w modelu mieszanym), a nie na urządzeniu wydaje się niezbędna do pozyskania wartościowych danych, które zostaną pozbawione wyników false-positive (fałszywych pozytywów).
 
Jednym z elementów w których odchodzimy od specyfikacji OpenTrace jest rezygnacja z wykorzystania numerów telefonów jako informacji kojarzonej już na etapie rejestracji danego UID.
Wydaje się to słabym ogniwem tego modelu i stąd decyzja o użyciu “rejestracji” anonimowej, która zdecydowanie zwiększa bezpieczeństwo i prywatność użytkowników.
 
## Dalsze założenia
- aplikacja ProteGO Safe nie umożliwia odczytu danych dotyczących zdrowia. Zmniejsza to znacznie ryzyko naruszenia ochrony danych szczególnej kategorii.
- numery telefonów osób u których wykryto chorobę COVID-19 są w Polsce przetwarzane przez upoważnione do tego organy zdrowia - nie ma zatem potrzeby angażowania aplikacji ProteGO Safe w ich pozyskiwanie, a tym bardziej przechowywanie.
- spodziewamy się dalszej dynamicznej ewolucji rozwiązań do rejestracji spotkań przy użyciu technologii bluetooth i nie tylko. Zakładamy, że dostosowanie ProteGO Safe do API Google i Apple będzie niezbędne, ale nie wiemy kiedy to rozwiązanie będzie gotowe.
UPDATE: 29.04.2020 zostaliśmy zaproszeni do zamkniętych beta testów API Google, podpisujemy NDA i czekamy na dokumentację. W ramach tego kontaktu zgłosimy również do Google sugestie, które pojawią się na naszym Github'ie. 
- zakładamy potrzebę interoperacyjności - wymiany danych z innymi projektami w Europie i kraju a to wymaga modelu federacyjnego, bezpiecznego standardu wymiany danych między systemami do CT oraz możliwości rozszerzenia modelu podstawowego (np: o możliwość jednostronnego szanującego prywatność rejestrowania przez użytkowników swojego kontaktu z instytucjami, obiektami publicznymi itd). Pierwsze testy planowane są z aplikacją czeską, kontakt roboczy został już nawiązany. Nie wyklucza się również testów z aplikacją norweską.
- potrzebne jest dalsze rozwijanie części informacyjno-edukacyjnej aplikacji ProteGO Safe - w szczególności brakuje jeszcze porad na temat higieny w kontekście długofalowej zmiany zachowań i higieny cyfrowej. 
- W komentarzach do publicznego kodu aplikacji pojawiają się stale wątki bezpieczeństwa urządzeń mobilnych jeszcze przed instalacją aplikacji. Od 29.04.2020 nawiążemy kontakty z podmiotami, które niezależnie od społecznego audytu przeprowadzą także profesjonalne audyty. 
- Chcemy wprowadzić obsługę kodów QR, aby w aplikacji pojawił się element, który pozwoli na określanie kontaktu bezpośredniego.
 
Projekt jest rozwijany na zlecenie MC przez konsorcjum firm: Tytani24 Sp. z o.o. (lider), The Coders Sp. z o.o. , Webini Sp. z o.o. , Sigma Connectivity Sp. z o.o. , 25wat Sp. z o.o. , Klimas Legal, Mobile Flag, HOLDAPP wspierane przez wszystkich chętnych kontrybutorów. 

Poniżej opis wersji Aplikacji, który umożliwia analizę funkcjonalności już wdrożonych oraz dopiero planowanych. Obecnie (od 28.04.2020) dostępna jest aplikacja w wersji 3.0. Publikacja aplikacji w wersji 3.1 jest zaplanowana na 08.05.2020 po zakończeniu audytu. Szersza komunikacja o aplikacji pojawi się po 04.05.2020 a start emisji promocji po 08.05.2020.

## Zakres 2.0
Zakres funkcjonalności dla wersji 2.0
Użytkownik anonimowo, bez podawania danych umożliwiających jakąkolwiek identyfikację instaluje Aplikację na telefonie z systemem operacyjnym Android i iOS (czeka na publikację),
Użytkownik otwiera Aplikację i wyświetlają mu się informacje o sposobie jej działania i potrzebnych zgodach/uprawnieniach (akceptacja Regulaminu i Polityki Prywatności).
Użytkownik uzupełnia metrykę zdrowia.
Użytkownik wypełnia pierwszy test oceny ryzyka (triaż).
Użytkownik dostaje pierwszy wynik klasyfikacji swojego stanu zdrowia (triaż).
Użytkownik odbiera notyfikacje push przypominające o potrzebie wypełnienia testu oceny ryzyka. 
Aplikacja prowadzi użytkownika przez porady i zalecenia związane z jego stanem zdrowia na podstawie oceny ryzyka (triażu).
Użytkownik może wypełniać dowolną ilość razy dziennie: test oceny ryzyka (triaż) i dziennik zdrowia.
Po trzech dniach, w których użytkownik przynajmniej raz dziennie wypełnił test oceny ryzyka w Aplikacji wyświetla się odznaka “Dbam o siebie i bliskich”.
W przypadku Aplikacji dla systemu iOS - użytkownik musi wyrazić zgodę na “Pozwolenie na wysyłanie notyfikacji”.

Zakres:
- celowy i pożądany brak synchronizacji z Google Analytics
- brak rejestracji użytkownika w Aplikacji przy użyciu numeru telefonu  
- dane z modułów: Metryka, test oceny ryzyka i dziennik zdrowia są zapisywane lokalnie na telefonie

## Zakres 3.0
Zakres funkcjonalności dla wersji 3.0

Użytkownik pobiera lub aktualizuje aplikację ProteGO Safe 3.0 z modułem OpenTrace i nie ma w niej możliwości (i widoku) podania numeru telefonu (użytkownik nie podaje numeru telefonu w aplikacji - nie zbieramy tych danych w żaden sposób). Serwer przyznaje aplikacji (a nie numerowi telefonu) UID czyli zanonimizowany unikatowy numer danej instalacji (aplikacji) - przez co jest w stanie komunikować się z aplikacją. Dla każdego UID backend generuje TempID (zapisuje na urządzeniu tablicę z listą numerów TempID na 2 tygodnie do przodu, które aplikacja będzie zmieniać co 15 minut). TempID służą do anonimizacji użytkowników w module tracingowym (kontakt Bluetooth). 
Na początku korzystania z aplikacji użytkownik jest proszony o wyrażenie zgody na:
Android: "Korzystanie z uslugi lokalizacja" (żeby skanować inne urządzenia w okolicy trzeba mieć zgodę na “Lokalizację”. W praktyce jest to wymagane do korzystania z modułu bluetooth. Aplikacja nie korzysta z geolokalizacji urządzenia za pośrednictwem GPS).
iOS: “Pozwolenie na używanie modułu Bluetooth”.
Po wyrażeniu zgody, aplikacja uruchamia moduł OpenTrace, który działa w tle (tylko w systemie Android, w systemie iOS możliwości działania Bluetooth w aplikacji działającej “w tle” są bardzo ograniczone), również po opuszczeniu aplikacji i zablokowaniu ekranu (na tyle na ile pozwala na to system operacyjny). Moduł bluetooth nie działa przy wyłączonej aplikacji. 
Moduł OpenTrace rozgłasza TempID przy użyciu Bluetooth.
TempID aplikacji jest rotowane tj. zmieniane co 15 minut zgodnie z bazą zapisaną na urządzeniu - ilość kodów określimy w parametrach. Częstotliwość pobierania nowej listy TempID jest również określana jako parametr w konfiguracji.
Moduł OpenTrace skanuje otoczenie w celu wykrycia innych użytkowników i zapisuje dane: timestamp, msg (TempID), siła sygnału bluetooth. Dane te są zapisywane wyłącznie w lokalnej pamięci telefonu.

## Zakres 3.1
Zakres funkcjonalności dla wersji 3.1

Aplikacja zostaje rozszerzona o funkcjonalność generowania kodów QR (kod QR jest związany z TempID).
Dla każdego statusu triażu użytkownika jest przypisany kod QR w kolorze triażu.
Aplikacja zyskuje funkcjonalność skanowania kodów QR wygenerowanych na innych urządzeniach z aplikacją ProteGO Safe.
Użytkownik jednej aplikacji może łatwo zeskanować kod QR drugiego użytkownika. W ten sposób TempID urządzenia zapisuje takie spotkanie jako bezpośrednie; jeżeli zestaw danych ze skanowania Bluetooth wykaże, że urządzenia widziały się przez więcej niż 15 min, oznacza to, że był to kontakt bezpośredni trwający więcej niż 15 minut. 
Aplikacja w tej wersji obejmuje możliwość wyboru pomiędzy korzystaniem z aplikacji w trybie osoby fizycznej oraz instytucji lub stworzymy dwie osobne aplikacje - jedną dla osób fizycznych (ProteGO Safe) i drugą dla instytucji.

Dla Instytucji planowane jest uruchomienie osobnego serwisu dostępnego online “Konta Instytucji”, które będzie działało odrębnie w stosunku do “zwykłego” użytkownika. Instytucji również przyznawany będzie UID.
Tryb Instytucji obsługuje następujące funkcje:
Rejestracja konta “Instytucji”. Instytucja to robocza nazwa oznaczająca podmioty publiczne takie jak: urzędy, muzea, fundacje i inne miejsca przyjmujące interesantów. 
Do rejestracji instytucji wymagany jest numer NIP. Aplikacja będzie umożliwiała import danych z bazy CEIDG/KRS a następnie ich weryfikację i potwierdzenie. 
Zapisanie danych kontaktowych Instytucji.
Wygenerowanie kodu QR przypisanego do Instytucji, a właściwie generowanego dla każdej lokalizacji/ oddziału instytucji osobno.
Wygenerowanie akcji stworzenia plakatu z kodem QR instytucji i nazwą instytucji wynikającą z NIP. 
Możliwość wysłania plakatu z kodem QR instytucji na podanego przy rejestracji instytucji emaila do kontaktu
Możliwość wyświetlania w koncie Instytucji listy ostrzeżeń aplikacji. Są to ostrzeżenia takie jak “Zdezynfekuj swoją placówkę, ponieważ w ostatnim czasie przebywała tam osoba z pozytywnym wynikiem testu na COVID-19”. Tego rodzaju komunikacja jednokierunkowa pozwala ostrzegać instytucje o ryzyku, do którego mogło dojść, nie daje natomiast możliwości na komunikację zwrotną.
Ostrzeżenia te są związane z powiadomieniami z Centrum Kontroli w razie wykrycia identyfikatora instytucji w danych przekazanych przez użytkownika z pozytywnym wynikiem testu na Covid-19.
Ostrzeżenia/notyfikacje, o których mowa w niniejszym punkcie nie będą zawierały danych umożliwiających identyfikację osoby fizycznej takich jak np. dokładny czas wizyty - jest to kluczowe założenie z punktu widzenia bezpieczeństwa.
Możliwość ręcznej weryfikacji podmiotów zakładających konta Instytucji.
Możliwość tymczasowego zawieszenia/odwieszenia konta Instytucji.

Przykładowe scenariusze zastosowania kodu QR w muzeum:
Wydrukowany kod QR jest udostępniony w widocznym miejscu. Przed wejściem do muzeum użytkownik może zeskanować kod – jeśli otrzyma pozytywny wynik testu na Covid-19 w ustalonym przez epidemiologów interwale zagrażającym bepieczeństwu publicznemu muzeum anonimowo dostanie odpowiednią informację.
 
 
## Zakres 3.2
Zakres funkcjonalności dla wersji 3.2 (w opracowaniu)


## ProteGO Safe and it's documentation is licensed under

[GNU General Public License v3.0](./LICENSE)

Permissions of this strong copyleft license are conditioned on making available complete source code of licensed works and modifications, which include larger works using a licensed work, under the same license. Copyright and license notices must be preserved. Contributors provide an express grant of patent rights.

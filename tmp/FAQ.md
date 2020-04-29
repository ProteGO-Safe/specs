# FAQ

**1) W jaki sposób zapewniono, że aplikacja nie zostanie wykorzystana do śledzenia użytkoników lub ich aktywności?**

ProteGO Safe nie ma modułów (funkcjonalności) umożliwiających lokalizację. Aplikacja jest budowana na podstawie otwartego źródła opublikowanego w serwisie GitHub. Zrezygnowaliśmy z funkcji analitycznych oferowanych np. przez Google Analytics. Nie zbieramy nawet informacji na temat zachowania użytkownika korzystającego z aplikacji. Analogicznie nie analizujemy jak użytkownicy korzystają ze strony https://safesafe.app. Informacje, które aplikacja przetwarza w ramach tzw. tracingu to natężenie sygnału Bluetooth urządzeń z którymi łączy się urządzenie użytkownika. Nie mamy możliwości wykorzystania tych danych do “śledzenia” tj. określania pozycji geograficznej. Nie ma możliwości ustalenia gdzie znajduje się użytkownik. W najlepszym wypadku można ustalić odległość między dwoma urządzeniami (dwoma użytkownikami). Niemniej jest to obarczone potencjalnym błędem, który wynika z urządzeń korzystających z różnej klasy modułów łączności bluetooth (niektóre urządzenia są wyższej klasy i dostarczają bardziej prawidłowe pomiary, a niektóre mniej), a także z sytuacjami losowymi (np. dwie osoby, które stoją w korku w dwóch autach obok siebie lub sąsiedzi mieszkający w bloku, których dzieli ściana).

**2) Czy aplikacja wykorzystuje dane geolokalizacyjne?** 

Nie. Aplikacja nie wykorzystuje ani nie zapisuje żadnych danych geolokalizacyjnych. W urządzeniach klasy Android użytkownicy mogą być pytani o “zgodę na lokalizację”, niemniej dotyczy ona wykorzystania modułu Bluetooth w urządzeniu. ProteGO Safe nie przetwarza danych geolokalizacyjnych. 

**3) Jakie zastosowano zabezpieczenia, aby zapewnić, że nie dojdzie do zbierania danych osób na dużą skalę teraz i w przyszłości?** 

Nie przetwarzamy danych szczególnej kategorii (wszystkie dane zapisywane w Dzienniku Zdrowia są przechowywane jedynie na urządzeniu użytkownika, a dane podawane w triażu tj. samoocenie są przekazywane w sposób zanonimizowany do Infermedica, która nie przechowuje tych danych oraz nie może zidentyfikować kto wysłał zapytanie). 

**5) Jak zapewniono, że informacje o osobach niezakażonych nie będą ujawniane?**

Aplikacja zbiera anonimowe dane urządzeń ale nie wysyła ich na serwer bez pozwolenia użytkownika. Dane można wysłać dopiero po potwierdzeniu zmiany statusu wynikającej z medycznego testu na Covid-19. Innymi słowy ani Ministerstwo Cyfryzacji, ani Główny Inspektor Sanitarny a nawet operatorzy systemu ProteGO Safe nie wiedzą z jakimi dokładnie użytkownikami zetknęli się zdrowi użytkownicy aplikacji.

**6) W jaki sposób ustalono zakres danych niezbędnych do zbierania w aplikacji, tak że jest on ograniczony wyłącznie do niezbędnych do walki z pandemią?**

Jest to zakres ustalony podczas analiz przez Głównego Inspektora Sanitarnego oraz Ministerstwo Cyfryzacji. Konieczność weryfikacji użytkownika w aplikacji za pośrednictwem kodu PIN przed wysłaniem danych do systemu umożliwia wprowadzenie do aplikacji potwierdzonych danych dotyczących zarażenia użytkownika chorobą COVID-19. Co za tym idzie ogranicza możliwość podania przez użytkownika nieprawdziwej informacji, która mogłaby spowodować niechcianą panikę. Obawiano się także, że użytkownicy, którzy będą wprowadzali informacje o zarażeniu w niekontrolowany sposób doprowadzą do spadku zaufania do aplikacji, która ma kluczową rolę w walce z pandemią COVID-19.

**7) Czy rozwiązanie jest transparentne? Jakie środki zastosowano?**

Od 20.04.2020 kod aplikacji jest udostępniany na bieżąco w otwartym repozytorium serwisu GitHub. Dokumentacja jest w nim również publikowana od 29.04.2020.

**8) Czy wybrano rozwiązania (komponenty/funkcjonalności), które są najkorzystniejsze z punktu widzenia prywatności? Jak przebiegał proces decyzyjny ich wyboru? Jakie jest uzasadnienie takich a nie innych rozwiązań z punktu widzenia najszerszego zapewnienia prywatności?**

Wybrana została najpewniejsza metoda niegromadzenia danych, które mogłyby być zakwalifikowane jako dane szczególnej kategorii (dane dotyczące zdrowia). Aplikacja nie opiera się o geolokalizację, co skutkuje niższą skutecznością pomiarów i analiz modułu tracingowego, ale zapewnia bezpieczeństwo prywatności użytkowników w walce z pandemią COVID-19.

**9) Jakie argumenty przeważyły za wyborem skoncentrowanego modelu gromadzenia danych?**

Jak wskazano powyżej dane gromadzone są na urządzeniach użytkowników. Przetwarzanie danych otrzymanych od użytkowników z pozytywnym wynikiem testu na Covid-19 są przetwarzane centralnie. Nie jest to zatem klasyczny model centralny a raczej rozwiązanie hybrydowe. Głównym powodem wyboru tego modelu jest większa pewność co do prawidłowości danych i minimalizuje szanse na wystąpienie tzw. _fałszywych pozytywów_. Dodatkowo oczywiście maksymalnie zabezpieczamy prywatność zdrowych osób - ich dane nigdy nie opuszczą ich urządzeń. To rozwiązanie łączy zalety ochrony prywatności modelu zdecentralizowanego z większą wiarygodnością statusu _potencjalnych kontaktów_ z modelu centralnego. Umożliwia to również ciągłe doskonalenie algorytmów szacowania ryzyka bez konieczności częstych aktualizacji aplikacji.

**10) Czy użytkownik może wyłączyć, skasować dane w każdej chwili?**

Tak. Aplikacja umożliwia usunięcie wszystkich danych do niej wprowadzonych.

**11) Czy aplikacja zostanie dezaktywowana po zakończeniu obecnego kryzysu?**

Tak. W kolejnych wersjach aplikacji taka funkcjonalność zostanie dodana w ProteGO Safe. Przypominamy również, że aplikacja nie jest obowiązkowa i użytkownik może w każdym momencie podjąc decyzję o jej usunięciu z urządzenia.

**12) Jakie dane i kiedy są przesyłane na serwer? Kto utrzymuje ten serwer? Kto ma dostęp do danych na serwerze? Komu są przekazywane? Jak długo będą przechowywane? Czy są zanonimizowane?**

Na serwer mogą zostać przesłane jedynie dane zgromadzone przez osoby zweryfikowane przez Centrum Kontaktu. Jest to tymczasowe TempID aplikacji oraz analogicznie tymczasowe TempID aplikacji innych użytkowników, modele urządzeń i siła ich sygnału (parafrazując: anonimowe dane dotyczące historii wykrytych przez aplikację spotkań innych użytkowników aplikacji oraz pomocniczo modele urządzeń do ewentualnej korekty danych na podstawie charakterystyk modułu bluetooth znanych modeli). Serwer backend jest utrzymywany przez Ministerstwo Cyfryzacji.

**13) Jakie zastosowano zabezpieczenia aplikacji? Co zapewnia, że aplikacja jest bezpieczna, a osoby niepożądane nie uzyskają dostępu do danych?**

ProteGO Safe to dostępna publicznie w internecie aplikacja uruchamiająca się wyłącznie lokalnie w pamięci urządzenia użytkownika. Tam też składuje wszystkie dane. Niezależnie od tego publiczna strona dostarczająca użytkownikowi taki program, jest zabezpieczona przed zapisem przez niepowołane osoby oraz chroniona przez wiodący system anty DDoS i WAF firmy Cloudflare. Hostingiem który dostarcza treści chronione przez Cloudflare jest nowoczesna usługa Firebase Hosting firmy Google. Zabezpieczamy również cały proces wytwarzania aplikacji web i natywnych aplikacji mobilnych kontrolując listę osób z uprawnieniami do ostatecznej publikacji nowych wersji. Kod źródłowy aplikacji jest sprawdzany przez skanery korzystające z publicznych baz danych podatności oprogramowania i jego komponentów. W procesie korzystamy również z metody peer review i publicznego audytu społecznego otwartego kodu aplikacji poprzez platformę GitHub.

**14) Jakie testy aplikacji zostały przeprowadzone, w szczególności w zakresie cyberbezpieczeństwa?**

Prowadzimy ciągłe testy za pomocą tzw. statycznej analizy kodu. Zarówno za pomocą tak zwanego peer review w ramach zespołu jak i za pomocą narzędzi automatycznych (Whitesource i Snyk) w ramach systemu ciągłej integracji i dostarczania oprogramowania. Publiczny adres aplikacji był skanowany za pomocą skanera Nessus. W przygotowaniu są również zewnętrzne testy penetracyjne i specjalistyczny audyt. Kod aplikacji web oraz aplikacji mobilnych jest skanowany przez skanery podatności firm Whitesource i Snyk przy każdej kolejnej zmianie wersji testowych i produkcyjnych. Planowane są dalsze testy.

**15) Z kim były konsultowane założenia/funkcjonalności systemu?**

Założenia aplikacji są na bieżąco konsultowane z: GIS, MC i MZ, środowiskiem zgromadzonym wokół inicjatyw SafeSafe-app (pierwotnie koronazglowy.com) i ProteGO Safe (safesafe.app), lekarzami, epidemiologami i specjalistami od technologii, a także z Prezesem Urzędu Ochrony Danych Osobowych oraz podczas spotkań sieci eHealth Komisji Europejskiej. Czekamy również na audyty zewnętrznych podmiotów, oraz - przede wszystkim - społeczności i NGO'sów. 

**16) Czy ProteGO Safe umożliwi inwigilację osób chorych?**

Nie. Rozdzielenie systemów (serwerów backendowych), które analizują zanonimizowane dane realizowane jest właśnie po to, aby uniknąć przetwarzania danych na jednym centralnym systemie (serwerze). Przetwarzanie danych “w jednym miejscu” budziłoby bowiem uzasadnione i słuszne wątpliwości związane z prywatnością użytkowników. Obecne rozwiązanie, stara się maksymalnie ograniczyć dostęp do danych stosując zasadę adekwatności i minimalizacji, które zostały określone w RODO.

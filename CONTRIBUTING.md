# Współpraca nad projektem

Zapraszamy wszystkich do współpracy nad projektem:

1. [Zasady ogólne](Zasady-ogólne)
2. [Chcę zgłosić błąd w działaniu aplikacji.](#Chcę-zgłosić-błąd-w-działaniu-aplikacji)
3. [Chcę zgłosić błąd dotyczący bezpieczeństwa.](#Chcę-zgłosić-błąd-dotyczący-bezpieczeństwa)
4. [Programuję, jak mogę pomóc?](#Programuję-jak-mogę-pomóc)
5. [Zajmuję się UX/UI, jak mogę pomóc?](#Zajmuję-się-uxui-jak-mogę-pomóc)
6. [Chcę pomóc testować nowe wersje aplikacji.](#Chcę-pomóc-testować-nowe-wersje-aplikacji)
7. [Chcę zaproponować nową funkcjonalność.](#Chcę-zaproponować-nową-funkcjonalność)
8. [Jak jeszcze mogę pomóc?](#Jak-jeszcze-moge-pomoc)

## Zasady ogólne

### Język komunikacji

Komunikujemy się po polsku, ponieważ jednym z głównych celów tego projektu jest zbudowanie zaufania do użytkowników aplikacji ProteGO, którymi będą głównie osoby mówiące po polsku. Wiele tematów które poruszamy na GitHub jest czytelnych dla osób nietechnicznych. Nie chcemy zabierać im możliwości partycypacji. Komunikacja po angielsku jest OK, odpowiadamy wtedy po angielsku. 

Kod i komentarze w kodzie piszemy po angielsku. Commity po polsku lub angielsku.

### Kto podejmuje decyzje w tym projekcie?

ProteGO ma jedynie sens jeśli zostanie stworzone we współpracy z administracją. Potrzebujemy połączenia z zaufanym źródłem informacji dotyczącym tego czy ktoś został zakażony SARS-CoV-2. Taki rejestr jest prowadzony przez stronę rządową. Ministerstwo Cyfryzacji (MC) zdecydowało się wydać i promować tę aplikację. Oznacza to jednak również to, że ostatecznie to MC decyduje o tym czy aplikacja i jej kolejne wersje będą wydane. Potrzebujemy więc współpracy i dialogu, który połączy potrzeby i obawy każdej ze stron. **Aktualnie** łącznikiem między MC i projektem jest [@jakublipinski](https://github.com/jakublipinski).

### Jaki jest "roadmap" projektu?

Poza wydaniem wersji `1.0` opisanej [tutaj](https://github.com/ProteGO-app/specs/blob/master/specs/README.md) nie ma jeszcze decyzji co dalej. Na pewno będziemy chcieli zachęcić użytkowników do częstszego zaglądania do aplikacji? Masz pomysł jak to zrobić - napisz.

## Chcę zgłosić błąd w działaniu aplikacji

Używamy `GitHub issues` do śledzenia postępów i błędów. Wypełnij formularz błędu w [aplikacji iOS](https://github.com/anna-app/ios/issues/new?assignees=&labels=&template=bug_report.md&title=), w [aplikacji Android](https://github.com/anna-app/android/issues/new?assignees=&labels=&template=bug_report.md&title=) lub [na serwerze](https://github.com/anna-app/backend/issues/new?assignees=&labels=&template=bug_report.md&title=). Pamiętaj o podaniu wszystkich wymaganych informacji. Zanim zgłosisz coś nowego, sprawdź czy nie ma już wcześniejszego podobnego zgłoszenia.

## Chcę zgłosić błąd dotyczący bezpieczeństwa

Zanim zgłosisz błąd dotyczący bezpieczeństwa aplikacji sprawdź naszą [listę znanych zagadnień dotyczących bezpieczeństwa](specs/security.md). Jeśli chcesz zgłosić coś nowego i jest to krytyczne skontaktuj się z nami bezpośrednio. W przeciwnym wypadku zgłoś błąd przez [`GitHub issues`](#Chcę-zgłosić-błąd-w-działaniu-aplikacji)

## Programuję, jak mogę pomóc?

Jest mnóstwo sposobów w jaki możesz nam pomóc:
* Zrób nam audyt kodu. 
* Przeglądnij listę zadań nad którymi pracujemy. 
* Dodaj swój `Pull Request`. 
* Przeglądnij istniejące `Pull Request`y. 
Komunikuj się z nami przez GitHub.

### Oświadczenie o udzieleniu licencji
Abyśmy mogli akceptować Twoje Pull Request'y zapoznaj się z zasadami poniżej:
1. ProteGO tworzone jest na licencjach Affero GPL (backend) i GPL (pozostałe komponenty)
2. Jeśli dodajesz jakąś zmianę do któregoś repozytorium **pozostajesz jej autorem i właścicielem**, a na mocy *GitHub Terms of Use* automatycznie [udzielasz licencji na swoje zmiany](https://help.github.com/en/github/site-policy/github-terms-of-service#6-contributions-under-repository-license).
3. Dla uniknięcia nieporozumień prosimy każdego twórcę Pull Request'a o potwierdzenie udzielenia licencji na swoje zmiany poprzez:
    * pobranie i wypełnienie [oświadczenia](files/oswiadczenie_licencja_GPL_AGPL.pdf), które:
        * potwierdza udzielenie licencji GPL/AGPL na swoje zmiany
        * zezwala każdemu kto stosuje się do postanowień licencji na dystrybucję binarnych plików przez App Store firmy Apple
        * zobowiązuje autora zmian do niewykonywania swoich osobistych praw autorskich i do nieodwoływania swojej licencji
    * podpisanie go [podpisem zaufanym](https://www.gov.pl/web/gov/podpisz-dokument-elektronicznie-wykorzystaj-podpis-zaufany), [podpisem osobistym](https://www.gov.pl/web/e-dowod/podpis-osobisty) lub [podpisem kwalifikowanym](https://pl.wikipedia.org/wiki/Podpis_kwalifikowany)
    * przesłanie podpisanego dokumentu na adres [protego@mc.gov.pl](mailto:protego@mc.gov.pl). Jako tytuł wiadomości wpisz `Oświadczenie GitHub`. Administratorem Twoich danych osobowych jest Ministerstwo Cyfryzacji.
4. Po podpisaniu i przesłaniu dokumentu, wraz z pierwszym Pull Request'em dodamy Cię do pliku [CONTRIBUTORS.md](CONTRIBUTORS.md). Dzięki temu każdy Twój kolejny Pull Request zostanie zaakceptowany szybciej.
5. Przyjmujemy Pull Request'y tylko od osób, które przesłały oświadczenie.

## Zajmuję się UX/UI, jak mogę pomóc?

Udostępniamy [pliki źródłowe dotyczące UX i UI](https://drive.google.com/drive/folders/1n2-dFkdkJWnezX3RjN1kaSOzHQiUg4iQ?usp=sharing). Jeśli chcesz coś zaproponować jakieś zmiany zgłoś je [tutaj](https://github.com/ProteGO-app/specs/issues)

## Chcę pomóc testować nowe wersje aplikacji

Instrukcja dotycząca tego jak dołączyć do zespołu testerów znajduje się [tutaj](specs/testing.md).

## Chcę zaproponować nową funkcjonalność.

Nowe funkcjonalności planujemy w [GitHub issues](https://github.com/anna-app/specs/issues). Sprawdź wcześniej czy ktoś nie zgłosił czegoś podobnego.

## Jak jeszcze mogę pomóc?

Używaj aplikacji, promuj wśród znajomych, zainstaluj rodzicom. Śledź nas na profilach społecznościowych.

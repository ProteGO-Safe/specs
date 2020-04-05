# Aplikacja ProteGO

For short english introduction click [here](ENGLISH.md)

## Spis treści

1. [Wprowadzenie](#wprowadzenie)
2. [Jak działa aplikacja?](specs/README.md)
3. [Najczęściej zadawane pytania](FAQ.md)
4. [Chcę pomóc, zgłosić błąd, mam pomysł](CONTRIBUTING.md)

## Wprowadzenie

Celem aplikacji jest pomoc w przejściu z ogólnopolskiego lockdown’u do selektywnej kwarantanny osób, które mogły być narażone były na ryzyko zakażenia SARS-CoV-2.

Aplikacja budowana jest przez społeczność obywateli pod kuratelą Ministerstwa Cyfryzacji, wydawcy aplikacji.

Aplikacja równoważy potrzebę zachowania prywatności obywateli z potrzebą zbierania informacji o tym kogo mogły spotkać i zarazić osoby zakażone. 

Aplikacja wymaga podania numeru telefonu i potwierdzenia go wiadomością SMS. Numer telefonu wymagany jest po to aby GIS mógł się skontaktować z użytkownikiem, który był narażony na kontakt z osobami chorymi.

Po zainstalowaniu, aplikacja działa w tle i skanuje otoczenie w poszukiwaniu innych telefonów (poprzez technologię Bluetooth) na których zainstalowana jest aplikacja i zapisuje historię spotykanych urządzeń. 

Dane te przechowywane są wyłącznie na urządzeniach obywateli i nie są przesyłane na żaden serwer centralny.

Dane wysyłane są na serwer dopiero w sytuacji w której u użytkownika aplikacji zdiagnozowano wirusa. W takim wypadku GIS instruuje pacjenta w jaki sposób wysłać dane z telefonu na serwer.

Dane trafiają na serwer gdzie administrator na podstawie ich analizy (długości, częstości, bliskości zgodnie ze standarami WHO) decyduje, które z osób z którymi spotykał się chory powinny poddać się kwarantannie domowej.

Każdy użytkownik może po otwarciu aplikacji sprawdzić jaki jest jego spersonalizowany status:
* Zielony - można swobodnie wychodzić zachowując obowiązujące regulacje
* Pomarańczowy - nie minęło jeszcze 2 tygodnie od zainstalowanie aplikacji, nie mamy wystarczająco dużo danych aby określić status. Należy zachować ostrożność.
* Czerwony - należy skontaktować się z GIS i poddać domowej kwarantannie

Aplikacja docelowo powinna być zainstalowana przez każdego obywatela. Rozpoczynamy budowę kultury używania aplikacji np. poprzez pokazywanie sobie nawzajem swojego zielonego statusu podczas powitania.

Ze względu na zrozumiały opór społeczny przed permanentną inwigilacją obywateli, kładziemy duży nacisk na zadbanie o ochronę prywatności. Kod aplikacji jest upubliczniony (open source) i może być zaudytowany przez ekspertów.

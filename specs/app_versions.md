# Środowiska i wersje aplikacji

## Środowiska pracy

Utrzymujemy trzy środowiska pracy nad aplikacją:

### `Dev` - środowisko rozwojowe

Środowisko do bieżącej pracy nad aplikacją. 

#### iOS

Nowe wersje do testowania budowane są przez programistów i testowane lokalnie lub budowane przez CI i dystrybuowane do testerów przy pomocy [Shuttle](https://www.polidea.com/blog/our-app-distribution-tool-open-sourced-shuttle-case-study/).

Wersje `dev` zawierają w sobie następujące narzędzia i biblioteki:
* Menu deweloperskie dostępne po potrząśnięciu telefonem ([SwiftTweaks](https://github.com/Khan/SwiftTweaks)),
* Integrację z serwisem Firebase Crashlytics,
* Integrację z serwisem Bugfender
* Szczegółowe logi na konsolę

#### Android

Nowe wersje do testowania budowane są przez programistów i testowane lokalnie lub budowane przez CI i dystrybuowane do testerów przy pomocy [Shuttle](https://www.polidea.com/blog/our-app-distribution-tool-open-sourced-shuttle-case-study/).

Wersje `dev` zawierają w sobie następujące narzędzia i biblioteki:
* Menu deweloperskie dostępne po potrząśnięciu telefonem ([Cockpit](https://www.polidea.com/blog/cockpit-22new-features-of-android-debug-menu/)),
* Integrację z serwisem Firebase Crashlytics,
* Integrację z serwisem Bugfender
* Szczegółowe logi na konsolę

#### Backend

Wersje `dev` łączą się z serwerem pod adresem:

https://europe-west3-protego-dev.cloudfunctions.net/

### `Stg` - środowisko przedprodukcyjne

Środowisko przedprodukcyjne do testowania wersji przed publikacją.

#### iOS

Nowe wersje do testowania budowane są przez CI i dystrybuowane do testerów przy pomocy TestFlight.

Wersje `stg` nie zawierają żadnych zewnętrznych bibliotek.

#### Android

Nowe wersje do testowania budowane są przez CI i dystrybuowane do testerów przy pomocy Google Play.

Wersje `stg` nie zawierają żadnych zewnętrznych bibliotek.

#### Backend

Wersje `stg` łączą się z serwerem pod adresem:

https://europe-west3-protego-stag.cloudfunctions.net/

### `Prod` - środowisko produkcyjne

Środowisko produkcyjne.

#### iOS

Nowe wersje do testowania budowane są przez CI i dystrybuowane do testerów przy pomocy TestFlight.

Wersje `prod` nie zawierają żadnych zewnętrznych bibliotek.

#### Android

Nowe wersje do testowania budowane są przez CI i dystrybuowane do testerów przy pomocy Google Play.

Wersje `prod` nie zawierają żadnych zewnętrznych bibliotek.

#### Backend

Wersje `prod` łączą się z serwerem pod adresem:

TBD

## Wersjonowanie aplikacji

Dla iOS i Android obowiązuje wersjonowanie w postaci: `X.Y.Z` gdzie:
* `X` - główny numer wersji
* `Y` - mniejszy numer wersji
* `Z` - kolejny numer budowy (ang. build) aplikacji. 

Numer wersji ustawiany jest przez programistów jako `tag` w repozytorium. Ustawienie `tag` wywołuje budowę projektu. Tagi i wersje mogą być różne dla iOS i Android.

Pierwsza wersja w sklepie może mieć więc numer np. `1.0.127` a kolejna `1.1.234`.

Aplikacje przesyłają do serwera całość `X.Y.Z` jako `app_version`.

Każda wersja budowana jest na postawie `tag`u z GitHub:
* iOS: https://github.com/ProteGO-app/ios/tags
* Android: https://github.com/ProteGO-app/android/tags

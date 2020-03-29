# Lista znanych nam zagadnień dotyczących bezpieczeństwa

### Aplikacje mają zaszyte adresy do serwera Google zamiast CNAME, który można kontrolować.

Wiemy. Podmienimy to jak tylko dostaniemy odpowiedni adres w domenie gov.pl. Tu jest odpowiednie [zadanie](https://github.com/anna-app/specs/issues/11).

### Aplikacja nie weryfikuje wystawcy certyfikatu SSL serwera do którego się łączy.

Wiemy. Poprawimy wkrótce. Odpowiednie zadania są [tutaj](https://github.com/anna-app/ios/issues/22) i [tutaj](https://github.com/anna-app/ios/issues/22).

### Aplikacja jest open-source. Mogę ją zmodyfikować i zainstalować na swoim telefonie wersję, która zawsze będzie pokazywać zielony status. 

Jest wiele sposobów na które można oszukiwać innych ludzi. Aplikacja jest open-source aby każdy mógł zweryfikować jak działa i jakie dane przetwarza.

### Czy dobrze rozumiem, że wystarczy wyłączyć Bluetooth i aplikacja przestaje działać?

Aplikacja wymaga włączenia Bluetooth aby móc rozgłaszać się i widzieć urządzenia innych użytkowników.

### Serwer w żaden sposób nie weryfikuje czy rozmawia z nim Aplikacja czy może ktoś się pod nią podszywa. 

Weryfikacja wiarygodności aplikacji klienckiej po stronie serwera jest nietrywialna. Rozważamy użycie [SafetyNet mobile attestation](https://developer.android.com/training/safetynet/attestation) dla Android i [DeviceCheck](https://developer.apple.com/documentation/devicecheck) dla iOS. Chętnie przyjmiemy sugestie lub Pull Request w tym temacie.

# Server API Specification/Documentation

## API Format

API endpoints are invoked with an HTTP/HTTPS? POST request with the parameters in a JSON body. Each of them returns a JSON response.

## Common parameters
The following parameters are included in every single request:

`platform` : `string ("ios"|"android")`

`os_version` : `string`

`device_type` : `string`

`app_version` : `int`

`api_version` : `int`

`user_id` : `string`

`lang` : `string`

Description of parameters:

`platform` - platform identifier. Currently one of `“android”` and `“ios”`

`os_version` - operating system version

`device_type` - device type (e.g. `"iPhone X"` or `"Android Galaxy"`)

`app_version` - currently installed app version

`api_version`  - API version supported by the application (by default 1)

`user_id` - user identifier assigned by server. Can be empty before registering the user

`lang` - two-letter code for the language of the phone

## `/check_version`

Checks if and update is needed for the application to work correctly

### Request parameters:
Common parameters

### Response:

`upgrade_required` : `bool`

`upgrade_url` : `string`

If `upgrade_required` is `true`, the application informs the user that to keep using the application they need to download a newer version of the application. In that case, `upgrade_url` contains a link to appropriate App Store where the user should be redirected.
In case `upgrade_required` is `false`, the application is started.

## `/register`

A new device is registered in the application.

### Request parameters:
Common parameters and the following:

`msisdn` : `string`  prefix `+48` + 9 digits

`send_sms` : `bool` allows to obtains the verification code in the response. Available only in the development environment.

### Response:
`registration_id` : `string`

`code` : `string` optional, when requested `send_sms: False` Available only in the development environment.

Server returns an error if `msisdn` is not from Poland (i.e. it doesn't start with `+48`).
A verification code is generated and sent to the phone number provided with an SMS.
Following data is stored:
- timestamp of the moment when the registration is started
- the telephone number
- verification code sent
There should be restrictions that limit abuse of this service.

### `/confirm_registration`

Application confirms the registration.

### Request parameters:
Common parameters and the following:

`registration_id` : `string`

`code` : `string`

`registration_id` - registration identifier returned by `/register`

`code` - the verification code obtained by the user

### Response:

`user_id` : `string`

`error_msg` : `string`


Serwer sprawdza czy istnieje bieżąca rejestracja zgodna z parametrami. Jeśli tak, rejestruje użytkownika, zapisuje i zwraca `user_id`. Jeśli nie, zwraca `error_msg`.

## Funkcja `/get_status`

Sprawdzenie swojego statusu i pobranie `beacon_ids`.

### Parametry:

standardowe

`last_beacon_date` : `string`

`last_beacon_date` to data i godzina najstarszego `beacon_id` które jest już przechowywane na urządzeniu.

### Wynik:

`status` : `string`

`beacon_ids` : `[ {“date”: date, “beacon_id”:beacon_id}, ...]`

`date` : `data i godzina w formacie "YYYYmmddHH"`

Serwer zwraca status użytkownika: `"greeen"`, `"orange"` lub `"red"`.  Jeśli nie minęło 14 dni od zainstalowania aplikacji, status jest pomarańczowy (`"orange"`).

Serwer zwraca identyfikatory którymi ma się rozgłaszać w określonych dniach i godzinach na 21 dni do przodu. Każdy `beacon_id` to identyfikator do rozgłaszania. Każdy `date` to data i godzina w formacie `YYYYmmddHH` określająca którym  identyfikatorem `beacon_id` powinien rozgłaszać się telefon w dniu i godzinie określonej przez `date`. Serwer zwraca tylko nowe identyfikatory biorąc pod uwagę `last_beacon_date`. Serwer może nie zwrócić żadnych `beacon_ids` jeśli uzna, że aplikacja ma ich wystarczająco dużo.

## Funkcja `/send_encounters`

Wysłanie listy napotkanych urządzeń na serwer.

### Parametry:
standardowe

`encounters` : `[{“encounters_date”: datetime, “beacon_id”, “signal_strength”}, …]`

`encounters` - `lista napotkanych urządzeń`


`encounter_date` - `data i godzina spotkania`

`beacon_id` - `id napotkanego urządzenia`

`signal_strength` - `siła sygnału przy napotkaniu urządzenia`

Serwer zapisuje dane do tabeli `Encounters` wraz z odpowiednim `user_id`.

# Dane przechowywane na serwerze

## GCP Datastore

### `Users`

`platform` : `string ("ios"|"android")`

`os_version` : `string`

`device_type` : `string`

`app_version` : `int`

`api_version` : `int`

`user_id` : `string`

`lang` : `string`

`msisdn` : `string`

`reg_date` : `datetime`

`last_status_requested` : `datetime`

`status` : `string`


### `Registrations`
`registration_date` : `datatime`

`registration_id` : `string`

`msisdn` : `string`

`code` : `string`

`is_expired` : `bool`


### `Encounter Uploads`

`upload_id` : `string`

`user_id` : `string`

`date` : `datatime`

`processed_by_health_authority` : `bool`

`confirmed_by_health_authority` : `bool`

## GCP BigQuery

### `Beacons`

`user_id` : `string`

`beacon_id` : `string`

`date` : `string w formacie YYYYmmddhh w czasie CET`

### `Encounters`

`upload_id` : `string`

`user_id` : `string`

`beacon_id` : `string`

`encounter_date` : `datetime`

`signal_strength` : `float`

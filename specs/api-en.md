# Server API Specification

## API Format

API endpoints are invoked with a POST request with the parameters in a JSON body. Each of them returns a JSON response.

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

`user_id` - user identifier assigned by server. Can be empty if user is not yet registered

`lang` - two-letter code for the language of the phone

## `/check_version`

Check if an update is needed for the application to work correctly

### Request parameters:
Common parameters

### Response:

`upgrade_required` : `bool`

`upgrade_url` : `string`

If `upgrade_required` is `true`, the application informs the user that to keep using the application they need to download a newer version of the application. In that case, `upgrade_url` contains a link to appropriate App Store where the user should be redirected.
In case `upgrade_required` is `false`, the application is started.

## `/register`

Register a new device in the application.

### Request parameters:
Common parameters and the following:

`msisdn` : `string`  prefix `+48` + 9 digits

`send_sms` : `bool` allows to obtain the verification code in the response instead of text message. Available only in the development environment.

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

## `/confirm_registration`

Confirm the registration.

### Request parameters:
Common parameters and the following:

`registration_id` : `string`

`code` : `string`

`registration_id` - registration identifier returned by `/register`

`code` - the verification code obtained by the user

### Response:

`user_id` : `string`

`error_msg` : `string`

Server checks if the registration exists. If so, the user is registered and stored and the endpoint returns the `user_id`. If not, `error_msg` is returned.

## `/get_status`

Check your status and obtain `beacon_ids`.

### Request parameters:
Common parameters and the following:

`last_beacon_date` : `string`

`last_beacon_date` is the date and time of the latest `beacon_id` that is already stored on the device.

### Response:

`status` : `string`

`beacon_ids` : `[ {“date”: date, “beacon_id”:beacon_id}, ...]`

`date` : `datetime in the following format - "YYYYmmddHH"`

The server returns the user's status: `"green"`, `"orange"` or `"red"`. The status is `"orange"` if 14 days haven't passed since the installation.

The server returns a list of `beacon_id`s to use for broadcasting at specified times for the following 21 days. Each element of the list has a `beacon_id` to broadcast and a `date` in this format: `YYYYmmddHH`. The server will only return new ids taking into account the `last_beacon_date` passed. There may be no `beacon_ids` returned if the application is deemed to have enough `beacon_ids` stored.

## `/send_encounters`

Send a list of encountered devices to the server.

### Request parameters:
Common parameters and the following:

`encounters` : `[{“encounters_date”: datetime, “beacon_id”, “signal_strength”}, …]`

`encounters` - `a list of encountered devices`


`encounter_date` - `date and time of encounter`

`beacon_id` - `id of the encountered device`

`signal_strength` - `strength of the signal during the encounter`

The server stores the data in the `Encounters` table with the appropriate `user_id`.

# Data stored in the server

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

`date` : `string in format "YYYYmmddhh" in the CET timezone`

### `Encounters`

`upload_id` : `string`

`user_id` : `string`

`beacon_id` : `string`

`encounter_date` : `datetime`

`signal_strength` : `float`

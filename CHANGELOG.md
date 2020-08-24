## Version 2.0 functionalities scope

- The User anonymously, without providing any data or enabling any identification, installs the Application on the device with the Android and iOS operating system (waiting for publication),

- The User opens the Application and displays information about the way it works and the necessary consents / permissions (acceptance of the Terms and the Privacy Policy).

- The user completes the health record. The user completes the first risk assessment test (triage).

- The user gets the first result of classification of his state of health (triage).

- The user periodically receives push notifications reminding the need to complete the risk assessment test.

- The application guides the user through advice and recommendations related to his state of health based on a risk assessment (triage).

- The user can fill in any number of times a day: risk assessment test (triage) and health diary.

- After three days, on which the user completed the risk assessment test at least once a day, the “I care for myself and loved ones” badge appears in the Application.

- In the case of an iOS Application - the user must agree to “Permission to send notifications”.

Scope: - purposeful and desirable lack of synchronization with Google Analytics. - lack of in-app user registration based on the phone number. - data from modules: metrics, risk assessment, and health journal are saved locally on the device.

## Version 3.0 functionalities scope

The user downloads or updates ProteGO Safe 3.0 with OpenTrace module, there is no possibility (and no view) to provide the phone number (user does not provide the phone number in the app – we’re not collecting this information in any form). The server grants the application (not the phone number) UID, an anonymized, unique number of this installation (app) – with UID it communicates with the app. For each UID backend generates the TempID (saves on device arrays with the list of TempID numbers for 2 weeks ahead – the app switches TempID every 15 minutes). TempIDs are used to anonymize users in the tracing module (Bluetooth contact).

When the user begins to use the application he is asked to let the app to: - Android: “Using location services” (to scan for nearby devices we need permission for “Location”. In practice it’s required for using the Bluetooth module. App does not use GPS for device geolocation). - iOS: “Permission to use Bluetooth module”. After being granted these permissions, the app turns on the OpenTrace module, running in the background (only on Android system, on iOS the ability to use Bluetooth in the app that’s working “in the background” is highly restricted), also after the user leaves the app and locks the screen (as much as operating system allows it).

The Bluetooth module is not working if the app is closed. The OpenTrace module emits TempID via Bluetooth. App’s TempID is rotated i.e. changed every 15 minutes, in accordance with the base that’s stored on the device – the number of codes will be established using the parameters. The frequency of downloading a new TempID list is also specified as a parameter in configuration.

The OpenTrace module scans the surroundings to detect other users and saves data: timestamp, msg (TempID), Bluetooth signal strength. This data is stored exclusively in the device’s local memory.
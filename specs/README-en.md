# Basic description of the ProteGO app

For the Polish version click [here](specs/README.md)

## Types of users

**User**

Everyone who installs the app.

**Doctor**

Doctor, diagnostician or an employee of the Chief Sanitary Inspectorate, who informs the user that they have been diagnosed with SARS-CoV-2 and instructs them how to share data about their personal history of human contacts to the central server.

**Administrator**

Administrator of the ProteGO system.

## How does the app work?

### Installing and checking the version

The user installs and boots the app.

### Each boot of the app

In case of lacking internet connection, the user is notified and disallowed from continuing.

After booting, the app checks whether the installed version is up-to-date and otherwise asks the user to install a newer version and directs them to the appropriate app store.

### First boot

When booted for the first time (`user_id` missing), the app is registered. The user is presented with starting screens:

* Welcome to the app
* Explanation about how the app works
* Request to turn on Bluetooth. The app does not allow for continuing without turning on Bluetooth (unless it is unable to check Bluetooth status).
* Request for a telephone number. The app prefills the +48 prefix (Polish dialling code). Notice about accepting the app's terms and conditions.
* After confirming, the user receives a text message with a 6-digit code that they input to the app.

### Later boots

The app checks whether Bluetooth is on. If not, the user is asked to turn it on. The app does not allow for continuing without turning on Bluetooth (unless it is unable to check Bluetooth status, then it only issues a reminder).

The app queries the server and displays one of three possible statuses:

* In case of detection of interaction with an infectee - Red

    It is likely you stayed around people who we identified as infectees. Call the closest chapter of the Sanitary Inspectorate. Quarantine yourself at home.
* In case of installation sooner than two weeks ago - Orange

    We don't have enough data to qualify whether you stayed around infectees. Continue using the app. You are recommended to use caution and refrain from going outside.
* Otherwise - Green

    Use standard caution. According to our information, you have not been to the high risk areas.

### Working in the background

The app runs in the background and continually saves the information about devices detected. In case of being closed, the app will attempt to turn itself on again.

### "About the app" window

The user can turn on the "About the app" window. They will find the following information there:
* The app's logo and its version
* User's ID (first half of the `user_id`, the first 8 bytes in the hex format, e.g. `User ID:  a809-8c1a-f86e-11da`)
* The `Send data` button which directs the user to send their data.

[Sending data to the server](data_sharing-en.md)

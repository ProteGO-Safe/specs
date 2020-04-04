# Uploading data from ProteGO to the server

Identifiers of other devices on which the application is also installed and which are located nearby are collected and stored locally (on the device) by ProteGO. The identifiers are randomly generated, they change every hour and hence do not reveal the identities of the owners of nearby devices. ProteGO stores information on the nearby devices for the last 2 weeks. Older data is deleted on an ongoing basis.

Upon identification of a new infected case, employees of the Polish Chief Sanitary Inspectorate (Główny Inspektor Sanitarny, GIS) or the Polish Central Registry of Infections (CRZ) can check in the ProteGO database whether he/she is a user of the ProteGO application. The check is based on the patient's phone number used to register the application.

If an infected person is a ProteGO user, a GIS / CRZ employee calls them or sends a text message with a request to send data from ProteGO to the central system. Example of a message:

``` Thank you for using ProteGO app. Please send information about people who were nearby to warn them of possible infection. Nobody will know about your illness. Open ProteGO, select About application -> Send data. Thank you.```'

The ProteGO system also shows if and when the patient has sent their data on the devices they encountered. The GIS / CRZ employee knows who of the patients sent the data, so he can send reminders to the infected.

After sending the infected patient's data, the server exchanges anonymous device identifiers to phone numbers of application users. A GIS / CRZ employee has access to 2-week history of all users who were near the infected person. For any user who was nearby, GIS / CRZ employees can see their phone numbers and information regarding the contact itself: date, frequency of contacts and signal strength (a measure of proximity). Using this information and available recommendations (e.g. by WHO) the employee decides which users are susceptible and should be contacted immediately to contact.

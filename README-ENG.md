## ProteGO Safe App

## ToC

- [Introduction](#introduction)
- [SARS-CoV-2 infection risk groups](#sars-cov-2-infection-risk-groups)
- [Anonymity and security](#anonymity-and-security)
- [Further principles](#further-principles)
- [[done] Version 2.0 functionalities scope](#done-version-20-functionalities-scope)
- [[done] Version 3.0 functionalities scope](#done-version-30-functionalities-scope)
- [[in progress] Version 4.0 functionalities scope](#in-progress-version-40-functionalities-scope)
- [Security Reports](#security-reports)
- [FAQ](#faq)
- [I want to help, report a bug, or have an idea](#i-want-to-help-report-a-bug-or-have-an-idea)
- [ProteGO Safe and it’s documentation is licensed under](#protego-safe-and-its-documentation-is-licensed-under)

## Introduction

The main goal of the ProteGO Safe mobile app is to provide a tool that can assist and protect users and their families from COVID-19 spread, and ultimately ease the transition between nation-wide lockdown and selective quarantine of people, who were exposed to the risk of COVID-19 infection.

Since 13.03.2020 three teams: ProteGO (Bluetooth tracing), SafeSafe (diagnosis and prevention), and Sigma Connectivity (Bluetooth tracing) were creating their solutions for mobile apps aimed to accelerate this process. The Ministry of Digital Affairs has merged these three teams and established a new name for the app – ProteGO Safe. The app is prepared for the Chief Sanitary Inspectorate (further: GIS), which is also the personal data controller. Minister of Digital Affairs and GovTech Polska due to their experience are supervising the development work.

The app is developed in compliance with principles arising from the General Data Protection Regulation (GDPR), including data minimization, privacy by design, privacy by default, accuracy, and confidentiality. Guidelines of the European Data Protection Board, European Commission, and the Toolbox developed under the eHealth Network operating at the European Commission. All parties involved pay particular attention to ensure the highest privacy standards. The whole project is fully apolitical. Adopted solutions ensure the support for the health authorities in fighting the pandemic while using the minimal set of data, necessary to accomplish that goal.

The Chief Sanitary Inspector, in consultation with the Minister of Digital Affairs, decided to halt further development of the Open Trace standard model striving to distribute the system - mainly due to advanced work on the tool that will provide better coverage while maintaining the distributed model - “Privacy-Preserving Contact Tracing” prepared by the consortium of Google and Apple (with the working name “Exposure Notification”).

The ProteGO Safe team has been invited to test the Exposure Notification solution, thanks to which we can implement a solution that has been designed from the very beginning as a distributed system and thus allows us to protect the privacy of users of tracing applications based on this standard.

ProteGO Safe does not require providing any personal data at any of the stages of using the Application. ProteGO Safe also does not collect personal data. All information processed by ProteGO Safe is collected and processed in such a way as to prevent users from being identified.

Currently, the basic functionality of ProteGO Safe is available, which makes it possible to perform triage, i.e. self-assessment of the risk of contracting COVID-19 disease. The triage functionality is provided by the Infermedica API also used by the pacjent.gov.pl portal. This functionality is being rewritten to be a module that will work locally (offline, i.e. not via the API).

The second key functionality that will be based on the Exposure Notification API enables the so-called Bluetooth tracing. If the user agrees - the application, using the built-in Bluetooth device, will announce a randomly generated, fully anonymous key, which will be replaced every 10 minutes, and simultaneously scan the environment for other phones on which the application is running, and save the history of anonymous keys to evaluate the “quality” of contacts using the Exposure Notification API developed by Google and Apple.

The “quality” of contacts assessment is based on configuration (parameters) provided by the local Health Authority. These parameters determine how much the final results will be impacted by: the duration of the meeting; physical distance between the devices; and how much time has passed since the contact occurred. Based on these parameters, the analytical module provided by G + A gives the result corresponding to the risk of exposure to the virus.

In addition to the estimated risk, information is also returned about the length of the meeting, which is recorded every 5 minutes. For security and privacy reasons, the upper limit of time recording is 30 minutes.

These data are stored only on the devices of the Application users and are not sent to any central server, which is ensured by the Exposure Notification API developed by the Google and Apple consortium. The application deletes the data collected on the device after 14 days from the date they were saved in the Application or at any time at the user’s request (appropriate option in the settings).

In the next version of the application (4.1) the functionalities related to COVID-19 prevention will be extended.

At the moment, since the beginning of the epidemic regardless of whether they’re using the app or not, each person diagnosed with COVID-19 disease is informed by phone about the test result by an authorized representative of the health authority. Soon, this authorized representative of the health authority, after informing about the positive result of the COVID-19 test, will also ask if the sick person has the ProteGO Safe application installed and wants to warn other people who were in its environment following the parameters set by GIS. If so, an authorized representative of the health authority proposes to the application’s user to send their Diagnosed Keys history (only the infected person - without the history of devices encountered) from the last 14 days (maximum) to the server from which the data will be sent further to the devices of the end-users of the application.

Thanks to this, after receiving an anonymous DiagnosedKeys package on the end user’s device, the process of analyzing encountered devices with the ProteGO Safe application installed will be initiated. The analytical module will first check whether the application has “seen” itself with an infected, DiagnosedKey.

If such contact has occurred, the application based on meeting time, the distance between devices, as well as other factors indicated in the GIS guidelines, will decide whether the end-user of the application should receive information about the potential threat of an exposure.

Then the application will display further messages (including the precise phone number for contacting the Contact Center) on how to proceed in case of being in the High-Risk Group of being exposed to SARS-CoV-2.

## SARS-CoV-2 infection risk groups

Every user after turning on the application can check his personalized status:

- Green – low-risk group – user can freely walk out, maintaining regulations in place and basic prevention.
- Orange – medium-risk group – Risk assessment or potential contact with infected person implicate the need for self-observation
- Red – high-risk group – one needs to contact GIS or their doctor.

## Anonymity and security

How will ProteGO Safe version 4.0 based on Exposure Notifications ensure user’s anonymity and data security?

Distributed system: 1) Data is stored on users’ devices. All information (entries in the Health Journal), as well as the history of devices encountered are stored on users’ devices and analyzed there. 2) Data entered into ProteGO Safe allows users to remain anonymous. It is not necessary to register or provide any identifying information. In addition to installing the application, the user only provides his nickname, which can be any, and its only purpose is user comfort. 3) Only people who are medically verified as patients with COVID-19 will be able to initiate the process of sending their Diagnosed Keys (prior to this, Contact Center has to reach the Patient to get a consent to enable appropriate export gateway for data upload - it's required - this consent is made voluntarily by a sick person, thus Contact Center has no means nor rights to do so on behalf of the patient by itself) so that they can send a warning to other users.

## Further principles

- The mobile phone numbers of people diagnosed with COVID-19 disease are processed in Poland by authorized Health Authorities - therefore there is no need to involve the ProteGO Safe application in their acquisition and storage.

- We assume the need for interoperability - data exchange with other projects in Europe and this requires a federation model. A secure standard for data exchange between systems to CT and the possibility of extending the basic model.

- Further development of the informative and educational part of the ProteGO Safe application is needed.

The project is being developed at the request of Ministry of Digital Affairs, by a consortium of companies: Tytani24 Sp. z o.o. (leaders), The Coders Sp. z o.o. , Webini Sp. z o.o. , Sigma Connectivity Sp. z o.o. , 25wat Sp. z o.o. , Klimas Legal, Mobile Flag, HOLDAPP supported by all willing contributors.

Description of the Application versions can be found below:

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

## Version 4.0 functionalities scope [current version]

Version 4.0 is based on the implementation of Exposure Notification API developed by Google and Apple (G + A) in place of the previously used OpenTrace.

The scope of functionality for version 4.0: 
- The user downloads the application or updates it to version 4.0 using the G + A API. 
- According to the requirements for using the API: the user’s device continuously broadcasts temporary identifiers (TemporaryExposureKey), which are taken from the previously generated user pool of keys, changed after a specified time. Simultaneously it’s listening for identifiers issued by other devices. 
- All identifiers are generated in a way that prevents them from being associated with a specific device or user. 
- Contact details are deleted from the user’s device after 14 days [parameter]. 
- The application at least once a day downloads the identifiers of users positively verified by the Chief Sanitary Inspectorate as infected and compares them with the identifiers stored on the user’s device, conducting their analysis and assessment of contact risk if necessary. 
- In case of a prolonged absence of the end-user, after turning on the application, it downloads all not previously obtained ‘infected’ DiagnosedKeys from the last 2 weeks. 
- The analysis of direct contact data is only carried out locally on the end-user’s device. 
- If contact with the patient is detected and the strength of the contact is assessed, the user receives an appropriate push notification. 
- Depending on the category to which a given contact will be assigned, the user receives an appropriate push notification.
- Because of the privacy and security concerns the App disables taking screenshots or screen recording/screencasting.

## Application roadmap

Application is live since June 2020 with full support of Exposure Notification API from Googla and Apple. However, there is still need for further development and maintenence of the application. Below is the list of planned changes, improvements and new features:
- [4.3.X]: Support for other languages (EN, UA) with possibility to add (propose) new translations by the community, Android app update to EN API 1.6, Google based server update to follow changes required by EN API 1.6
- [4.4.X]: Possiblity to report bug/issue in the application, Kill Switch feature (blocking app after pandemic is over), UX/UI changes to improve usability
- [4.5.X]: Interoperability - support for EU solution for exchanging TEKs with other countries through the [Fedaration Gateway solution](https://github.com/eu-federation-gateway-service), especially with DE [Corona Warn App](https://www.coronawarn.app/en/), Huawei no GMS phones support (using Core Contact Shield SDK)


## Interoperability

As most of countries lower their restrictions and exit lock-down there is increase in people traveling to other countries. It is important to support these people in solution that works not only in their home country but is compatible with applications introduced in other countries, too. Thanks to Exposure Notification API that is a most preferred technical solution for contact tracing in most of EU countries it is possible to make all applications that use it to co-exist and recognize contacts with positivly diagnosed people from other countries. An eHealth Network group working under European Commision is responsible for preparing technical solution that will integrate all applications using Exposure Notification API. The proposed and currently discussed option is [Fedaration Gateway](https://github.com/eu-federation-gateway-service) that will be able to share user's TEKs across the integrated countries. Discussions first of all take into account users data privacy aspects.

ProteGO Safe is involved into eHealth Network group, plans to integrate with Federation Gateway and takes part in a piloting program for couple of EU countries.

## Security reports
- [Securitum](audits/SECURITUM_Raport_z_testow_bezpieczenstwa_20200720-PL.pdf)

## FAQ

The FAQ is available here: [FAQ](FAQ.md). (Polish Language version only)

## I want to help, report a bug, or have an idea

Guidelines and Code of Conduct for contributors is available here: [Contributing](.github/CONTRIBUTING.md). (Polish Language version only)

## ProteGO Safe and it’s documentation is licensed under

The application’s source code is available under a well-known and open GPL-3.0 license. Link to the GitHub repository: https://github.com/ProteGO-Safe GNU General Public License v3.0
Permissions of this strong copyleft license are conditioned on making available complete source code of licensed works and modifications, which include larger works using a licensed work, under the same license. Copyright and license notices must be preserved. Contributors provide an express grant of patent rights.

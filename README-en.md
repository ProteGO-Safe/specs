# ProteGO application

For version in Polish click [here](README.md)

## Table of Contents

1. [Introduction](#introduction)
2. [How does the app work?](specs/README-en.md)
3. TBD: [FAQ](FAQ-en.md)
4. [I'd like to contribute, report a bug, have an idea](CONTRIBUTING-en.md)

## Introduction

The purpose of the application is to help move from a nationwide to a selective quarantine of people who may have been exposed to the risk of SARS-CoV-2 infection by enabling contact tracing.

The application is built by the community of citizens in cooperation the Polish Ministry of Digital Affairs, the publisher of the application.

The application balances the need to preserve the privacy of citizens with the need to collect information about those who could be at risk of being infected.

The application can be used anonymously. In this case, all communication with the user is conducted using the application.

Optionally, the user can enter his phone number and confirm it by a text message (SMS). In this case, the phone number can be used by GIS (the Polish Chief Sanitary Inspectorate, Główny Inspektorat Sanitarny) to contact a user who has been exposed to a contact with person identified as ill.

After installing, the app securely connects with other users via Bluetooth. It records a 2 weeks history of all the devices encountered. This data is stored only on citizens' devices and is not sent to any central server. Data is deleted after 2 weeks.

Each person diagnosed with SARS-CoV-2 is asked to send the history of devices encountered during the previous 14 days to the server.

The data is then sent to a server where the administrator, based on their analysis (length of contact, frequency of contacts, proximity in accordance with WHO standards) decides which of the people he met with should receive information about the potential threat. In the case of people who have not registered using the telephone number, the administrator is not able to know their personal data.

After opening the application, each user can check their personalized status:

* Green - you can go out freely and keep the applicable regulations
* Orange - two weeks have not yet passed since the application was installed, we do not have enough data to determine the status. Be careful.
* Red - you should contact the health authorities and subject to self isolation (home quarantine)

Ultimately, the application should be installed by every citizen. We should start creating a culture of using the application, e.g. by showing each other your green status upon meeting each other.

Due to understandable social resistance to the risk of surveillance, we place great emphasis on ensuring privacy. The application code is hence made public (open source) and we encourage independent audit by experts.

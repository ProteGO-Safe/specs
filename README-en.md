# ProteGO application

For version in Polish click [here](README.md)

## Table of Contents

1. [Introduction](#introduction)
2. [How does the app work?](specs/README-en.md)
3. TBD: [FAQ] (FAQ-en.md)
4. TBD: [I'd like to contribute, report a bug, have an idea - unfortunately, still in Polish; please feel free to use the standard methods of communication on GitHub, the team is bilingual] (CONTRIBTUING-en.md)

## introduction

The purpose of the application is to help move from a nationwide to a selective quarantine of people who may have been exposed to the risk of SARS-CoV-2 infection by enabling contact tracing.

The application is built by the community of citizens in cooperation the Polish Ministry of Digital Affairs, the publisher of the application.

The application balances the need to preserve the privacy of citizens with the need to collect information about those who could be at risk of being infected.

The application requires a phone number and its confirmation by a text message (SMS). The phone number is required so that Polish health authorities can contact the user who has been nearby people testing positive.

After installing, the app securely connects with other users via Bluetooth. It records a 2 weeks history of all the devices encountered. This data is stored encrypted only on citizens' devices and is not sent to any central server.

Data is sent to the server only when the user of the application has been tested positive for coronavirus. In this case, the health authority instructs the patient how to send data from the phone to the server.

The data is sent to the server where the health authority personnel, based on their analysis (length, frequency, proximity in accordance with WHO standards), decides which people should be subject to home quarantine.

After opening the application, each user can check their personalized status:

* Green - you can go out freely and keep the applicable regulations
* Orange - two weeks have not yet passed since the application was installed, we do not have enough data to determine the status. Be careful.
* Red - you should contact the health authorities and subject to self isolation (home quarantine)

Ultimately, the application should be installed by every citizen. We should start creating a culture of using the application, e.g. by showing each other your green status upon meeting each other.

Due to understandable social resistance to the risk of surveillance, we place great emphasis on ensuring privacy. The application code is hence made public (open source) and we encourage independent audit by experts.

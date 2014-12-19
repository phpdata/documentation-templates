# Developer/Tester Workflow

### Development / Automated testing (Team member)

**Key**
- Github: Code repository
- Comms: (eg. Slack) Team chat & Services integration (eg. builds, deployment etc)
- CI: (eg. Travis) Continuous Integration / Build Server
- Hosting: (eg. PaaS Heroku)
- Static Code Analysis: (eg. Scrutinizer)

![Alt text](http://g.gravizo.com/g?
@startuml;
actor Member;
participant "Feature/Bug/Tests" as DEVELOPER;
participant "Local Dev ENV" as LOCAL;
participant "Comms" as COMMS;
participant "Github" as GITHUB;
participant "CI" as CI;
participant "Hosting" as HOSTING;
participant "Static Code Analysis" as ANALYSIS;
Member -> DEVELOPER: Code;
activate DEVELOPER;
DEVELOPER -> LOCAL: Do Work;
activate LOCAL;
LOCAL -> GITHUB: Push;
activate GITHUB;
activate COMMS;
GITHUB -> COMMS: Notification;
GITHUB -> CI: Push Hook;
activate CI;
activate HOSTING;
CI -> HOSTING: If Successful;
CI --> GITHUB: If failure;
CI --> COMMS: Notification;
activate ANALYSIS;
CI --> ANALYSIS: Push;
ANALYSIS --> GITHUB: Notification;
deactivate ANALYSIS;
CI -> GITHUB: Notification;
HOSTING --> COMMS: Notification;
deactivate HOSTING;
CI --> GITHUB: Notification;
deactivate CI;
deactivate GITHUB;
COMMS --> DEVELOPER: Notification;
deactivate COMMS;
deactivate LOCAL;
DEVELOPER --> Member: Done;
deactivate DEVELOPER;
@enduml
)

# Task 1 - conveyer operation

Task 1 (PRG1) manages the operation and process of the conveyer belt system.

```plantuml

@startuml
[*] --> Idle : System Started

Idle --> Running : Start Command
Running --> Idle : Stop Command
Running --> Fault : Object Missing

Fault --> Idle : Fault Cleared
@enduml
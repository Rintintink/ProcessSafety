# Task 1 - conveyer belt operation

```plantuml

@startuml
[*] --> Idle : System Initialized

Idle --> Running : Start Command
Running --> Idle : Stop Command
Running --> Fault : Object Missing

Fault --> Idle : Fault Cleared
@enduml
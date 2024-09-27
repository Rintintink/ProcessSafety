# Task 2 - Object detection check

```plantuml

@startuml
[*] --> Idle : System Started

Idle --> DetectObject : Timer Event
DetectObject --> Alarm : Object Missing
DetectObject --> Idle : Object Detected
Alarm --> Idle : Object Restored

@enduml

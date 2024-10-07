# Task 2 - Object detection check

```plantuml

@startuml
[*] --> Idle : System Started

State Idle {
    Idle : Idle af
    Timer -> Hello
}

@enduml

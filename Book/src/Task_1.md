# Task 1 - conveyer operation

```plantuml
@startuml
[*] --> OFF : Power on

state OFF {
    [*] --> WaitingForStart
    WaitingForStart --> IDLE : KN_001 pressed
}

state IDLE {
    [*] --> WaitingForObject
    WaitingForObject --> RUNNING : Object detected
    WaitingForObject --> FAULT : Alarm triggered
}

state RUNNING {
    [*] --> ConveyorRunning
    ConveyorRunning --> IDLE : Conveyor finished transporting
    ConveyorRunning --> FAULT : Alarm triggered
}

state FAULT {
    [*] --> AlarmState
    AlarmState --> IDLE : Acknowledge alarm (KN_002)
}

OFF --> IDLE : KN_001 pressed
IDLE --> RUNNING : Object detected
RUNNING --> IDLE : Transport completed
RUNNING --> FAULT : Alarm triggered
FAULT --> IDLE : Acknowledge alarm (KN_002)

@enduml

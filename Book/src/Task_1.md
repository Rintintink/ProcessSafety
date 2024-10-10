# Task 1 - conveyer operation

```plantuml
@startuml PRG1_Conveyer_Operation

!theme spacelab-white
skinparam backgroundcolor transparent

[*] -right-> OFF : PLC Power-up
OFF --> IDLE : Start Button Pressed
IDLE --> RUNNING : Object Detected &\nWeightime expired
RUNNING --> IDLE : Object Transport\nComplete
IDLE -> FAULT : Alarm\nTriggered
FAULT -> IDLE : Alarm\nAcknowledged

state OFF {
    
    OFF : System is off
}

state IDLE {
    
    IDLE : System is idle
    IDLE : Waiting for object detection
    IDLE : 
    State Detected {
        Detected : Calculate Speed
        
    } 
    
}

state RUNNING {
    
    RUNNING : Conveyer is running
    RUNNING : Measures total runtime from speed
    RUNNING : Calculates progress from speed
}

state FAULT {
    FAULT : System in fault mode
    FAULT : Alarm triggered
}

@enduml






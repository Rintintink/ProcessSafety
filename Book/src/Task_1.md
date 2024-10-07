# Task 1 - conveyer operation

```plantuml
@startuml PRG1_Conveyer_Operation

[*] --> OFF : PLC Power-up
OFF --> IDLE : Start Button Pressed
IDLE --> RUNNING : Object Detected and Weighed
RUNNING --> IDLE : Object Transport Complete
RUNNING --> FAULT : Alarm Triggered
FAULT -[norank]-> IDLE : Alarm Acknowledged

state OFF {
    
    OFF : System is off
}

state IDLE {
    
    IDLE : System is idle
    IDLE : Waiting for object detection
}

state RUNNING {
    
    RUNNING : Conveyer is running
    RUNNING : Measure runtime from speed
    RUNNING : Calculate progress from speed
}

state FAULT {
    FAULT : System in fault mode
    FAULT : Alarm triggered
}

@enduml






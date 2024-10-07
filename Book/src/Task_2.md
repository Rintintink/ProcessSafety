# Task 2 - Object detection check

```plantuml

@startuml

[*] --> Inputs : System Started
Inputs --> PRG1_IDLE : PRG1 in status 1
PRG1_IDLE --> ObjectDetected : LS_001 is HIGH
PRG1_IDLE -> ALARM : Wait time expires
ObjectDetected --> Inputs

ALARM -> Inputs : KN_001 reset
ALARM --> Outputs
ObjectDetected --> Outputs
Outputs --> Inputs

State Inputs {
   Inputs : Set Alarm false
   Inputs : Set WaitTime = 0 sec
}

State PRG1_IDLE{
    
    PRG1_IDLE : Wait for object
    PRG1_IDLE : Count up idle timer
}

State ObjectDetected {
        ObjectDetected : Reset wachttijd
        ObjectDetected : Alarmstatus = false
}

State ALARM {

}
State Outputs {
        
}
@enduml

# Task 2 - Object detection check

```plantuml

@startuml
!theme spacelab-white
skinparam backgroundcolor transparent

[*] --> ReadInputs : System Started
ReadInputs --> PRG1_IDLE : PRG1 in status 1
PRG1_IDLE --> ObjectDetected : LS_001 is HIGH
PRG1_IDLE -> ALARM : Wait time expires


ALARM -> ReadInputs : Alarm\nresetknop
ALARM --> Outputs
ObjectDetected --> Outputs
Outputs --> ReadInputs

State ReadInputs {
   ReadInputs : Set Alarm false
   ReadInputs : Set WaitTime = 0 sec
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
    Outputs : Set GVL Alarmstatus
    Outputs : Set GVL Objectstatus
        
}
@enduml

# Task 2 - Object detection check

```plantuml

@startuml
!theme spacelab-white
skinparam backgroundcolor transparent

[*] -right-> ReadInputs : System Started
ReadInputs -d-> PRG1_IDLE : PRG1 in status 1
PRG1_IDLE --> ObjectDetected : LS_001\nis HIGH
PRG1_IDLE -d-> ALARM : Waittime\nexpires
ALARM -> Outputs : Alarm\nresetknop
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
    ALARM : Reset wachttijd
    ALARM : Alarmstatus = true
}

State Outputs {
    Outputs : Write GVL Alarmstatus
    Outputs : Write GVL Objectstatus
        
}
@enduml

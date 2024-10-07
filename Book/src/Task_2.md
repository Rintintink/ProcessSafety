# Task 2 - Object detection check

```plantuml

@startuml
[*] --> Inputs : System Started
Inputs --> IDLE : PRG1 in status 1
IDLE --> ObjectDetected : LS_001 is HIGH
IDLE --> NoObject : LS_001 stays LOW
ObjectDetected --> Inputs
NoObject --> ALARM : Max Idletime 
ALARM -> Inputs : KN_001 reset
ALARM --> Outputs
ObjectDetected --> Outputs

State Inputs {
   Inputs : Alarm is false
   Inputs : WaitTime = 0 sec
}

State IDLE{
    IDLE : 
}

State ObjectDetected {
        
}

State NoObject {
        
}
State ALARM {

}
State Outputs {
        
}
@enduml

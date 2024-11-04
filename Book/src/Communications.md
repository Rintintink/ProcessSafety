# Communication

```plantuml
@startuml
!theme spacelab-white
skinparam backgroundcolor transparent
skinparam arrowcolor lightblue

actor "Operator" as Operator 
participant "PRG1_Conveyer_Operation" as PRG1
participant "PRG2_Object_Detectie" as PRG2
participant "Global Variables" as GVL
participant "FC Calculate speed" as FC1

Operator -> PRG1: Press KN_001 (start)
PRG1 -> GVL: Set PRG1_Status to IDLE


PRG2 -> GVL: Wait for LS_001 (object detection)
alt No object detected
    PRG2 -> GVL: Countup Wachttijd
    alt Wachttijd >= MaxWachttijd
        PRG2 -> GVL: Set AlarmStatus to TRUE
        GVL -> PRG1: Set PRG1_Status to FAULT
        Operator -> PRG1: Press KN_002 (Acknowledge Alarm)
        PRG1 -> GVL: Reset AlarmStatus
        PRG1 -> GVL: Set PRG1_Status to IDLE
    end
else Object detected (LS_001)
    PRG2 -> GVL: Reset Wachttijd
    PRG2 -> GVL: Continue conveyor operation
    GVL -> PRG1 : Set PRG1_Status to RUNNING
    Operator -> PRG1 : Manually set weight for simulation
    PRG1 -> FC1 : Function call speedcalculation
    FC1 -> PRG1 : return calculated speed
    PRG1 --> PRG1 : Calculate total runtime based on speed and end point
    PRG1 --> PRG1 : Run until progress reaches end point
    GVL -> PRG1 : Set PRG1_Status to IDLE
end
Operator -> PRG1 : Reset KN_001 (stop)




@enduml

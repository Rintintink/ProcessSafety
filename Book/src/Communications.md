# Communication

```plantuml
@startuml
actor "Operator" as Operator
participant "PRG1_Conveyer_Operation" as PRG1
participant "PRG2_Object_Detectie" as PRG2
participant "Global Variables" as GVL

Operator -> PRG1: Press KN_001 (start)
PRG1 -> GVL: Set PRG1_Status to IDLE
PRG1 -> PRG2: Check Object Detection (LS_001)

PRG2 -> GVL: Wait for LS_001 (object detection)
alt Object detected
    PRG2 -> GVL: Reset Wachttijd
    PRG2 -> PRG1: Continue conveyor operation
else No object detected
    PRG2 -> GVL: Countup Wachttijd
    alt Wachttijd >= MaxWachttijd
        PRG2 -> GVL: Set AlarmStatus to TRUE
        PRG2 -> PRG1: Set PRG1_Status to FAULT
    end
end

Operator -> PRG1: Press KN_002 (Acknowledge Alarm)
PRG1 -> GVL: Reset AlarmStatus
PRG1 -> GVL: Set PRG1_Status to IDLE

@enduml

# Communication

```plantuml

@startuml
actor Operator
participant Task1 as "Conveyor Operation"
participant Task2 as "Object Detection"
participant GVL

Operator -> Task1 : Start Conveyor
Task1 -> GVL : Set Conveyor State (Running)
Task2 -> GVL : Read Object Presence
Task2 -> Task1 : Notify Object Missing
Task1 -> GVL : Set Conveyor State (Fault)
Task2 -> GVL : Set Alarm
Task2 -> Operator : Alarm notification
Operator -> Task2 : Reset Alarm

@enduml
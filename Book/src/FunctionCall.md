# Function call

```plantuml
@startuml
!theme spacelab-white
skinparam backgroundcolor transparent


participant Task1 as "Conveyor Operation"
participant Function as "Calculate Conveyor Speed FC"
participant GVL

Task1 -> GVL : Read Load on Conveyor
Task1 -> Function : Call CalculateConveyorSpeedFC(Load)
Function -> Task1 : Output calculated onveyor Speed
Task1 -> GVL : Set Conveyor Speed
@enduml


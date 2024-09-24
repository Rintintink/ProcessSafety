# Function call

```plantuml
@startuml
participant Task1 as "Conveyor Operation"
participant Function as "CalculateConveyorSpeed"
participant GVL

Task1 -> GVL : Read Load on Conveyor
Task1 -> Function : Call CalculateConveyorSpeed(Load)
Function --> Task1 : Conveyor Speed
Task1 -> GVL : Set Conveyor Speed
@enduml


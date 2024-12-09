@startuml
|Human|
start
:Send Command;
|Robot|
:Process Command;
if (Command is "move") then (yes)
    :Move in specified direction;
    :Check for obstacles;
    if (Obstacle encountered?) then (yes)
        :Cannot move;
    else (no)
        :Update battery level;
    endif
else (no)
    if (Command is "pick up") then (yes)
        :Check for object at current position;
        if (Object exists?) then (yes)
            :Pick up object;
        else (no)
            :No object found;
        endif
    else (no)
        if (Command is "place") then (yes)
            :Place object at specified location;
        else (no)
            if (Command is "charge") then (yes)
                :Charge battery;
            else (no)
                :Invalid command;
            endif
        endif
    endif
endif
:Send feedback to Human;
|Human|
:Receive Feedback;
stop
@enduml

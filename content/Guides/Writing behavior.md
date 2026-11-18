---
tags:
  - guide
---

Most of the behavior should be written in the [[OracleWrapper#Update|Update()]] method:
```cs
protected override void Update() {  
   // your logic   
}
```

> [!WARNING]
> Do NOT override Update(bool)! That overload is executed by the room and it contains interfacing logic with the internal oracle systems. Update() with no arguments is also wrapped in a try-catch block in Update(bool) to prevent it from freezing the game if an exception is raised and displays an error screen to the player if one does happen.

# Finite state machine
The library is made primarily for writing oracles with a finite state machine paradigm. To simplify, that is something that can exist in a finite amount of states that govern its behavior and switch between them depending on the context.
It is of course possible to use a different technique, but FSMs were primarily kept in mind during development.
The base setup is akin to this:
```cs
// Define your custom states if necessary
private OracleState.ID Foo = new(nameof(Foo), true);  
private OracleState.ID Bar = new(nameof(Bar), true);  
protected override void Update() {  
    if (State == Foo) {  
        // Foo state logic
        if (barCondition)  
            State.Id = Bar;  
    } else if (State == Bar) {  
        // Bar state logic
        if (fooCondition)  
            State.Id = Foo;  
    }  
}
// Handle state switching
public override void StateSwitch(OracleState.ID newState) {  
    if (newState == Foo) {  
        // ...  
    } else if (newState == Bar) {  
        // ...  
    }  
}
```
`StateSwitch` is called every time you set `State.Id` to a new value.
# Movement
To move the puppet, simply set the [[OracleWrapper#TargetPos|TargetPos]] property, movement logic is taken off automatically. To change the orientation, set the [[OracleWrapper#Angle|Angle]] property.
If you wish to implement your own movement logic, override the [[OracleWrapper#Move]] method.
Use [[OracleWrapper#MoveAroundTarget]] to easily position the puppet around a target position.
# Event response
You can override `IngameEvent` to let the oracle respond to things happening in the room:
```cs
public override void InGameEvent(IngameEvent e, Vector2 position, ITuple eventData = null) {  
    if (e == IngameEvent.PlayerGrabObject) {  
        var data = (Tuple<Player,PhysicalObject>)eventData!;  
        if (data.Item2 is SLOracleSwarmer) {  
            // request to let go  
        }  
    }  
}
```
In this example, we use the `PlayerGrabObject` event which provides 2 data points: the player and the item they grabbed. Most events also additionally provide positional data.
Refer to the [[IngameEvent]] page for a list of all events and their data.
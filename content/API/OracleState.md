---
tags:
  - api
---

Encapsulates some values useful for storing the current state of the oracle.

> [!HINT] Comparing
> This class can be compared directly to [[#ID|ID]] and [[#MovementBehavior]] without having to access the fields:
> ```cs
> State == OracleState.ID.Idle;
> State == OracleState.MovementBehavior.Center;
> ```

---
# Properties
## Id
```cs
public ID Id { get; set; }
```
Stores the current state ID. When this changes, [[OracleWrapper#StateSwitch|OracleWrapper.StateSwitch]] is called with the new value.
## Movement
```cs
public MovementBehavior Movement { get; set; }
```
Stores the current movement behavior.
## Owner
```cs
public OracleWrapper Owner { get; set; }
```
Stores the [[OracleWrapper]] this state is linked to.
## Time
```cs
public int Time { get; }
```
Calculates the time since the state was last changed.
## SwitchTime
```cs
public int SwitchTime { get; set; }
```
Stores the time the state was last switched, used for calculating [[#Time]]. This is set automatically with [[#Id]] changes.
## Progress
```cs
public int Progress { get; set; }
```
Stores the progress, or 'sub-state'. Completely up to your utilization.

---
# Subclasses
## ID
**Base classes**:
- ExtEnum\<ID\>
	- **ID**

The ExtEnum used for storing the state.
Contains states likely to be commonly used:
- Idle
- Welcome
- FirstEncounterSpear
- FirstEncounterArti
- FirstEncounterHunter
- FirstEncounterGourm
- FirstEncounterSurv
- FirstEncounterMonk
- FirstEncounterRiv
- FirstEncounterSaint
- InspectObject
- InspectPearl
## MovementBehavior
**Base classes**:
- ExtEnum\<MovementBehavior\>
	- **MovementBehavior**

The ExtEnum used for storing the current movement behavior.
By default contains:
- Center
---
tags:
  - subclass
  - api
---

Stores placed object data for [[OracleWrapper]].
**Base classes**:
- PlacedObject.Data
	- Pom.ManagedData
		- **OracleWrapper.Data**

# Fields
## ArmArea
```cs
public IntVector2 ArmArea;
```
Stores the area the arm can move around in.
## Broken
```cs
public bool Broken;
```
Whether this oracle is broken (like LttM post-spearmaster or FP during Rivulet and Saint)
## DisconnectedCord
```cs
public bool DisconnectedCord;
```
Whether the umbilical cord is disconnected (like that of post-collapse LttM)
Purely visual.
## BrokenArmBasePos
```cs
public Vector2 BrokenArmBasePos;
```
Stores where the arm base is located if the oracle is [[#Broken]]. Note that this stores the position relative to the placed object's position, and you must convert it to room-relative coordinates first.

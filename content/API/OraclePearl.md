---
tags:
  - api
---
Data pearl that typically resides in a puppet chamber.
**Base classes:**
- UpdatableAndDeletable
	- PhysicalObject
		- PlayerCarryableItem
			- DataPearl
				- PebblesPearl
					- **OraclePearl**
# Constructors
```cs
public OraclePearl(AbstractPhysicalObject abstractPhysicalObject, World world, Color @base, Color highlight, AbstractDataPearl.DataPearlType type)
```
# Properties
## BaseColor
```cs
public Color BaseColor { get; set; }
```
Base color of the pearl
## HighlightColor
```cs
public Color HighlightColor { get; set; }
```
Highlight color of the pearl
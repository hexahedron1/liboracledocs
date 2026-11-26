---
tags:
  - api
---
A wrapper for ProjectedCircle for easier usage
**Base classes**:
- UpdatableAndDeletable
	- **CircleProjector**
Implements **IOwnProjectedCircles**
# Constructors
```cs
public CircleProjector(Vector2 pos, int index = 0, float radius = 180f)
```
- `pos` - see [[#Position]]
- `index` - i don't actually know what this is, but it's present in the ProjectedCircle constructor so it is included here
- `radius` - see [[#Radius]]
# Properties
## Position
```cs
public Vector2 Position { get; set; }
```
The position of the circle.
## Circle
```cs
public ProjectedCircle Circle { get; private set; }
```
The projected circle tied to this object.
## Index
```cs
public int Index { get; set; }
```
¯\\\_(ツ)\_/¯
## Radius
```cs
public float Radius { get; set; }
```
The radius of the circle.
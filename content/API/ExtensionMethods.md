---
tags:
  - api
---

This static class stores some utility extension methods.
# IngameEvent
```cs
public static void IngameEvent(this Room room, IngameEvent e, Vector2 position, [CanBeNull] ITuple eventData = null)
```
Used to raise an [[IngameEvent]] to all [[OracleWrapper|OracleWrappers]] in a room.
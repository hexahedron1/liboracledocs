---
tags:
  - api
  - integration
---

This static class contains references to [Custom Regions Support](https://steamcommunity.com/sharedfiles/filedetails/?id=2941565790) as a soft dependency.

> [!WARNING]
> Check [[Plugin#CrsLoaded|Plugin.CrsLoaded]] before using this class. If it is not loaded, it will result in an exception.
# Methods
## LoadEventsFromFile
```cs
public static void LoadEventsFromFile(Conversation self, string fileName, SlugcatStats.Name saveFile = null, bool oneRandomLine = false, int randomSeed = 0)
```
Calls `CustomRegions.Collectables.CustomConvo.LoadEventsFromFile` with the same arguments.
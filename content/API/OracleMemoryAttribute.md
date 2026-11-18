---
tags:
  - attribute
  - api
---

Marks a field to be recorded in the save file.
**Base classes**:
- Attribute
	- **OracleMemoryAttribute**

This class contains nothing by itself and is only checked for presence by the library.
# Usage
Simply add it to any **public static field**:
```cs
[OracleMemory] public static int Encounters;
```
Now all changes to this field will be saved across cycles and game sessions.
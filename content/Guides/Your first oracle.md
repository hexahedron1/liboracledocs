---
tags:
  - guide
---

The code for this template is available at the [GitHub repo](https://github.com/hexahedron1/LibOracle).
# Creation
Creating an oracle is very simple:
1. Define a class which inherits from [[OracleWrapper]]
   ```cs
   public class TemplateOracle : OracleWrapper { }
   ```
2. Create a constructor and set the ID to a new value (this is used for pearl conversations). It is usually identical to the acronym of the region the oracle resides in.
   ```cs
public TemplateOracle(PlacedObject pobj, Room room) : base(pobj, room) {  
    ID = new OracleID("TMIR", true);  
}
   ```
3. Register it
   ```cs
   // in your OnModsInit
   OracleWrapper.RegisterOracle<TemplateOracle>("Template Oracle");
   ```

Now you can build your mod and launch the game.
With that done you can place the oracle in a room like you would with any other placed object.
![[fig1.png]]
There are some builtin data values that you can use to configure the oracle:
- Broken - this sets if the oracle is broken or not (for more info see [[Data#Broken|OracleWrapper.Data.Broken]]). This primarily makes the arm not move and the projected halo to disappear.
- DisconnectedCord - makes the umbilical cord appear like it does for post-collapse Looks to the Moon (requires a room reload). It is otherwise purely cosmetic.

The large rectangle is the arm area - the arm base moves around the edges of it.
The disconnected handle defines the position the arm base will be placed on if the oracle is broken. The arm base will automatically find the closest point to it on the area's edges.

---
Now that your oracle is ready to flesh out, check these pages for their respective topic:
[[Cosmetics]]
[[Writing behavior]]
[[Dialogue]]
[[Chamber pearl setup]]
These API pages are useful in a lot of cases:
[[OracleWrapper]] for a list of available functions and properties.
[[OracleState]] for storing the current oracle state.
[[OracleMemoryAttribute]] for storing persistent data.
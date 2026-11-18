---
tags:
  - guide
---

To add pearls (or any other object) to the chamber when the oracle is created, you need to override [[OracleWrapper#InitChamberObjects|OracleWrapper.InitChamberObjects]], which is a dedicated method for that. It gets called on the first update of the oracle, to ensure that the objects don't get created at (0, 0) which sometimes happens when adding them from the constructor.
```cs
protected override void InitChamberObjects() {
    AddPearl(Center, new Color(1f, 1f, 1f), this, 1, 20f);    
	AddPearl(new Vector2(220f, 80f), new Color(0.5f, 0.5f, 0.5f));
}
```
[[OracleWrapper#AddPearl|OracleWrapper.AddPearl]] can be used to easily add pearls with all the setup done automatically.
Any other object can be added here as well if you need to.

You can assign a custom data pearl type to the pearls by creating or referencing a `DataPearl.AbstractDataPearl.DataPearlType` member. This is useful for adding custom dialogue different from pebbles' pearls which is the default.
```cs
private readonly DataPearl.AbstractDataPearl.DataPearlType TemplateOraclePearl = new (nameof(TemplateOraclePearl));
```

If you add the pearl dialogue using CRS, you shouldn't re-register the pearl type to avoid duplicates.
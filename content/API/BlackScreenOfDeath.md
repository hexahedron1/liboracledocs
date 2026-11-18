---
tags:
  - subclass
  - api
---

Object that displays an error screen to the end user.
The object will play a sound akin to pre-collapse Look to the Moon's panic attack, make the oracle go unconscious, and display some visuals (synced to the sound) and then english text describing what just happened.
**Base classes**:
- UpdatableAndDeletable
	- **BlackScreenOfDeath**

# Constructors
```cs
public BlackScreenOfDeath(Vector2 pos, OracleWrapper owner, Exception exc, bool myFault)
```
- `pos`: The position of the screen
- `owner`: The [[OracleWrapper]] this screen is tied to.
- `exc`: The exception that triggered this screen. Only used for seeding the random title glyphs.
- `myFault`: Whether the error was caused by the library itself (as opposed to the dependent mod)

---
# Properties
## Pos
```cs
public Vector2 Pos { get; set; }
```
Sets the position of the screen.
## Tick
```cs
public int Tick { get; set; }
```
Stores the amount of ticks the screen has existed for.
## TitleLabel
```cs
public GlyphLabel TitleLabel { get; set; }
```
Stores the title glyph label.
## TitleBlink
```cs  
public int TitleBlink { get; set; }
```
The title is invisible while this is above 0. If so, decrements every tick and when it reaches 0, the title appears.

---
# Fields
## GlyphLabels
```cs
public GlyphLabel[] GlyphLabels = new GlyphLabel[5];;
```
Stores the small glyph label lines below the title that are shown until the human-readable text appears.
## Image
```cs
protected ProjectedImage Image;
```
Stores the image with human-readable text

---
# Methods
## Update
```cs
public override void Update(bool eu)
```
Called every room update.
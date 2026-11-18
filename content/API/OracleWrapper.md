---
tags:
  - api
---

The star of the show (this is what you'll be working with most of the time)

**Base classes**:
- UpdatableAndDeletable
	- PhysicalObject
		- Oracle
			- **OracleWrapper**

# Constructors
```cs
protected OracleWrapper(PlacedObject pobj, Room room)
```
This constructor is used by POM to add the object to a room.

---
# Properties
## Center
```cs
public Vector2 Center { get; }
```
Gets the center of the arm area rectangle.
## BottomCenter
```cs
public Vector2 BottomCenter { get; }
```
Gets the middle of the bottom edge of the arm area rectangle.
## PData
```cs
public Data PData => (Data)PObject.data;
```
Gets the placed object's data.
## SkinColor
```cs
public Color SkinColor { get; set; }
```
Sets the color of the puppet's skin.
## RobeColor
```cs
public Color RobeColor { get; set; }
```
Sets the upper fade limit of the robe.
## RobeFadeColor
```cs
public Color RobeFadeColor { get; set; }
```
Sets the lower fade limit of the robe.
## EyeColor
```cs
public Color EyeColor { get; set; }
```
Sets the color of the puppet's eyes.
## LightColor
```cs
public Color LightColor { get; set; }
```
Sets the color of the puppet's light.
## LightAlpha
```cs
public float LightAlpha { get; set; }
```
Sets the alpha (or intensity) of the puppet's light.
## CrawlSpeed
```cs
public float CrawlSpeed { get; set; }
```
Sets how fast the puppet can crawl around if broken.
## InSitPosition
```cs
public bool InSitPosition { get; set; }
```
Sets if the puppet is in sit position (must be above a solid tile to matter).
## HoldKnees
```cs
public bool HoldKnees { get; set; }
```
Sets if the puppet is holding its knees when sitting.
## State
```cs
public OracleState State { get; set; }
```
Stores the oracle's current state. See [[OracleState]] for more info.
## LookPos
```cs
public Vector2 LookPos { get; set; }
```
Sets where the puppet is looking.
## EyesOpen
```cs
public bool EyesOpen { get; set; }
```
Sets whether the puppet's eyes are open.
## Angle
```cs
public float Angle { get; set; }
```
Sets the angle the puppet's body tries to align itself at (clockwise, 0° = up)
## Conscious
```cs
public bool Conscious { get; set; }
```
Sets whether the puppet is conscious.
## SaveState
```cs
public SaveState SaveState { get; set; }
```
A shorthand to `StoryGameSession.saveState`. Not to be confused with [[OracleMemoryAttribute|OracleMemories]].
## TargetPos
```cs
public Vector2 TargetPos { get; set; }
```
Sets the position to which the puppet's body wants to move to.
Every time this is set the current path is automatically recalculated.
## Pearls
```cs
public List<OraclePearl> Pearls { get; } = [];
```
Stores the oracle's pearls.

---
# Methods
## IsPlayerInEntrance
```cs
public static bool IsPlayerInEntrance(Player player)
```
Gets whether the player is currently in an entrance pipe.
## StateSwitch
```cs
public virtual void StateSwitch(OracleState.ID newState)
```
Called every time the [[OracleState#Id|OracleState.Id]] is changed. Override this to handle state transitions.
## Say
```cs
public void Say(string line, int extraLinger = 0, bool interrupt = false)
```
Shows a message on the dialog box's (or adds a message to its queue if one is being displayed). `extraLinger` sets the extra time that it stays on screen, in ticks. If `interrupt` is true, instead completely skips the queue.
If the player doesn't have the mark, instead plays a voice line (see [[#Voice]])
## Voice
```cs
public virtual void Voice(int? line = null)
```
Plays a voice line. If `line` is null, expected to play a random one. By default plays Five Pebbles' voice.
## StartConversation
```cs
public void StartConversation(Conversation.ID id)
```
Starts a conversation sequence. For defining the lines, see [[#ConversationEvents]]
## ConversationEvents
```cs
protected virtual void ConversationEvents(ConversationWrapper convo)
```
Creates the events for a conversation sequence. For more info, see [[ConversationWrapper]].
## ReplaceParts
```cs
public virtual string ReplaceParts(string s)
```
Called by the conversation to dynamically replace keywords depending on the context. By default, changes nothing.
## SpecialEvent
```cs
public virtual void SpecialEvent(string eventName)
```
Called by the conversation when a special event is reached. `eventName` is the string passed in the event method or after `SPECEVENT : `  in a file. By default, does nothing.
## InGameEvent
```cs
public virtual void InGameEvent(IngameEvent e, Vector2 position, [CanBeNull] ITuple eventData = null)
```
Called when an event occurs in the room. See [[IngameEvent]] for more info.
## SetPalette
```cs
protected internal void SetPalette(int palA, int palB, float blend)
```
Helper method to set the current room's palette.
## Move
```cs
protected virtual void Move()
```
Defines the movement logic for the puppet. In most cases, the default logic is fine, but you can define your own by overriding this method.
## InitChamberObjects
```cs
protected virtual void InitChamberObjects()
```
Called on the first frame after the oracle begins being updated.
This should be used for setting up objects within the chamber instead of the constructor, as sometimes the latter can cause them to appear at the room origin (0, 0).
## Update
```cs
public override void Update(bool eu)
```
The overload called by the room. It is not recommended to override this, as it contains important internal logic and [[BlackScreenOfDeath|error handling]]. Instead, override the variant below.
```cs
protected virtual void Update()
```
This overload is wrapped in `Update(bool)` in a try-catch block to prevent errors from freezing the game. By default contains code to position the puppet in the center of the chamber. It is not necessary to call `base.Update()` when overriding this.
## MoveAroundTarget
```cs
public void MoveAroundTarget(Vector2 pos, float minDist, float maxDist, float changeChance = 0f)
```
Finds a position around a target position and moves the puppet there.
- `pos` - the target position
- `minDist` - minimum distance to the target
- `maxDist` - maximum distance to the target
- `changeChance` - the chance to randomly pick a new position every tick (from 0 to 1)
## AddPearl
```cs
public OraclePearl AddPearl(Vector2 pos, Color color, [CanBeNull] DataPearl.AbstractDataPearl.DataPearlType type = null, Color? highlightColor = null)
```
Adds an [[OraclePearl]] to the room and to [[#Pearls]].
- `pos` - the 'rest' position of the pearl, it will try to float to that position if free
- `color` - the base color of the pearl
- `type` - the type of the pearl. Useful for custom dialogue. Leave `null` to use the default Pebbles' pearl type
- `highlightColor` - the highlight color of the pearl. Leave `null` to default to the base color
```cs
public OraclePearl AddPearl(Vector2 pos, Color color, PhysicalObject orbitObj, int circle, float distance, [CanBeNull] DataPearl.AbstractDataPearl.DataPearlType type = null, Color? highlightColor = null)
```
Same as above, but makes the pearl orbit another object instead of hovering at a fixed position.
- `pos` - the initial position of the pearl
- `orbitObj` - the object this pearl will be orbiting
- `circle` - the circle index the pearl will inhabit. Pearls of the same index will try to arrange themselves with even spacing
- `distance` - the orbit radius from the object
## Pulse
```cs
public void Pulse(Vector2 pos)
```
Pulses a position akin to the player receiving the mark.
## RegisterOracle
```cs
public static void RegisterOracle<TOracle>(string category)
	where TOracle : OracleWrapper
```
Registers an oracle class as a placed object.
- `category` - what DevTools category the placed object will appear in. A new category is automatically created if it is missing.
```cs
public static void RegisterOracle<TOracle, TData>(string category)   
    where TOracle : OracleWrapper   
	where TData   : OracleWrapper.Data
```
Same as above, but allows using a custom Data class. (though it must extend `OracleWrapper.Data`)


---
# Subclasses
[[Arm|Arm]]
[[Behavior|Behavior]]
[[ConversationWrapper|ConversationWrapper]]
[[Data|Data]]


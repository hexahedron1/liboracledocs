---
tags:
  - subclass
  - api
---

Handles conversation sequences for [[OracleWrapper|OracleWrappers]].
**Base classes**:
- Conversation
	- **ConversationWrapper**
# Constructors
```cs
public ConversationWrapper(IOwnAConversation owner, ID id, DialogBox box)
```
- `owner` - the object that owns this conversation.
- `id` - `Conversation.ID` ExtEnum
- `box` - the dialog box this conversation is tied to.

---
# Properties
## Oracle
```cs
protected OracleWrapper Oracle { get; }
```
Gets the oracle this is linked to.

---
# Methods
## AddTextEvent
```cs
public void AddTextEvent(string text, int initialWait = 0, int extraLinger = 0)
```
Helper method for adding a text event (regular dialogue line).
- `text` - the text to be displayed
- `initialWait` - how long to wait until displaying this line, in ticks
- `extraLinger` - how long for this line to remain on screen after the normal timer runs out, in ticks

## AddSpecialEvent
```cs
public void AddSpecialEvent(string eventName, int initialWait = 0)
```
Helper method for adding special events.
## AddWaitEvent
```cs
public void AddWaitEvent(int initialWait)
```
Adds a wait event
- `wait` - how long to wait for, in ticks.
## LoadEventsFromFile
```cs
public void LoadEventsFromFile(string fileName, bool oneRandomLine = false, int randomSeed = 0)
```
Loads conversation events from a file. Searches for the file in the same way as CRS does it, using the current campaign and oracle ID.
> [!WARNING]
> This method uses CRS's api for finding and parsing conversation files, and so it must be enabled for this method to work. This method does nothing without it and only logs a warning.


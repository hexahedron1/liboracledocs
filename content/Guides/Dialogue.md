---
tags:
  - guide
---

To add conversations to your oracle, you need to register a `Conversation.ID` for each conversation sequence:
```cs
private Conversation.ID ExampleConvo = new(nameof(ExampleConvo), true);
```
If you want to add dialogue for an existing conversation ID, this is not necessary.
Then, define the events that make up each sequence. This is done by overriding the [[OracleWrapper#ConversationEvents|ConversationEvents]] method:
```cs
protected override void ConversationEvents(ConversationWrapper convo) {  
    if (convo.id == ExampleConvo) {  
        // ...  
    }  
}
```
There are 2 ways of adding events to the conversation:
- Manual: calling `convo.AddTextEvent`, `convo.AddSpecialEvent` and `convo.AddWaitEvent` for each event to be added.
  ```cs
convo.AddTextEvent("Hello world!");
convo.AddSpecialEvent("testEvent");
convo.AddTextEvent("This line waits a bit before appearing.", 20);  
convo.AddTextEvent("This line stays on the screen for longer.", extraLinger: 60);
  ```
- File-based: calling `convo.LoadEventsFromFile`. This uses CRS's logic for finding the appropriate file based on the oracle's ID and campaign. As such, CRS must be enabled for this to work, otherwise the method does nothing but log a warning.

To trigger the conversation, call `StartConversation` with the ID.
# Pearl dialogue
You can use `Conversation.DataPearlToConversation` to get the pearl's conversation ID, or `Conversation.ID.None` if it was not found. CRS extends this method past vanilla pearls.
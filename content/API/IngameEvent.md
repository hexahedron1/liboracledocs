---
tags:
  - extenum
  - api
---

IngameEvent is an ExtEnum representing the types of events which can be responded to with `InGameEvent(...)`.
Each event type can carry positional and event-specific data with it in the form of a `Vector2` and a tuple.
All events are raised on a room basis, thus the oracle only receives events from the same room.
# Types


> [!NOTE]
> Some events lack additional data due to technical difficulties with retrieving that data

| Name                     | Position data? | Additional data           | What triggers                                                                                                                                             |
| ------------------------ | -------------- | ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PlayerDied               | Yes            | Player                    | A player dying                                                                                                                                            |
| PlayerGrabObject         | Yes            | Player, PhysicalObject    | A player picking up any object (item or creature)                                                                                                         |
| PlayerReleaseObject      | Yes            | Player, PhysicalObject    | A player placing an object on the ground                                                                                                                  |
| PlayerThrowObject        | Yes            | Player, PhysicalObject    | A player throwing an object                                                                                                                               |
| PlayerSwallowObject      | Yes            | Player, PhysicalObject    | A player swallowing an item                                                                                                                               |
| PlayerRegurgitateObject  | Yes            | Player                    | A player regurgitating an item                                                                                                                            |
| PlayerBiteObject         | Yes            | Player                    | A player biting a food item                                                                                                                               |
| PlayerEatObject          | Yes            | Player, IPlayerEdible     | A player fully eating a food item                                                                                                                         |
| PlayerHit                | Yes            | Player, Weapon, Creature  | A player getting hit by a weapon. `Creature` is the creature that hold the kill tag                                                                       |
| PlayerJump               | Yes            | Player                    | A player jumping                                                                                                                                          |
| SpearMake                | Yes            | Player                    | (Spearmaster exclusive)<br>A player making a needle                                                                                                       |
| BombJump                 | Yes            | Player                    | (Artificer exclusive)<br>A player performing a bomb jump                                                                                                  |
| SpearPutOnBack           | Yes            | Player, Spear             | (Hunter exclusive)<br>A player putting a spear on their back                                                                                              |
| SpearTakenFromBack       | Yes            | Player, Spear             | (Hunter exclusive)<br>A player taking a spear from their back                                                                                             |
| CraftObject              | Yes            | Player                    | (Gourmand and Artificer exclusive)<br>A player crafting an item                                                                                           |
| AscensionActivate        | Yes            | Player                    | (Saint exclusive)<br>A player activating ascension flight                                                                                                 |
| AscensionDeactivate      | Yes            | Player                    | (Saint exclusive)<br>A player deactivating ascension flight                                                                                               |
| CreatureAscended         | Yes            | Player, Creature          | (Saint exclusive)<br>A player ascending a creature                                                                                                        |
| OracleAscended           | Yes            | Player, Oracle            | (Saint exclusive)<br>A player ascending an oracle. Not necessarily the oracle that receives this event, if there are multiple in the same room.           |
| TongueAttach             | Yes            | Player, bool              | (Saint exclusive)<br>A player attaches to something with their tongue.<br>The bool value indicates if the attached object is terrain (false if bodychunk) |
| TongueRetract            | Yes            | Player                    | (Saint exclusive)<br>A player retracts their tongue                                                                                                       |
| OracleHitByExplosion<br> | Yes            | Explosion                 | The current oracle is hit by an explosion                                                                                                                 |
| OracleHitByWeapon        | Yes            | Weapon                    | The current oracle is hit by a weapon                                                                                                                     |
| Explosion                | Yes            | Explosion                 | An explosion occurs in the room                                                                                                                           |
| Noise                    | Yes            | InGameNoise               | An InGameNoise occurs in the room                                                                                                                         |
| CycleEndSoon             | No             | No                        | The cycle timer is less than 1 minute                                                                                                                     |
| CycleEnd                 | No             | No                        | The cycle has ended                                                                                                                                       |
| PrecycleEnd              | No             | No                        | The precycle has ended                                                                                                                                    |
| NightStart               | No             | No                        | The night has started                                                                                                                                     |
| SingularityBombThrown    | Yes            | Creature, SingularityBomb | A singularity bomb is thrown in the room (`Creature` is the thrower)                                                                                      |

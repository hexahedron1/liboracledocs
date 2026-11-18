This library makes some bold decisions to omit or replace certain parts of the vanilla oracle system for the sake of being more readable by humans.
# OracleState
OracleState replaces both subbehaviors and Actions, and includes the `movementBehavior` field.
# Behavior classes
Most functionality has been merged into `OracleWrapper`. Internally, it does have a `Behavior` subclass, but that is intended only for compatibility with existing code which was built with the assumption that it is there.
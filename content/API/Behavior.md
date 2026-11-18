---
tags:
  - subclass
  - api
---
Internal class for compatibility with vanilla oracle systems. Contains aliases for properties of [[OracleWrapper]]. Unless you are doing something very low-level, it is not needed to touch this class at all.
**Base classes**:
- OracleBehavior
	- **OracleWrapper.Behavior**\
## Properties
References to private fields are omitted.
```cs
public class Behavior(OracleWrapper o) : OracleBehavior(o) {  
    private OracleWrapper wrapper => (OracleWrapper)oracle; 
    public override Vector2 GetToDir => Custom.DegToVec(wrapper.Angle);  
    public override bool EyesClosed => !wrapper.EyesOpen;  
}
```
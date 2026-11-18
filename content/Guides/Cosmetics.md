---
tags:
  - guide
---

All cosmetic settings should be set up in the class constructor, as the sprites are only initialized once.

> [!Attention]
> Don't use #000000 for black in any color parameter - Rain World interprets that value as fully transparent. Instead, use a very dark gray color, such as `(0.01f, 0.01f, 0.01f)`, that is virtually indistinguishable from black.

# Skin and eye color
Simply set the `SkinColor` and `EyeColor` parameters to whichever color you wish.
# Robe
*aka* cloak, gown, etc.
The robe fades from one color to another, so there are 2 parameters for it:
- `RobeColor` - the color at the top end of the gradient
- `RobeFadeColor`  - vice versa, at the bottom
# Light
The body light of the oracle has 2 parameters - `LightColor` and `LightAlpha`, which set the color and alpha (opacity/strength) of the light respectively.
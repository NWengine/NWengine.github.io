# Transform
Transform is one important the most used component by other component, and by other parts of the engine.
The main intend of this component is to be used to situate objects in world coordinate.

## Attributes
|Type 	            | Attribute
|-------------------|----------
|       fVec2       |    position 
|       fVec2       |    scale

## Inheritance
+ [GameComponent](GameComponent.html)

## Description
Scale is a vector that get multiplied to the original size of a primitive (generally contained within a sprite) to get the actual object size.
Since world coordinates are in pixels, each position coordinate get ceiled before vertices transformation. The use of float vector `fVec2`here instead of `iVec2` serves the interpolation, avoiding the user to use other variables to store inbetween values.








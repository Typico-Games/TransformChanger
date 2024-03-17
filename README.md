# TransformChanger
Tool for real-time transform switching in Unreal Engine. 

This github repository includes source code for this tool. This tool is also on Unreal Engine marketplace as a free plugin. It is part of tools created for VR game [Next Move](https://www.meta.com/cs-cz/experiences/6785834628189984?ranking_trace=106799090815324_6785834628189984_QUESTSEARCH_1CIOhKO7vzRZvA7Ca_eyJwbGF0Zm9ybSI6ImFuZHJvaWQtNmRvZiIsInF1ZXJ5X3N0cmluZyI6Im5leHQgbW92ZSIsImxvY2FsZSI6ImNzX0NaIiwibnVtX2ZldGNoIjoxMDEsInNlYXJjaF9yb3V0ZSI6IndlYiIsInRhZ19pZHMiOltdfQ%3D%3D_eyJzZWN0aW9uX2tleSI6IlNFQVJDSCJ9) by [Typico Games](https://typicogames.com)


# Setup

1. Place TransformChanger Actor in viewport
2. Group every actor you want to manipulate.
3. Fill GroupActorSelection variable in TransformChanger with desired GroupActor
4. Press "Add Actors to global selection" button in TransformChanger. Make sure every actor is set to Movable
5. Set CurrentTransformId to 0
6. Directly in the viewport, apply your preferred transformations to each individual actor added (Actors don't have to be grouped now)
7. Press "Update Actor Transforms" in TransformChanger
8. Set CurrentTransformId to 1
9. Directly in the viewport, apply your preferred transformations to each individual actor added (Actors don't have to be grouped now)
10. Press "Update Actor Transforms" in TransformChanger
11. Change CurrentTransformId between 0 and 1 in editor and you'll see their two positions. Location is relative to TransformChanger Actor, so you can move TransformChanger Actor to offset desired locations.
12. Simulate Game.
13. Press button "Change Transform" and you'll see how transforms are switching.


Now you can define as many transforms you want to and modify it's behaviour with additional parameters.

When used for your project access ChangeTransforms function in TransformChanger. It has optional parameter defining desired Transform. If not filled, it has value of -1. That means Switch is made to next transform.

Function ChangeTransforms is also a blueprint node.


# Sounds

You can define sounds for moving and impact for each Actor. MovingSound and ImpactSound audio component are main definitions. When creating transforms, each sound will be played from each of the actors root with same attenuation settings. Can be customized in TransformChangerData.

# Parameter Explanations

### `GroupActorSelection`
- **Type**: `AGroupActor*`
- **Description**: This property is a pointer to a `AGroupActor` instance. Use it to select a group of actors that you want to add to the TransformChanger configuration. The "Button Add Actors to global selection" feature will add the selected group actor to your configuration, enabling you to easily manage groups of actors for transformation purposes. Initially, this is set to `nullptr`, meaning no group actor is selected by default.


### `CurrentTransformId`
- **Type**: `int32`
- **Description**: Represents the index of the current transform being displayed or edited. Set this to `0` for the first transform, `1` for the second, and so on. This allows you to switch between different transforms in the editor for quick adjustments.

# TransformChanger
Define and change in real-time any Actors transform in the world. Needs interaction system so it can be used with default trigger system. 


This github repository includes source code for this tool. This tool is also on Unreal Engine marketplace as a free plugin. It is part of tools created for VR game [Next Move](https://www.meta.com/cs-cz/experiences/6785834628189984?ranking_trace=106799090815324_6785834628189984_QUESTSEARCH_1CIOhKO7vzRZvA7Ca_eyJwbGF0Zm9ybSI6ImFuZHJvaWQtNmRvZiIsInF1ZXJ5X3N0cmluZyI6Im5leHQgbW92ZSIsImxvY2FsZSI6ImNzX0NaIiwibnVtX2ZldGNoIjoxMDEsInNlYXJjaF9yb3V0ZSI6IndlYiIsInRhZ19pZHMiOltdfQ%3D%3D_eyJzZWN0aW9uX2tleSI6IlNFQVJDSCJ9) by [Typico Games](https://typicogames.com)

TransformChanger requires InteractionSystem plugin to install, but there is no need to use it. InteractionSystem is able connect all plugins from TypicoGames and also provides set of trigger systems. 

# Use Cases

This system enables you to create situations like:
 - Shooting target location of door.
 - Area triggers magical bridge that repositions itself
 - Custom DeathTrap actor represented by spikes goes up when player steps on platform.
 - 40 different cubes that are flying in the world will reposition themselfs into platforms when player steps into BoxTrigger

# Base Setup

1. Place TransformChanger Actor in viewport
2. Group every actor you want to manipulate. Make sure Actors are movable.
3. Set CurrentTransformId to 0
4. Directly in the viewport, apply your preferred transformations to each individual actor added (Actors don't have to be grouped now)
5. Click on TransformChanger Actor (selecting BP_TransformChanger saves your transforms)
6. Set CurrentTransformId to 1
7. Directly in the viewport, apply your preferred transformations to each individual actor added (Actors don't have to be grouped now)
8. Click on TransformChanger Actor (selecting BP_TransformChanger saves your transforms)
9. Change CurrentTransformId between 0 and 1 in editor and you'll see the change of your defined transforms.
10. (Location is relative to TransformChanger Actor, so you can move TransformChanger Actor to offset desired locations.)
11. Simulate Game.
12. Press button "SetNextTransform" and you'll see how transforms are switching.


Now you can define as many transforms you want to and modify it's behaviour with additional parameters.

When used for your project access SetDesiredTransform function in TransformChanger. It has optional parameter defining desired Transform ID. If not filled, it has value of -1. That means TransformChanger switches to next transform.

Function SetNextTransform switches to consequent transform configuration.

SetNextTransform and SetDesiredTransform is also a blueprint node.


# Example Map

- Check content in folder called "Levels".
- There is a showcase for this tool.

# Sounds

You can define sounds for moving and impact for each Actor. MovingSound and ImpactSound audio component are main definitions. When creating transforms, each sound will be played from each of the actors root with same attenuation settings. Can be customized in TransformChangerData.

# Parameter Explanations

### `GroupActorSelection`
- **Type**: `AActor*`
- **Description**: This property is a pointer to an `AActor` instance. Use it to select a group of actors that you want to add to the TransformChanger configuration. Utilizing the "Button Add Actors to global selection" feature will incorporate the selected actors into your configuration, facilitating the management and transformation of actor groups. Initially, this is set to `nullptr`, which means no actor group is selected by default.

### `CurrentTransformId`
- **Type**: `int32`
- **Description**: Represents the index of the current transform being displayed or edited in the editor. Assign `0` for the first transform, `1` for the second, and so on, allowing for seamless switching among different actor transforms for efficient editing.

### `NumberOfTransforms`
- **Type**: `int32`
- **Description**: Displays the maximum number of transforms that can be switched between. For example, a value of `3` indicates there are three different transforms available for each actor. This property is visible in the editor for reference but cannot be modified directly.

### `TransformChangerData`
- **Type**: `TArray<FTransformChangerData>`
- **Description**: Houses the main configuration for actor transforms. Add actor-specific transformation data here to utilize within the Transform Changer. Leveraging the group adding button feature can expedite the configuration process.

### `InterpType`
- **Type**: `TEnumAsByte<EInterpType::Type>`
- **Description**: Determines the type of interpolation between transforms, whether constant or scaled based on distance. This choice affects how smoothly actor transforms transition from one state to another.

### `MinGlobalRotationSpeed`, `MaxGlobalRotationSpeed`, `MinGlobalLocationSpeed`, `MaxGlobalLocationSpeed`, `MinGlobalScaleSpeed`, `MaxGlobalScaleSpeed`
- **Type**: `float`
- **Description**: These properties define the minimum and maximum speeds for randomizing each actor's rotation, location, and scale movements. Adjust these to set the range of possible speeds. The "Set interp transform" button activates these settings.

### `ConstantGlobalSpeed`
- **Type**: `float`
- **Description**: Defines a constant speed applied globally to all actors' transformations, irrespective of the individual speed settings.

### `MovingSoundFadeOutDuration`, `MovingSoundFadeInDuration`
- **Type**: `float`
- **Description**: Specify the duration for fading out and fading in the moving sound, respectively. These settings help create smoother audio transitions for moving actors.

### `LocationThresholdForSound`, `RotationThresholdForSound`, `ScaleThresholdForSound`
- **Type**: `float`
- **Description**: Set the thresholds for location, rotation, and scale at which the stop sound for movement will trigger. These thresholds help determine when an actor's movement is considered complete.

### `InterpolatedDelta`
- **Type**: `float`
- **Description**: Represents the delta time used for interpolation calculations. This helps in smoothing behavior in lower FPS situations by adjusting the interpolation rate.

### `InterpolatedDeltaSpeed`
- **Type**: `float`
- **Description**: Controls the speed of interpolation adjustments when experiencing lower FPS, ensuring smoother actor movements and transitions under varying performance conditions.

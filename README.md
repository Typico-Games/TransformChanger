# TransformChanger
Tool for real-time transform switching in Unreal Engine. 

This github repository includes source code for this tool. This tool is also on Unreal Engine marketplace as a free plugin. It is part of tools created for VR game [Next Move](https://www.meta.com/cs-cz/experiences/6785834628189984?ranking_trace=106799090815324_6785834628189984_QUESTSEARCH_1CIOhKO7vzRZvA7Ca_eyJwbGF0Zm9ybSI6ImFuZHJvaWQtNmRvZiIsInF1ZXJ5X3N0cmluZyI6Im5leHQgbW92ZSIsImxvY2FsZSI6ImNzX0NaIiwibnVtX2ZldGNoIjoxMDEsInNlYXJjaF9yb3V0ZSI6IndlYiIsInRhZ19pZHMiOltdfQ%3D%3D_eyJzZWN0aW9uX2tleSI6IlNFQVJDSCJ9) by [Typico Games](https://typicogames.com)


# Documentation

1) Place TransformChanger Actor in viewport




## Property Explanations

### `CurrentTransformId`
- **Type**: `int32`
- **Access**: Editable in the Unreal Editor.
- **Category**: Configuration
- **Description**: Represents the index of the current transform being displayed or edited. Set this to `0` for the first transform, `1` for the second, and so on. This allows you to switch between different transforms in the editor for quick adjustments.

### `NumberOfTransforms`
- **Type**: `int32`
- **Access**: Visible but not editable in the Unreal Editor.
- **Category**: Configuration
- **Description**: Shows the total number of transforms available or configured. This property is automatically updated and provides a quick reference for the number of transforms defined.

### `TransformChangerData`
- **Type**: `TArray<FTransformChangerData>`
- **Access**: Editable in the Unreal Editor.
- **Category**: Configuration
- **Description**: This is the main configuration array for the transforms associated with each actor. Add actors and their corresponding transforms here to be used by the Transform Changer. Utilize the group adding button feature to streamline the process when configuring multiple actors. This array holds all the necessary data to switch transforms among the specified actors.

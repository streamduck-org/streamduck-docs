# Component Parameters
Component parameters represent things that components allow you to change, renderer component allows you to change the way the button will look like and etc.

Streamduck has 2 things that support parameters - module settings and component parameters

## Listing parameters
To list parameters of a module or component, you can use following command depending on which of the 2 you want to check:
```shell
button component params list <key index> <component name>
```
or
```shell
module params list <module name>
```
After running the command, you'll see a list of all parameters that the component or module provides, each parameter will have a name, description, path, type and current value

## Parameter types
Parameters come in all various ways and each accept different inputs, you can refer to this table to see what parameter type accepts what

| Type             | What it accepts                                                                                                                                                          |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Header           | Doesn't accept anything, just large text for UI to render                                                                                                                |
| Label            | Doesn't accept anything, meant to be a small textbox that cannot be changed                                                                                              |
| Float            | Accepts decimal fractions, example: 0.1; 35; 6546.241253                                                                                                                 |
| Integer          | Accepts whole numbers, example: 3; 6783; 3153; 53                                                                                                                        |
| String           | Accepts any text, spaces don't need to be escaped                                                                                                                        |
| Float2           | Accepts 2 decimal fractions one after the other, example: 0.1 0.2                                                                                                        |
| Integer2         | Accepts 2 whole numbers one after the other, example: 1 2                                                                                                                |
| Positive Integer | Accepts a positive whole number, negative numbers will get an error                                                                                                      |
| Choice           | Accepts a choice from predetermined ones, need to be written as they were specified in the parameters list, spaces don't need to be escaped                              |
| Boolean          | Accepts either `true` or `false`                                                                                                                                         |
| Color            | Accepts 4 numbers in succession with range from 0 to 255, example: 255 35 0 255                                                                                          |
| Submenu          | Doesn't accept anything, meant to be just a submenu in UI for organization of parameters                                                                                 |
| Array            | Doesn't accept anything on its own, see [following section](#dealing-with-arrays) for more info on arrays                                                                |
| ImageData        | Accepts base64 data that represents image binary data of supported format, you can insert base64 string here, or use [upload](#uploading-images-into-parameters) command |
| ExistingImage    | Accepts image identifier of an existing image, see [image list](commands.md#image-list-preview-size) command to get identifiers for uploaded images                      |
| Font             | Accepts font name, see [font list](commands.md#font-list-command) command for font names                                                                                 |

## Setting parameters
After you figured out what you want to set, copy the path of the parameter and see what you can set to it based on the table above, you can use following command to set parameters
```shell
button component params set <key index> <component name> <path to parameter> <value to set>
```
or
```shell
module params set <module name> <path to parameter> <value to set>
```
If the value you want to set is the text kind, spaces will be preserved, so everything after the path will be the value

## Uploading images into parameters
You can use following command to upload images as parameter value, only supported by ImageData type
```shell
button component params upload <key index> <component name> <path to parameter> <path to file>
```
or
```shell
module params uplaod <module name> <path to parameter> <path to file>
```

## Dealing with arrays
Arrays represent parameters that can have multiple elements. You cannot set to array directly, but you can add elements to it, remove elements and set values to its elements.

### Adding elements to arrays
You can add elements to arrays using following command, path to the array means you need to copy path of the parameter that has the type `Array`
```shell
button component params add <key index> <component name> <path to the array>
```
or
```shell
module params add <module name> <path to the array>
```
This will add a new element at the end of the array

### Removing elements from arrays
Use following command to remove elements from arrays

Index of the element can be inferred from the path, as elements of arrays get suffixed with a number which represents their index. So `text_params.text.0.text` means the parameter is located in element with index of 0
```shell
button component params remove <key index> <component name> <path to the array> <index of the element> 
```
or
```shell
module params remove <module name> <path to the array> <index of the element>
```
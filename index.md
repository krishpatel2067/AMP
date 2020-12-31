# AMP - Array Modifier Plugin

AMP is a plugin made to easily create arrays of parts to alleviate any need to manually perform repetitive steps. There are many features to suit almost any situation, and of course, I'll add more as time goes on.

Please note that this is my first plugin and therefore, there may be bugs I have overlooked. So, please be patient!

___

## Getting Started
Visit SITE to install the plugin to Roblox Studio.

1. Open the widget by clicking on the plugin icon:

 ![Plugin button](Plugin_Button.png)

2. Select a part or multiple parts. 
3. The last part selected will be shown along with its class name [1]. Under it, you can add the modifier for all selected parts, by clicking on the corresponding button [2].

![Add button](Add_Part.png)

4. You will see all the settings currently available. Let us understand what each one does in the section below.

![Settings](Settings.png)

Notice the "Apply" button. Until you click it, any change of settings will reflect only a *preview* of the result. To actually create the result, you must apply the modifier by clicking the button. Once you apply,  you cannot change the settings and you'll have to add the modifier to the part again.
___
## Features

### Offset
There are two modes, which can both be on/off at the same time or have only one of them on.
* **Constant** - using studs to position each array part
* **Relative** - using factors of the size of the original part to create incrementally units

For each option, there are 3 input fields for the X, Y, and Z directions. Entering a positive number will shift them in the position direction while entering a negative number will shift them in the opposite direction.

Relative offset is useful when the size of the part is an inconvenient decimal to write out and you want a continuous array without gaps or overlaps. Inputting 0 as the factor will have the series of parts be exactly in the same position as the original one. Inputting 1 will shift them in that given direction and each array part will be exactly touching the adjacent one without overlapping. 

Since you can have constant and relative offset both on at the same time, you can tweak its behavior to better suit the situation. For example, by default, constant offset is a measure of the distance between the *center* of the previous array part and the current one. 

The part below is of size 4 in the X-direction. Offsetting it by 3 will leave a 1 stud overlap between each part.

![Constant enabled only](Only_Constant.png)

If you want it to be distance between the *edges* of the parts, all you need to do is enable relative offset and input 1 for that given direction.

This is after setting the X relative offset to 1 while keeping the constant offset enabled. As you can see, now it's 3 studs between the *edges* of parts.

![Relative and constant enabled](Relative_And_Constant.png)

### Array Type
* **Fixed count** - create a set number of parts with a defined offset
* **Fit to length** - create as many parts as needed to fit a certain length with a defined offset
* **Endpoint incremental** - create a set number of parts between two "endpoint" parts where the offset is automatically set

The last one deserves a bit more explanation. It creates a series of parts between two selected parts, called endpoints. You do not need to input the offset for this as it will automatically be calculated based on the distance between the endpoints and the required count input. If either endpoint is moved, then the array of parts in between will be adjusted to stay on that imaginary "line" between them.

Unlike the other two types, endpoint incremental needs to have the count be n + 2 where n denotes the number of parts in between the two endpoints.

> NOTE: This mode is in alpha, please use with patience. I plan to add more features to it and eliminate bugs.

### Axis Type
* **Local** - use the vectors of the part's faces
* **Global** - use the world axes 

The difference between the two is seen when you rotate the original part. 

This is the result with local selected:

![Local axis type](Local.gif)

In local mode, the array parts move with the rotation of the original part and their axis is one of the part's face vectors (such as -Z being the look vector etc.).

In contrast, this is what happens when global is selected.

![Global axis type](Global.gif)

Global mode can be useful in certain cases if you just want the array parts to rotate while being stationary on a global axis. This will limit you to the 6 axis (+X, +Y, +Z, -X, -Y, and -Z) and diagonals are not possible.

> Note: Axis Type is not configurable when endpoint incremental is selected.

## Toggle Preview
Using this button, you can choose if you would like to view the preview parts before applying:

![Toggle preview button](Hide_Preview.png)

This is purely visual, it does not change any setting. If you apply while the preview parts are hidden, it will still function as intended.
___

## Current Issues/Warnings
* Undo/redo isn't exactly "compatible" with this yet, so please be cautious when using it. If you undo, then the output may fill up with warnings stating the parent property of certain instances is locked. This is due to them already being destroyed, and hitting undo with try to revive them which will cause problems. This isn't a destructure issue, just an annoying one.
* I have not yet set up a system to filter all the text boxes yet, so refrain from entering invalid inputs such as a string.
* Other bugs not listed here will occur, especially since this is my first experience in creating and publishing a plugin. Please post it in the plugin release's DevForum post and include specific reproduction steps. 
___
## My Todo List
Priority levels:
[1]  - High (almost guaranteed)
[2] - Moderate (less guaranteed)
[3] - Low (not very likely)

- [ ] [1] Fixing bugs (of course)
- [ ] [1] Trying to work out the whole undo/redo situation
- [ ] [1] Optimize code
- [ ] [2] Allow endpoint incremental to work with 2+ parts e.g. selecting 3 parts will create a "triangle" of array parts in between.
- [ ] [3] Adding an object transformation mode to create more advanced structures
___
## Closure
Thank you all for using this plugin. I appreciate your patience with my novelty with plugins in advance! With reporting bugs or requesting features, just know beforehand that I am considering all feedback, but I may be delayed in delivering a response and/or the update.

(If you are reading this on the day of release then Happy New Year!)

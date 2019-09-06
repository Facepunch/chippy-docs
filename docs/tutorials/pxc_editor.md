# Pixel Editor

The **PxcEditor** is used to draw units, assign pixels, create animations, and export them to json files.

Download for Windows: [PxcEditor_v35.rar](https://files.facepunch.com/ryleigh/1b0311b1/PxcEditor_v35.rar)

<img src="https://files.facepunch.com/ryleigh/1b1511b1/PxcEditor_2019-08-15_20-49-04.png" width="100%"/>

### Brush

To select the brush: press ++b++, click the `B` button in the toolbar, or eyedrop a colored pixel. <br>
Use ++"LMB"++ to draw on the canvas.<br>
Press ++p++ or click the `PP` button in the toolbar to toggle **pixel perfect drawing**.
Press ++x++ to swap swatch colors.

### Eraser

To select the brush: press ++"E"++, click the `E` button in the toolbar, or eyedrop a blank pixel.<br>
Use ++"LMB"++ to erase pixels on the canvas.<br>

### Flood-Fill

To select flood-fill: press ++"G"++, or click the `G` button in the toolbar.<br>
Use ++"LMB"++ to fill an area on the canvas.<br>

*Quick flood-fill:*<br>
If you have the **brush** selected, ++ctrl+"RMB"++ to fill an area.<br>
If you have the **eraser** selected, ++ctrl+"RMB"++ to erase an area.<br>

### Eyedropper

Use ++"RMB"++ on a colored pixel to select that color.<br>
Use ++"RMB"++ on a blank pixel to select the eraser.<br>
Use ++"Scroll Wheel"++ to adjust color brightness.<br>

### Shapes

*While using the **brush** or **eraser**:*<br>
Hold ++shift++ to draw a line.<br>
Hold ++shift+alt+"LMB"++ to draw a rectangle.<br>
Hold ++shift+alt+"RMB"++ to draw a filled rectangle.<br>
Hold ++shift+alt+ctrl+"LMB"++ to draw a circle.<br>
Hold ++shift+alt+ctrl+"RMB"++ to draw a filled circle.<br>

## Selection

Hold ++"RMB"++ and drag on the canvas to select a rectangle.<br>
And/or hold ++shift++ to add to current selection.<br>
And/or hold ++ctrl++ to select individual pixels.<br>
And/or hold ++alt++ to deselect selection rectangles.<br>

Hold ++"LMB"++ on a selection rectangle and drag to move all selected pixels.<br>
Press ++del++ to clear all selected pixels.<br>
Press ++"Arrow Keys"++ to nudge selected pixels.<br>

Press ++c+"RMB"++ to select all pixels of the same color.<br>
Press ++v+"RMB"++ to flood-select an area.<br>

To select everything, use ++ctrl+a++
To deselect everything, either use ++ctrl+d++ or use ++"RMB"++ on the canvas without dragging.

### Copy & Paste

Use ++ctrl+c++ to copy current selection.<br>
Use ++ctrl+x++ to cut current selection.<br>
Use ++ctrl+v++ to paste. Pasted pixels can be dragged around before they become permanent.<br>

## Canvas Panel

<img src="https://files.facepunch.com/ryleigh/1b1911b1/PxcEditor_2019-08-19_21-02-50.png" width="100%"/>

Hold ++"RMB"++ on the edge and drag to **move** it around.<br>
Hold ++"RMB"++ on one of the corners and drag to change the canvas **dimensions**.<br>
Hover over the panel and use ++alt+"Scroll Wheel"++ to **resize** it.<br>

Click the ++"◩"++ button on the right side of the toolbar to switch between **dark** and **light** canvas backgrounds.<br>

## Layer Panel

Use layers for reference or testing different variants.<br>
The unit you export must all be on a single layer.

<img src="https://files.facepunch.com/ryleigh/1b1611b1/PxcEditor_2019-08-16_20-26-57.png" width="100%"/>

Hold ++"RMB"++ on the panel to be able to **move** it around.<br>
Hold ++"RMB"++ on one of the corners and drag to change the **number of layers** shown.<br>
Hover over the panel and use ++alt+"Scroll Wheel"++ to **resize** it.<br>

Use ++"LMB"++ on a layer to **select** it.<br>
Use ++"RMB"++ on a layer to **toggle** it on and off.<br>
Use ++ctrl+"RMB"++ on a layer to **delete** it.<br>

Use ++w++ to **select** the next frame above.<br>
Use ++s++ to **select** the next frame below.<br>
Use ++shift+w++ to **create** a new frame above.<br>
Use ++shift+s++ to **create** a new frame above.<br>

## Frame Panel

Use frames to create pixel animations.<br>
All pixels should be assigned before you start animating.

<img src="https://files.facepunch.com/ryleigh/1b1911b1/PxcEditor_2019-08-19_15-36-35.png" width="100%"/>

Hold ++"RMB"++ on the panel to be able to **move** it around.<br>
Hold ++"RMB"++ on one of the corners and drag to change the **number of frames** shown.<br>
Hover over the panel and use ++alt+"Scroll Wheel"++ to **resize** it.<br>

Use ++"LMB"++ on a frame to **select** it.<br>
Use ++ctrl+"RMB"++ on a frame to **delete** it.<br>

Use ++a++ to **select** previous frame.<br>
Use ++d++ to **select** next frame.<br>
Use ++shift+a++ to **duplicate** current frame back.<br>
Use ++shift+d++ to **duplicate** current frame forward.<br>
Use ++shift+space++ to create a new **blank** frame.<br>
Use ++shift+delete++ or ++shift+backspace++ to **delete** current frame.<br>

Use ++ctrl+c++ (while no pixels selected) to **copy** current frame.<br>
Use ++ctrl+v++ to **paste** copied frame after selected frame.<br>

Use ++ctrl+alt+"RMB"++ on a frame to **export** it to png file in editor directory.<br>

## Mirroring

All actions taken on the canvas can be mirrored, which is very useful when drawing or animating a unit. The blue lines through the canvas indicate mirroring (red lines if rotational mirroring is turned on).

<img src="https://files.facepunch.com/ryleigh/1b1911b1/PxcEditor_2019-08-19_16-08-57.png" width="100%"/>

Use ++space+a++ or ++space+d++ to toggle horizontal mirroring.<br>
Use ++space+w++ or ++space+s++ to toggle vertical mirroring.<br>
Use ++space+a+w++ or ++space+w+d++, etc to toggle diagonal mirroring.<br>
Use ++space+f++ to switch between mirroring modes.<br>
Use ++space+m++ to toggle all mirroring.<br>

Use ++r++ to toggle rotational mirroring.<br>

Use ++shift+left++ or ++shift+right++ to flip layer horizontally.<br>
Use ++shift+up++ or ++shift+down++ to flip layer vertically.<br>

Use the `CCW` and the `CW` buttons in the toolbar to rotate the canvas counter-clockwise and clockwise, respectively.

## Assigning Pixels

All pixels need a unique id number so that they can be tracked throughout their animations.

<img src="https://files.facepunch.com/ryleigh/1b1911b1/PxcEditor_2019-08-19_16-26-06.png" width="100%"/>

Press ++tab++ to toggle pixel assignment mode.<br>
While in this mode, the editor background color is red.<br>

Use ++ctrl+"RMB"++ with Brush tool to flood-assign hovered area.<br>
Use ++ctrl+"RMB"++ with Eraser tool to flood-unassign hovered area.<br>
Use ++ctrl+f++ to assign all selected un-assigned pixels on current frame (if none are selected, it assigns **all** unassigned pixels).<br>
Use ++del++ to delete all (or selected) assignments on current frame.<br>

You can use ++"LMB"++ on a pixel to assign it (or un-assign it with the Eraser), but generally this is the best workflow:

> 1) Make sure the current frame has no assignments, and contains every pixel in the animation.

> 2) Use ++ctrl+"RMB"++ on each part to flood-assign them.

<img src="https://files.facepunch.com/ryleigh/1b1911b1/PxcEditor_2019-08-19_16-59-45.png" width="80%"/>

> 3) Use ++c+"RMB"++ to highlight all pixels of a certain color, that you want to have special properties<br>
    - then press ++ctrl+f++ to assign them all<br>
    - deselect all pixels before assigning the next pixel type<br>

> 4) Make sure the numbers on the frame match - the left is the amount of pixels, the right is the amount of assigned pixels

<img src="https://files.facepunch.com/ryleigh/1b1911b1/PxcEditor_2019-08-19_17-02-42.png" width="80%"/>

> 5) If the rest of the unassigned pixels are homogenous, use ++ctrl+f++ (while nothing is selected) to assign them all.

## Animation

Generally, you'll want to draw your unit, then assign the pixels, then proceed to animation.

Use ++space++ to start/stop animation playback.<br>

The animation section in the toolbar shows the frame number, followed by the frame's time, followed by the loop mode.<br>
<img src="https://files.facepunch.com/ryleigh/1b1911b1/PxcEditor_2019-08-19_19-21-37.png" />

The frame time is a bit of a relic and you should probably adjust the animation's time in the unit script instead.<br>
The loop mode can be set here or easily overridden in the unit script.<br>

At this point, **do not create any more pixels**, as it'll be too complex to assign them correctly.<br>
The easiest way to animate involves duplicating the current frame and moving around assigned pixels.<br>
More specifically,<br>
> **1)** Set appropriate mirroring.<br>
> **2)** Select the pixels you want to move, set appropriate mirroring, and adjust the pixel positions with mouse or arrow keys.<br>
> **3)** Press ++shift+d++ to duplicate current frame.<br>

## Saving & Loading

Press the `SAV` button in the toolbar to save a json file of your animation.<br>
Press the `LOD` button in the toolbar to open an animation json file.<br>

<img src="https://files.facepunch.com/ryleigh/1b1911b1/PxcEditor_2019-08-19_20-40-20.png" />

## Exporting

When exporting an animation to use in Chippy, there are two parts needed.<br>
The `source` file is a list of all pixels the unit has.<br>
The `anim` files are one or more sequences of source pixels.<br>

Press the `SRC` button in the toolbar to save a source json file.<br>
Press the `ANM` button in the toolbar to save an anim json file.<br>

## Other Features

Use ++ctrl+z++ to undo.<br>
Use ++ctrl+shift+z++ to redo.<br>

In the center of the toolbar:<br>
<img src="https://files.facepunch.com/ryleigh/1b1911b1/PxcEditor_2019-08-19_20-58-55.png" /><br>
You can replace `NAME` with the name of your animation (pointless).<br>
Press the `IMP` button to import a png (this clears and resizes the canvas).<br>
Change the `32` `32` to adjust canvas dimensions (or ++"RMB"++ and drag a canvas panel corner).<br>
Press `NEW` to start a new blank animation.<br>
Press `RST` to reset all panel size and positions (without changing current animation).<br>

On the far right of the toolbar:<br>
<img src="https://files.facepunch.com/ryleigh/1b1911b1/PxcEditor_2019-08-19_20-50-59.png" /><br>
Press ` / ` to toggle diamond-shaped canvas.<br>
Press `FLT` to flatten all layers.<br>
Press ` # ` to toggle grid lines.<br>
Press ` = ` or use ++"Middle Mouse"++ to toggle showing selected pixel ranges.<br>
<img src="https://files.facepunch.com/ryleigh/1b1911b1/PxcEditor_2019-08-19_20-54-40.png" /><br>


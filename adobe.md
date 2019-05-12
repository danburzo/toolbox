# Adobe Stuff

## Photoshop

## Illustrator

### Working with SVG

#### Pasting copied objects as SVG

Illustrator has this neat feature that lets you copy (<kbd>⌘C</kbd>) any object from your design and paste it (<kbd>⌘V</kbd>) as SVG in any text editor. However, configuring _how_ the SVG is generated is a bit obscure:

1. With any Illustrator file, go to <kbd>File → Save As...</kbd> or <kbd>File → Save a Copy...</kbd> and choose <kbd>Format: SVG</kbd>
2. On the next screen, called <kbd>SVG Options</kbd>, you can configure how the SVG will be generated. (Click on <kbd>More Options</kbd> to see all of them). Then, press <kbd>OK</kbd>
3. The options you set on this screen will apply to SVGs you copy to the clipboard from now on

> 💡 You only need to do this once, or whenever you want to change the way the SVG gets generated.

#### Create a rectangle to serve as a viewbox

To create a `viewbox` for the SVG while using the copy/paste trick, you can draw a rectangle behind your artwork to serve this purpose. After pasting the artwork in a text editor, you can just delete the background `<rect>` element.

#### Expand the appearance

TBD.


### Working with Area Type

__Area Type__ is the text area in Illustrator. You can scale the bounding box and the text inside will reflow — as opposed to _point type_, which scales like any other shape. 

#### Switch between Type and Area Type

Double-click on the prong that sticks out of the _right side_ of the box.

#### Auto-fit area to the text content

Double-click on the prong that sticks out of the _bottom side_ of the box to fit the area snugly around the text.

> 💡 Set this behavior as the default by going to <kbd>Illustrator → Preferences… → Type </kbd> and check <kbd>Auto Size New Area Type</kbd>.

#### Resize area type without stretching the text

Selecting a type area and entering a width / height in the Transform pane will stretch the text instead of resizing the text area and reflowing the text. To achieve the latter, use the Direct Selection tool (<kbd>A</kbd>) to select _just the area_ and not the text inside. In this state, using the width / height inputs from the Transform pane will scale the text area without distoring the text. 

> 💡 You can also set the area's size (along with other options) from the <kbd>Type → Area Type Options…</kbd> menu item.

### Convert an illustration from RGB to CMYK

Some tools, such as ArchiCAD, can only produce color PDFs in the RGB color space. To convert that to a CMYK file ready for offset printing:

1. Open the PDF in Illustrator and change its color space to CMYK by using <kbd>File → Document Color Mode → CMYK</kbd>
2. Select all objects (<kbd>⌘A</kbd>) and proceed to <kbd>Edit → Edit Colors → Recolor Artwork…</kbd>
3. In the options dialog:
	1. <kbd>Color Reduction Options…</kbd>, __deselect__ <kbd>Preserve: Black</kbd> to be able to map the rich black to K:100 black;
	2. Switch the color picker to use CMYK sliders;
	3. Select each color in the list, one by one, and ajust it to the preferred CMYK values. You'll mostly want to adjust the blacks and grayscales to only use the K channel.
4. Make sure you overprint blacks to avoid misregistration issues at the offset printer; use <kbd>Edit → Edit Colors → Overprint Black…</kbd> to ensure colors underneath are not knocked out
5. [Use the <kbd>Window → Separations Preview</kbd> panel](https://helpx.adobe.com/illustrator/using/printing-color-separations.html) to make sure the C/M/Y/K plates look as expected.



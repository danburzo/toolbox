# Adobe Stuff

## Illustrator

### Pasting copied objects as SVG

Illustrator has this neat feature that lets you copy (<kbd>⌘C</kbd>) any object from your design and paste them (<kbd>⌘V</kbd>) as SVG in any text editor. However, configuring _how_ the SVG is generated is a bit obscure:

1. With any Illustrator file, go to <kbd>File → Save As...</kbd> or <kbd>File → Save a Copy...</kbd> and choose <kbd>Format: SVG</kbd>
2. On the next screen, called <kbd>SVG Options</kbd>, you can configure how the SVG will be generated. (Click on <kbd>More Options</kbd> to see all of them). Then, press <kbd>OK</kbd>
3. The options you set on that screen will apply to SVGs you copy to the clipboard from now on

You only need to do this once, and whenever you want to change the way the SVG gets generated.

### Working with Area Type

__Area Type__ is the text area in Illustrator. You can scale it and the text inside will reflow. (As opposed to normal type, which gets resized like a normal shape). 

#### Switch between Type and Area Type

Double-click on the thing that sticks out of the right side of the box.

#### Auto-fit text

Double-click on the pointy thing that sticks out of the bottom side of the box. 

__Tip:__ Enable this by default by going to <kbd>Illustrator → Preferences… → Type </kbd> and check <kbd>Auto Size New Area Type</kbd>

#### Resize area type without stretching the text

For some reason, entering a width / height in the Transform pane will stretch the text instead of resizing the text area. (Hopefully this will change soon). In the meantime, if you want to size your text areas with precisions, go to <kbd>Type → Area Type Options…</kbd> and use the _width_ and _height_ controls from there.

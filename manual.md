# REXPaint v1.50 - Manual <!-- omit in toc -->

A powerful and user-friendly ASCII art editor.

## Background <!-- omit in toc -->

There are a number of ASCII art editors available on the web, but most suffer from poor usability or small feature sets (one notable exception being Eigenbom's awesome fork of ASCII Paint). For development of my own projects, I needed an application equipped with a wide range of tools for quickly drawing and manipulating ASCII art, as well as the ability to easily browse the images created as stored in their native format. Thus REXPaint was born.

Over the years since its first public release, REXPaint has found use as a general purpose ASCII art editor, as well as a roguelike development tool for mockups, mapping, and design. I love seeing what people create with this program, so send me a link/copy if you've made something cool! (Or share it with us on the [forums](www.gridsagegames.com/forums/index.php?board=8.0))

## Features <!-- omit in toc -->

An overview of REXPaint's major features:

* Edit characters, foreground, and background colors separately
* Draw shapes and text
* Copy/cut/paste areas
* Undo/redo changes
* Preview effects simply by hovering the cursor over the canvas
* Palette manipulation
* Image-wide color tweaking and palette swaps
* True-color RGB/HSV color picker
* Create multi-layered images
* Zooming: Scale an image by changing font size on the fly
* Custom fonts and support for extended characters and tilesets
* Browse art assets and begin editing at the press of a button
* Images highly compressed
* Export `.png` for use in other programs or on the web
* Export `.ans` files for ANSI art
* Other exportable formats: `.txt`, `.csv`, `.xml`, `.xpm`, `BBCode`, `C:DDA`
* Import `.txt` files
* Skinnable interface

## Table of Contents

* [Table of Contents](#table-of-contents)
* [Canvas](#canvas)
  * [Resizing](#resizing)
  * [Shifting](#shifting)
* [Drawing](#drawing)
  * [Apply](#apply)
  * [Draw Modes](#draw-modes)
  * [Preview](#preview)
  * [Undo](#undo)
* [Fonts](#fonts)
  * [Glyphs](#glyphs)
  * [Glyph Swapping](#glyph-swapping)
* [Palette](#palette)
  * [Selection & Editing](#selection--editing)
  * [Color Picker](#color-picker)
  * [Palette Files](#palette-files)
  * [Extraction](#extraction)
  * [Adding](#adding)
  * [Organization](#organization)
  * [Palette Swapping](#palette-swapping)
  * [Color Shifting](#color-shifting)
  * [Transparency](#transparency)
* [Layers](#layers)
  * [Control](#control)
  * [Active Layer](#active-layer)
  * [Order](#order)
  * [Visibility & Locking](#visibility--locking)
  * [Merging](#merging)
  * [Multi-layer Editing](#multi-layer-editing)
  * [Extended Layers Mode](#extended-layers-mode)
* [Browsing](#browsing)
  * [File/Image Control](#fileimage-control)
  * [Viewing & Editing](#viewing--editing)
  * [Saving](#saving)
  * [Exporting](#exporting)
* [Customization](#customization)
  * [Options](#options)
  * [Skins](#skins)
  * [Additional Resources](#additional-resources)
* [Commands](#commands)
  * [Font](#font)
  * [Palette](#palette-1)
  * [Drawing](#drawing-1)
  * [Text Tool](#text-tool)
  * [Apply](#apply-1)
  * [Canvas](#canvas-1)
  * [Layers](#layers-1)
  * [Info](#info)
  * [Color Picker](#color-picker-1)
  * [Browse](#browse)
  * [Image](#image)
  * [Resize](#resize)
  * [General](#general)
* [Appendix A: Known Issues](#appendix-a-known-issues)
* [Appendix B: `.xp` Format Specification (and Import Libraries)](#appendix-b-xp-format-specification-and-import-libraries)
* [Appendix C: External Libraries and Tools](#appendix-c-external-libraries-and-tools)
* [Appendix D: ANSI Art `.ans`](#appendix-d-ansi-art-ans)
* [Appendix E: Exportable Text Formats (`.txt`, `.csv`, `.xml`, `BBCode`)](#appendix-e-exportable-text-formats-txt-csv-xml-bbcode)
  * [`.csv`](#csv)
  * [`.xml`](#xml)
  * [`BBCode`](#bbcode)
* [Appendix F: Importing Text Files](#appendix-f-importing-text-files)
* [Appendix G: Importing `.png`s](#appendix-g-importing-pngs)
* [Appendix H: Batch Exporting `.png`s](#appendix-h-batch-exporting-pngs)
* [Appendix I: Exporting ANSI art for C:DDA](#appendix-i-exporting-ansi-art-for-cdda)

## Canvas

The black area to the right of the tool menus is the *canvas view* where all image editing occurs, and the image itself initially appears as a box outline that defaults to the size of the entire canvas view.

### Resizing

Resize the image as necessary `Ctrl-r`, ideally before starting to draw so that later changes are not affected by a change in image dimensions. Resizing can be done at any time, but the dimensions are always based from the top-left corner of an image, so make sure the portion of a larger image you wish to retain is based in the top-left corner before shrinking it (move the relevant section with the copy tool).

### Shifting

To view different parts of a large image (or reposition a smaller one), hold `space` while left-clicking on the image and moving the mouse to drag it (Photoshop style). The numpad can also be used for eight-directional shifting of the image, `Enter` resets its location, and `Ctrl-Enter` centers it.

## Drawing

### Apply

The *apply menu* determines what is actually produced by the current draw mode when you left-click on the image.\
Glyphs (characters), foreground color, and background color are each drawn/edited separately, and can be individually toggled on and off via the menu buttons or `g`, `f`, and `b`. Thus if you activate "glyph" and deactivate "fore" and "back," when you draw only the current glyph will be applied, while the image's colors remain unchanged. Activating all modes will overwrite the glyph and both foreground and background colors when drawing. (Turning all apply modes off would draw... nothing, and be completely pointless!)

---
The colors to be applied are shown to the right of their button, and the current glyph is that highlighted/chosen among the characters in the font box. Change the glyph by left-clicking on a different one in the font box, and change the colors by either left-clicking on the color square (see Color Picker explanation further below) or choosing a color from the palette (`LMB` choses a color for the foreground, `RMB` for the background).

---

### Draw Modes

*Drawing modes* define the shape and area of the image affected while drawing. Only one mode can be active at a time, and some modes have an alternate setting that changes their behavior (left-click on the active mode to toggle its secondary feature, or cycle through them if more than one).

* **Cell** `c`\
  Applies the effect to a single "cell" `space` on the image. Hold `LMB` and move the cursor to keep drawing. Alternate mode: Auto-wall/auto-box drawing. While the current glyph is any of the single or double line characters (but not a single-double intersection), drawn lines and all adjacent lines of the same type (single/double) will be automatically reoriented to connect with one another. This is useful for creating map walls or boxes. Has no effect for other (non-line) glyphs, which will be drawn normally.
* **Line** `l`\
  Applies the effect to a line. Left-click at the line's start and release the button at its end, or press `RMB`/`Esc` before releasing the button to cancel the line.
* **Rect** `r`\
  Applies the effect to a rectangular area. Left-click at one corner of the rectangle and release the button at the opposite corner, or press `RMB`/`Esc` before releasing the button to cancel the rectangle. Alternate mode: Fills the entire rectangle instead of drawing an outline. Non-filled rects drawn with any line glyph will automatically create a properly oriented ASCII box.
* **Oval** `o`\
  Like rect mode, but draws ovals. Alternate mode fills the oval. By default ovals are centered on the point chosen; to instead draw from any corner switch the oval drawing method via `Alt-o`.
* **Fill** `i`\
  Applies the effect to all like cells attached to the one under the cursor. When comparing cells, fill mode only checks the attributes for which the apply mode is currently active. For example, if foreground color is the only active apply mode then fill mode propagates to all those attached cells with the same foreground color, regardless of their glyph or background color. Alternate Mode: Fill search is performed in 8 directions rather than 4, allowing the fill to travel along diagonals through obstacles.
* **Text** `t`\
  Types text onto the image. See the Text Input section below for a list of valid commands.
* **Copy** `Ctrl-c`\
  Copies a rectangular area of the image into the clipboard for later pasting. Always copies all attributes (glyph and colors) of the regardless of current apply settings. Alternate mode:
* **Cut** `Ctrl-x`\
  Cut mode erases everything in a certain area after storing it to the clipboard. Note that if the Paste tool is in an _alternate mode_, any copy actions also automatically mirror the copied contents to match that mode.
* **Paste** `Ctrl-v`\
  Paste the clipboard contents to the image. While the copy/cut command stores all glyph and color information, only those attributes for which the apply mode is currently active will by pasted.\
  _Alternate modes_: Flip clipboard contents horizontally, vertically, or both (by default this also automatically converts any non-symmetrical glyphs with mirror images; to flip by position only and leave glyphs unchanged set `Paste-flip ASCII` to `No` in the options menu).

### Preview

While the cursor is hovering over the image, applicable draw modes (cell, fill, paste) will show a preview of what the image will look like assuming a left-click at that location. Remember this is true even for fill mode, which may cause the image to appear quite different, but is great for quickly visualizing changes without having to do a lot of applying and undo-ing. To temporarily hide the preview and see the image as it is, hold `Shift` or `Alt`.

### Undo

All image manipulation actions can be undone/redone (`Ctrl-z`/`Ctrl-y`, or just `z`/`y`). Undo histories are also saved separately for each image, thus you can freely switch between images in the browser and still come back to undo changes from a previous image. (Closing the program, however, will forget all undo states!)

## Fonts

Images themselves do not store font information, instead remembering only what glyph/character index belongs at each position. This means you can dynamically change the size and/or appearance of an image by simply switching the font (`Ctrl-PgUp`/`PgDn` or `<`/`>`).

---
By default, both the GUI and images use a standard 256-character Code Page 437 font. REXPaint makes this same font available at several sizes (and changes #254 and #255 to radio boxes). You can edit these fonts (in the `data/fonts/` directory), and/or add new ones by creating a new `.png` bitmap and listing it in the `data/fonts/_config.xt` text file. Fonts do not require square glyphs (rectangles are okay), but both the GUI and Art font must use the same glyph dimensions.\
When creating a custom font you could even replace some or all of the glyphs/characters/symbols, though you should leave the GUI font unchanged so the interface appears as expected (notice how `_config.xt` defines the GUI and art fonts separately—they do not have to use the same font!). Note that custom fonts always treat index 32 as a space, regardless of what the font bitmap contains there.\
Although the default number of rows in a font bitmap is 16, and that is the largest number REXPaint will display at once, fonts with additional rows are supported, essentially allowing space for an "unlimited" number of glyphs in an image. Simply specify the proper number of rows available for the relevant art font in `_config.xt` and it will be loaded normally (16 columns is still a requirement), then you can use `PgUp`/`PgDn` or `Wheel` (with cursor in the glyph area) to see and use glyphs beyond #255. The mouse scrolling rate can be adjusted in `REXPaint.cfg` via `glyphScrollRowCount`. If any art fonts have more than 16 rows, the font window will display numbers at the top right indicating the number of rows currently above and below the current view. To make it easier to use large tilesets, by default right-clicking on an image glyph to select a glyph currently outside the viewable glyph window does not automatically scroll the view to show it unless you right-click on the same selected glyph a second time, though you can overide this behavior and have it always scroll immediately by setting `glyphSelectAlwaysAutoscrolls` in `REXPaint.cfg`.\
One supported feature not used by the included fonts is alpha transparency. Font bitmaps are drawn as white on black, but know that using shades of gray will cause the foreground color to be semi-transparent to a degree equal to the shade of gray (e.g., pixels drawn using 128,128,128 gray will appear as 50% transparent). Also, even though they may only use two colors, bitmaps must be saved as 32-bit pngs (using 8-bit pngs will crash REXPaint). The font bitmap can use any background color, where REXPaint will automatically detect it by checking the upper leftmost pixel (at 0,0). By extension, if the character at the first position wants to use that pixel, REXPaint will not be able to automagically detect the background color; in this situation, you can override the background color key with a specific RGB color in `REXPaint.cfg` via `fontKeyColorOverride`.

---

### Glyphs

Select a glyph to draw with by clicking on it in the font window. Once you have a partially-drawn image the fastest way to load a previously used glyph, including even its foreground/background colors, is to simply right-click on it in the image.

For reference you can toggle highlighting of all used glyphs by pressing `u` (the highlights are updated only every five seconds, and will be slow in the case of massive images since the entire image must be searched for matches—not recommended to leave this mode on when editing especially large images). To see where a specific glyph has been used in the image's currently active layer, hold `Alt` while hovering the cursor over it in the font window.

### Glyph Swapping

To replace every occurrence of a glyph in all visible unlocked layers of an image, `Shift-LMB` on it in the font window, then `Shift-LMB` on the new glyph to replace it with. After selecting a source glyph, the swap can be cancelled by again pressing `Shift-LMB` on the same glyph.

## Palette

*Palettes* in REXPaint are tools intended purely for color selection and organization, thus images themselves do not store palettes (i.e., image colors are not "indexed") and you can edit images without ever touching the palette. That said, palettes provide a convenient way to unify/standardize colors across multiple images, along with a variety of other color manipulation features.

### Selection & Editing

Left-clicking on a palette color (including an "empty" space, which is actually black) will select it as the foreground color; right-clicking selects it as the background color. Clicking on the same color again will allow you to edit it in the color picker (see below). `Shift`-clicking will also open the color picker, but once the new color is confirmed will also replace all matching colors in the image (applied to foreground and/or background, depending on which apply modes are active at the time, NOT whether `LMB`/`RMB` used).

---
To see where a specific color has been used in the image's currently active layer, hold `Alt` while hovering the cursor over it in the palette window.

---

### Color Picker

The color picker is fairly straightforward—its features and layout are taken from Photoshop for those familiar with it. Left-click on a color to select it (you can also hold `LMB` and move the cursor to watch the new color and its values change), and click on it again to accept it (or press the `OK` button or `Enter`). Alternatively, choose a precise color by specifying HSV/RGB number values (click on the number, or press `h`/`s`/`v`/`r`/`g`/`b` for faster entry).

---
By default the slider will be in hue mode, but you can set it to saturation or brightness mode by left-clicking on the corresponding box seen next to the S/V values.

---

### Palette Files

Any number of palettes can be created by clicking on the `+` button (switch between them with the buttons or `[`/`]` keys). New palettes are unnamed until saved (click on the `S`), when they are stored in a text format in the `data/palettes/` directory. The files can be modified in any text editor (turn off line wrapping), though editing is generally most conveniently handled directly in the editor itself. Knowing where the palettes are stored can be useful for making copies or saving them to another location for safe-keeping. (You can also rename them, as the file name is the name displayed in REXPaint.)

---
Remember to save a palette again after making any changes you want to keep (palettes are not automatically saved). Palette changes are NOT recorded as part of the undo history, so changes are permanent unless you previously saved a copy of the palette file.\
Colors can of course be edited directly in the palette file, using and of the four color formats described in the `skins.xt` file: named colors, RGB, HSV, or HEX (individual colors can even used different formats).

---

### Extraction

Pressing `Ctrl-Shift-e` will create a new empty palette, then add to it all unique foreground and background colors found in the current image.

### Adding

Right-clicking on the foreground or background color shown in the apply menu will add it to the palette at the first empty (black) space found, if available. This can be useful when colors were created using the color picker through the apply menu before later deciding to add them to the palette.

### Organization

There are several commands that enable you to manipulate the palette itself for organizational purposes:

* **Organize** `Ctrl-Shit-o`\
  Rearranges the palette colors by moving them into hue-major order. It doesn't always look perfect, but it's better than nothing if you have a horribly messy palette (and is a good place to start from when manually organizing such a palette).
* **Purge** `Ctrl-Shift-p`\
  Removes from the palette all colors not found in the current image.
* **Manual relocation** `Ctrl-LMB`\
  Control-click on two different palette positions to swap those two colors. As empty palette positions are actually black, you can safely "move" colors to these empty positions as well.
* **Duplicate** `CMB`\
  Click on a source color, then on a target position (may be in the same or a different palette) to copy the source color. Useful for more quickly creating different variations/shades of a color when building a palette.

### Palette Swapping

You can mimic a "palette swap" in the traditional sense by opening the target image and source palette and pressing `Ctrl-Shift-w`, then opening the target palette and pressing `Ctrl-w`. This will change all colors found in both the image and source palette to those colors found at the same position in the target palette. After setting the source palette you can apply the target palette to any number of other images.

---
To swap all instances of a single color throughout an image (foreground and background, all layers) with another in the same palette, `Shift-LMB` on the first color and then `Shift-LMB` on the color you want to change it too.

---

### Color Shifting

Having a properly set up palette (ideally with shades of colors listed by row) also enables you to easily shift individual colors directly on an image to quickly get/test the right color/shade without manually selecting them in the palette every time. Hold `Shift` and use the left and right mouse buttons on the image to shift the foreground color based on its position in the palette (black and white palette positions are skipped); use `Alt` instead for background color. This only works for colors found in the current palette.

---
Alternatively, press `Shift-h`/`s`/`v` to activate the respective HSV shifting mode, in which using the left/right mouse buttons and `Shift`/`Alt` as indicated above will instead tweak that characteristic of the target cell's foreground/background, completely ignoring palette colors. Return to palette-based shifting mode by toggling the current HSV shifting mode again.

---

### Transparency

You'll notice the default palette appears to have a missing color, as does the color picker's hue slider. The color is actually there, but it's a background color set to 255,0,255 (hot pink) which REXPaint uses to identify transparent cells. This means two things:

1. It is impossible to use 255,0,255 as a background color in an image (as a foreground color it's okay)
2. You can create multi-layered images where upper layers contain transparent sections through which lower layers are visible.

Draw using the transparent background color to create a transparent cell/area, but know that the glyph and foreground must not be applied (deactivate them) because a transparent background will be automatically converted to black in order to make sure the foreground is visible in that case.

## Layers

Use of layers is completely optional, and a majority of users will probably do just fine with the single layer automatically created for an image. Layer functionality exists mostly for the workflow/editing benefits of keeping different components of an image on separate layers, or perhaps having alternate versions of a certain part of the image. Other advantages are limited since layers cannot currently be blended.

### Control

Each image automatically comes with one base layer (required). More can be created with `Ctrl-l` or by clicking on the layer window's `+` button. A single image can have up to nine separate layers, and all newly created layers are automatically filled with transparent cells (255,0,255). Press the `X` button to delete a layer (deletion is not possible if there is only one layer remaining).

### Active Layer

The *active layer* is the one which effects are applied to when drawing to the image—its number will appear highlighted. Change the active layer by clicking on a different number, pressing `1`~`9`, or using the mouse wheel while the cursor is over the canvas area.

### Order

Layers are listed in top to bottom order, and their order determines which are drawn on top, so opaque parts of higher layers will obscure those portions of lower layers. The relative order of layers can be changed by clicking on the arrow buttons.

### Visibility & Locking

Individual layers can be hidden from view, but the active layer must always be visible. (To hide the active layer, select a different layer first.) Note that while hidden layers are always saved as normal with the image data, they are NOT drawn when the image is exported, so make sure the image appears as intended before exporting.

---
Any layer can be locked (`Shift-#` or the `Lck` button), which prevents editing it even by accident.

---

### Merging

Use the `Ctrl-Shift-m` command to merge the active layer downward, permanently combining it with the one below. Only the base layer cannot be merged (as there is nothing under it). This action is irreversible, so use it carefully.

### Multi-layer Editing

The copy/cut/paste tools in particular can work across multiple layers at once, simultaneously copying the same area from more than one layer. To get this effect, use `d` to increment the amount of _depth_ you want to manipulate. While the depth is greater than 1, additional layers below the current active layer will be included in each operation. For example, using a depth of 2 to copy an area from layer 4 will add that area from both layer 4 and 3 to the clipboard, and maintaining the same depth value while pasting to layer 2 will paste the layer 4 contents on layer 2, and layer 3 contents on layer 1.

---
Nothing will copy from intermediary hidden layers, and nothing can be cut from locked layers (though the copy portion of a cut operation will still work on that layer). Nothing will paste into intermediary hidden or locked layers, either.\
`Shift-d` decrements the depth counter.

---

### Extended Layers Mode

While a single image may include up to nine layers, normally only the lowest four of those will be listed in the Layers window. To view more than that, click the `E` button or press `Ctrl-Shift-l` to toggle *Extended Layers Mode*, which will cover the Info window but allow as many as nine layers to be listed at once. If you're using hotkeys for layer control, those will still work as usual even if those layers are not currently visible in the list.

---
An `*` appears at the top right of the Layers window if an image contains more layers than currently listed, or it will instead show the layer number if a non-listed layer is currently active.\
Note that while Extended Layers Mode is active, the options and help menus are inaccessible, as they are normally opened via the Info window, which will be covered.

---

## Browsing

Switch between *paint mode* and *browse mode* by clicking on the buttons at the top of the menu area or with `tab`. Browse mode allows you to view all the images created by REXPaint as found in the `images/` directory and any of its subdirectories (use Windows to add any subdirectories you need for organizational purposes, though note that file tree branches will be ignored beyond/deeper than four levels).

### File/Image Control

You'll notice there is always one unnamed image created on startup; you don't have to modify or save it unless you want to. Additional new/empty images can be created by pressing `Ctrl-n` or through the `New` button in paint mode—these are added to the base path (`images/` by default). To create an empty image in a specific subdirectory, simply left-click the directory name.

---
Realize that browse mode is mostly an image browser, not a full-featured file manager, so actions like image moving, directory operations, etc. should be performed through Windows. You can, however, rename `RMB`, duplicate `Shift-LMB` and delete `Ctrl-Shift-Alt-LMB` images from here. Image deletion is permanent, so be careful with it!\
Feel free to create additional subdirectories under REXPaint's `images/` directory, as those will also be shown in the browser, and may be collapsed/expanded as well.\
While REXPaint is open, you can reload all image files to reflect changes at the file system level via `Ctrl-Shift-r` or the `R` button at the bottom of the browser. Of course you'll lose any unsaved images or progress, but you'll be warned if that will happen. Once complete, the reloading process will do its best to restore the original browsing state and selected image.

---

### Viewing & Editing

Images do not need to be explicitly opened in REXPaint. When the program starts, all images are loaded into memory and you can browse through them by clicking on their name in the browser or pressing `⇑`/`⇓` (see [**Commands**](#commands) for more list controls), then edit any of them immediately by switching over to paint mode. Copy-paste also works normally between different images (i.e. you can copy from one image to another).

### Saving

When changes are made to an image, an indicator will appear next to its name in the browser, as well as in the top-left corner of the paint mode window. The browser menu also shows the total number of unsaved images to the top left. Save the image to remove the indicator. Saving can be done from either browse or paint mode with `Ctrl-s` or the `Save` button.

### Exporting

Unless you're drawing art for my game you'll probably want to use your image elsewhere, and REXPaint's compressed `.xp` format won't be very useful. Use the Export button (or `Ctrl-e`) to save the current image as a `.png` file (can be done from either *paint* or *browse* mode). By default, the new file can be found in the `images/` directory.

---
When exporting, remember that

1. font size matters
2. hidden layers are not exported

Essentially, the image will be exported exactly as you see it (minus any draw preview seen when the cursor is hovering over the image).\
Exporting to `.ans` is also possible (see [**Appendix D**](#appendix-d-ansi-art-ans)).\
Export as an `.xpm` image (X PixMap) by pressing `Ctrl-p` (see <http://en.wikipedia.org/wiki/X_PixMap>).\
Other exportable formats include `.txt` `Ctrl-t`, `.csv` `Ctrl-k`, `.xml` `Ctrl-m`, and `BBCode` `Ctrl-b` (see [**Appendix E**](#appendix-e-exportable-text-formats-txt-csv-xml-bbcode)).

---

## Customization

### Options

The first time REXPaint is run, it will create a new `REXPaint.cfg` file using the default options. It's generally not necessary to edit this file directly, as options may be modified through an in-program options menu `F3`, and all changes are saved when the program is closed. Delete the file while REXPaint is not running to have it reset all values to defaults when next started.

There are currently several options not mentioned elsewhere in the manual, implemented by request, which require editing `REXPaint.cfg` to take advantage of:

* `unlimitedFontSize`: Setting this value to 1 loads all fonts, even those which will allow extreme zooming where it produces a window which doesn't fit on the screen! This is far from ideal usage of REXPaint, but may be helpful in special circumstances.
* `txtOutputUTF8`: Whether the `TXT` export should use UTF8 encoding instead of pure ASCII characters. The former uses unicode hard spaces, which you may not want depending on your use case.
* `baseImagePath`: Set to the base path from which to load images into the browser, relative to the `.exe` location. As a relative path it can use `../` to move to higher directories.
* `exportsToBase`: Whether exported files are always placed in the base image path, rather than to the same path as their source image which may be in a subdirectory.
* `ignorePath`: Use this to specify one or more paths (relative to the `baseImagePath`) which will be ignored by the image loader so that even those directories (and all subdirectories and their contents) will not appear in the file browser. You can list as many separate paths as you like by using `ignorePath` on a separate line for each.

### Skins

REXPaint comes with several different skins; press `F4` to cycle through them. You can edit them, or add more, by setting the colors in `data/skins.xt` (open as a text file).

### Additional Resources

See the [online resource repository](http://www.gridsagegames.com/rexpaint/resources.html) for additional user-submitted resources like fonts and palettes, and feel free to send in your own if you feel you've created something that would benefit the community. There you'll also find palettes and fonts for a large number of legacy systems like the Apple II, Atari 2600, Commodore 64, NES, ZX Spectrum, and many more.

A guide to using REXPaint for mockups, art, prefabs and more, with specific techniques and plenty of reference images, can be found [here](http://www.gridsagegames.com/blog/2015/07/roguelike-development-rexpaint/)

Developers see [**Appendix C**](#appendix-c-external-libraries-and-tools) for links to existing libraries and tools capable of interfacing with REXPaint files.

## Commands

Many commands that are either obvious or too advanced are not listed in REXPaint's `F1`/`?` help screen. Below is a complete list of all currently supported commands (advanced commands are explained in the relevant section of the manual above):

### Font

| key                          | function \[subfunction\]                                     |
| ---------------------------- | ------------------------------------------------------------ |
| `Ctrl-PgUp`/`PgDn` / `<`/`>` | change font (scale image/UI)                                 |
| `Ctrl-Wheel`                 | change font (scale image/UI)                                 |
| `LMB`                        | select glyph                                                 |
| `⇑`/`⇓`/`⇐`/`⇒`              | shift selection                                              |
| `Wheel` / `PgUp`/`PgDn`      | scroll view to extended glyphs (if present)                  |
| `Home`/`End`                 | scroll view to first/last extended glyph page (if present)   |
| `u`                          | toggle **u**sed glyph highlighting (slow for massive images) |
| `Alt` (hold)                 | highlight hovered glyph in current layer                     |
| `Shift-LMB` x2               | swap occurrences of *glyph 1* with *glyph 2*                 |

### Palette

| key            | function \[subfunction\]                     |
| -------------- | -------------------------------------------- |
| `[`/`]`        | change palette                               |
| `LMB` \[x2\]   | set \[edit\] foreground color                |
| `RMB` \[x2\]   | set \[edit\] background color                |
| `Shift-LMB` x2 | swap occurrences of *color 1* with *color 2* |
| `Alt-LMB` x2   | edit and replace foreground color in image   |
| `Alt-RMB` x2   | edit and replace background color in image   |
| `Ctrl-Shift-o` | **o**rganize palette                         |
| `Ctrl-Shift-e` | **e**xtract image palette                    |
| `Ctrl-Shift-p` | **p**urge unused colors                      |
| `Ctrl-LMB` x2  | swap palette colors (*source*->*target*)     |
| `Ctrl-Shift-w` | set palette s**w**ap source                  |
| `Ctrl-w`       | s**w**ap image palette                       |
| `CMB`          | set color copy source/target                 |
| `Alt` (hold)   | highlight hovered color in current layer     |

### Drawing

| key             | function \[subfunction\]                       |
| --------------- | ---------------------------------------------- |
| `c` \[x2\]      | **c**ell \[auto-walls\]                        |
| `l`             | **l**ine                                       |
| `r` \[x2\]      | **r**ectangle \[filled\]                       |
| `o` \[x2\]      | **o**val \[filled\]                            |
| `Alt-o`         | toggle **o**val drawing method (center/corner) |
| `i` \[x2\]      | f**i**ll \[8-direction\]                       |
| `t`             | **t**ext                                       |
| `Ctrl-c`        | copy                                           |
| `Ctrl-x`        | cut                                            |
| `Ctrl-v` \[x2\] | paste \[flip\]                                 |
| `Esc` / `RMB`   | stop/cancel                                    |

### Text Tool

| key              | function \[subfunction\]                                                 |
| ---------------- | ------------------------------------------------------------------------ |
| `Enter`          | confirm                                                                  |
| `Ctrl-Enter`     | confirm current text and start new line directly below it                |
| `Esc`            | cancel                                                                   |
| `⇐`/`⇒`          | move caret left/right (insert characters anywhere in text)               |
| `Ctrl-⇐`/`⇒`     | move caret to beginning/end of text                                      |
| `Home`/`End`     | move caret to beginning/end of text                                      |
| `Backspace`      | delete character before caret                                            |
| `Ctrl-Backspace` | delete all text before before caret                                      |
| `Delete`         | delete character at caret position                                       |
| `Ctrl-Delete`    | delete all text from caret to the end                                    |
| `⇑`/`⇓`          | cycle through text history (previously confirmed text) for reuse/editing |

### Apply

| key                        | function \[subfunction\]                                |
| -------------------------- | ------------------------------------------------------- |
| `g` \[`G`\]                | toggle \[solo\] **g**lyph                               |
| `f` \[`F`\]                | toggle \[solo\] **f**oreground color                    |
| `b` \[`B`\]                | toggle \[solo\] **b**ackground color                    |
| `LMB`                      | edit color                                              |
| `RMB`                      | add color to palette                                    |
| `Alt-w`                    | s**w**ap foreground/background colors                   |
| `Shift-Alt-r`/`g`/`b`      | toggle foreground color channel application (all tools) |
| `Ctrl-Shift-Alt-r`/`g`/`b` | toggle background color channel application (all tools) |
| `d`/`shift-d`              | increment/decrement copy\cut\paste layer **d**epth      |

### Canvas

| key                       | function \[subfunction\]                                                                  |
| ------------------------- | ----------------------------------------------------------------------------------------- |
| `Space` (hold)            | enter drag mode                                                                           |
| `LMB`                     | hold canvas to drag                                                                       |
| numpad                    | shift canvas                                                                              |
| `Shift-Wheel`             | scroll image up/down                                                                      |
| `Enter`                   | reset image location                                                                      |
| `Ctrl-Enter`              | center image                                                                              |
| `RMB`                     | copy cell contents (applied modes only), where source is current layer                    |
| `Ctrl-RMB`                | as `RMB`, but from uppermost visible layer (useful for reference layers)                  |
| `Shift`/`Alt` (hold)      | hide preview                                                                              |
| `Shift-arrow`/numpad      | shift all layers in indicated direction (wraps)                                           |
| `Shift-Ctrl-arrow`/numpad | shift active layer in indicated direction (wraps)                                         |
| `n`                       | toggle explicit transparency mode                                                         |
| `Shift-Alt-n`             | toggle explicit transparency color set                                                    |
| `Shift-h`/`s`/`v`         | switch color shift mode (repeat same to restore to *palette* mode)                        |
| `Shift-LMB`/`RMB`         | apply color shift to foreground (`Prev`/`Next` or `⇓`/`⇑`, whichever appropriate)         |
| `Alt-LMB`/`RMB`           | apply color shift to background (`Prev`/`Next` or `⇓`/`⇑`, whichever appropriate)         |
| `Shift-Alt-w`             | s**w**ap foreground/background colors throughout active layer                             |
| `Ctrl-Shift-Alt-w`        | s**w**ap foreground/background colors throughout image                                    |
| `Ctrl-Shift-c`            | copy entire active layer (to clipboard) (does multi-layer copy if selected depth > 1)     |
| `z`/`Ctrl-z`              | undo                                                                                      |
| `y`/`Ctrl-y`              | redo                                                                                      |
| `Ctrl-d`                  | toggle rect dimension **d**isplay (for drawing/selecting a rectangle; also `RDim` button) |
| `Ctrl-g`                  | toggle **g**rid                                                                           |
| `Alt-Wheel`               | change grid resolution                                                                    |
| `Alt-g`                   | toggle **g**rid under mode (show in undrawn areas only)                                   |
| `Ctrl-Tab`                | switch between current/latest image                                                       |
| `Ctrl-⇑`/`⇓`              | edit previous/next image (even in paint mode)                                             |

### Layers

| key            | function \[subfunction\]    |
| -------------- | --------------------------- |
| `Ctrl-l`       | new **l**ayer               |
| `Wheel`        | cycle active layer          |
| `1`~`9`        | activate layer              |
| `Ctrl-1`~`9`   | toggle layer hide           |
| `Shift-1`~`9`  | toggle layer lock           |
| `Ctrl-Shift-m` | **m**erge active layer      |
| `Ctrl-Shift-l` | toggle extended layers mode |

### Info

| key | function \[subfunction\] |
| --- | ------------------------ |
| `q` | toggle RGB/HSV mode      |

### Color Picker

| key          | function \[subfunction\] |
| ------------ | ------------------------ |
| `h`/`s`/`v`  | edit value               |
| `r`/`g`/`b`  | edit value               |
| `#` or `x`   | edit hex                 |
| `LMB` \[x2\] | set \[accept\] color     |
| `Enter`      | accept new color         |
| `Esc`        | cancel                   |

### Browse

| key                     | function \[subfunction\]        |
| ----------------------- | ------------------------------- |
| `Wheel` / `PgUp`/`PgDn` | scroll list                     |
| `LMB`                   | view image                      |
| `⇑`/`⇓` / `Shift-Wheel` | view previous/next image        |
| `RMB`                   | rename image                    |
| `F2`                    | rename currently selected image |
| `Shift-LMB`             | duplicate image                 |
| `Ctrl-Shift-Alt-LMB`    | delete image (permanent!)       |
| `Ctrl-Shift-r`          | reload all image files          |
| `Ctrl-⇑`/`⇓` / `L`/`R`  | previous/next directory         |
| `Home`/`End`            | first/last image                |
| `LMB` (folder)          | collapse/expand folder          |
| `Shift-LMB` (folder)    | create new image in folder      |
| `Shift-RMB` (folder)    | export all images as pngs       |
| `Ctrl-⇐`/`⇒`            | collapse/expand all folders     |

### Image

| key      | function \[subfunction\]                                                         |
| -------- | -------------------------------------------------------------------------------- |
| `Ctrl-n` | **n**ew (in base path)                                                           |
| `Ctrl-r` | **r**esize                                                                       |
| `Ctrl-s` | **s**ave                                                                         |
| `Ctrl-e` | **e**xport png                                                                   |
| `Ctrl-t` | export `.txt` (ascii only, no color)                                             |
| `Ctrl-k` | export `.csv`                                                                    |
| `Ctrl-a` | export `.ans` (has restrictions, see [**Appendix D**](#appendix-d-ansi-art-ans)) |
| `Ctrl-m` | export `.xml`                                                                    |
| `Ctrl-p` | export `.xpm`                                                                    |
| `Ctrl-b` | export `BBCode` (ascii w/fgd color, no bkg)                                      |
| Ctrl-j   | export `C:DDA` ([see **Appendix I**](#appendix-i-exporting-ansi-art-for-cdda))   |

### Resize

| key             | function \[subfunction\] |
| --------------- | ------------------------ |
| `LMB` / `w`/`h` | width/height             |
| `Enter`         | accept                   |
| `Esc`           | cancel                   |

### General

| key         | function \[subfunction\] |
| ----------- | ------------------------ |
| `Tab`       | toggle paint/browse      |
| `F1` / `?`  | commands                 |
| `F3`        | options                  |
| `F4`        | change skin              |
| `F5`        | toggle fps               |
| `Ctrl-F5`   | uncap fps                |
| `PrtScn`    | screenshot               |
| `Alt-F4`    | exit                     |
| `Alt-Enter` | fullscreen               |

## Appendix A: Known Issues

1. Capslock has no affect on text entry. This is because the library is unable to detect key state changes outside the program itself, which would lead to confusion when the capslock effect is out of sync with the key state, thus capslock support was removed completely.
2. Any font change commands (`Shift-<`/`>` and `Ctrl-PgUp`/`PgDn`) cannot be repeated without releasing the `Shift`/`Ctrl` key. This is due to an underlying library limitation on command processing when changing the video mode, and workarounds would have other undesirable side effects.
3. When exporting to `.png` or taking a screenshot of the application, all foreground colors drawn on non-black background colors will have one or more of their RGB component values shifted by a tiny amount dependent on the background color (never by more than a value of 1, however). This issue is due to how the potential for alpha transparency of foreground colors is handled internally by the library, and cannot be corrected for at this time.
4. If you run REXPaint off a thumb drive, **do not** remove the drive while the program is running, as file operations will seem to continue working when they are actually quietly failing in the background.

## Appendix B: `.xp` Format Specification (and Import Libraries)

If you are making a console/grid-based game with ASCII graphics, such as a traditional roguelike, by importing `.xp` files directly you will save both development time and huge amounts of space due to the highly compressed format (even smaller than `.png`s of the same image/dimensions). This is the original intent behind REXPaint's design: a tool for drawing lots of ASCII art or maps for use in roguelikes.

The `.xp` files are deflated with zlib (specifically they are gzipped files created via gzofstream); once decompressed the format is binary, and data is stored in the following order (bit size in parenthesis, 32 referring to integers and 8 to unsigned chars):

```text
#─────xp format version (32)

A─────number of layers (32)
 ┌────image width (32)
 │    image height (32)
 │  ┌─ASCII code (32) (little─endian!)
B│  │ foreground color red (8)
 │  │ foreground color green (8)
 │  │ foreground color blue (8)
 │ C│ background color red (8)
 │  │ background color green (8)
 └──┴─background color blue (8)
```

The file begins with the internal `.xp` format version number, You can ignore this value, as it is only used by REXPaint itself (in case future changes to the format are required). Note that because pre-R9 versions of REXPaint did not include an `.xp` version number, it's actually stored as a negative value to differentiate old image files (which begin with a positive layer count) in order to detect and automatically update them.

The actual image data begins with *A*, the number of image layers (always a number from 1 to 9 in the current version), followed by a section *B* for each layer (the image *width/height* is stored for every layer due to the method of serialization used, but will always be the same values for every layer). Section *C* is then repeated for each cell in the image, storing the image's 2D matrix in 1D array format. I.e., the length of that matrix would equal `width*height`, and if you need them you can get the `x-value` with `index/height`, and `y-value` with `index%height` (my own matrix class stores its data in a 1D array so I just read all the cells straight in). Note that this means the image data happens to be stored in column-major order!

One thing to remember about directly reading `.xp` files is that undrawn (empty) cells on any layer (even the base layer) are considered transparent, which is identified by the background color 255,0,255. Thus to rebuild the image as seen in REXPaint, always first test a cell's background color and skip drawing those cells which are transparent, while converting any visible (i.e., non-covered) transparent cells on the lowest layer to black.

If you don't like working with binary, an alternative is to export images to one of the available text-based formats: `.txt`, `.csv`, or `.xml` (see [**Appendix E**](#appendix-e-exportable-text-formats-txt-csv-xml-bbcode)).

## Appendix C: External Libraries and Tools

If you'd like to use (or at least reference) some pre-existing code for reading `.xp` files into your own game/software and converting them to an easy to use format, a number of generous developers have shared their solutions for input/output of REXPaint's native `.xp` format.

* **C\#**
  * SadRex by Thraka, a library for importing `.xp` files\
    <https://github.com/Thraka/SadRex>
  * RexReader by BaconSoap, the original C# `.xp` reader (though it has some issues)\
    <https://github.com/BaconSoap/RexReader>
* **C++**
  * REXReader-C++ by Tim Stoddard, a C++ version of BaconSoap's importer\
    <https://github.com/gamepopper/REXReader-CPlusPlus/>
  * REXSpeeder by pyridine, a fast `.xp` loader that that also supports resaving\
    <https://github.com/pyridine/REXSpeeder>
  * mini-REXSpeeder by Mreuwu, a REXSpeeder alternative compatible with emscripten\
    <http://www.gridsagegames.com/forums/index.php?topic=492.0>
  * RLTK by thebracket, a multifeature roguelike toolkit including xp support\
    <https://github.com/thebracket/rltk>
* **Go**
  * reximage by Ben Nicholls, an `.xp` image importer\
    <https://github.com/BenNicholls/burl-E/tree/master/reximage>
* **Godot**
  * rex_sprite by rzuf, an `.xp` image importer\
    <https://github.com/rzuf79/GDAddons/tree/master/addons/rex_sprite>
* **SFML 2.0**
  * XPText by Tim Stoddard, an SFML entity for rendering `.xp` images\
    <https://github.com/gamepopper/REXReader-CPlusPlus/>
* **Python**
  * XPLoader by RCIX (includes libtcod support!)\
    <https://github.com/RCIX/XPLoader>
* **Python 3 + TDL**
  * XPLoaderPy3 by Edern76\
    <https://github.com/Edern76/XPLoaderPy3>
* **Rust**
  * rs-rexpaint by medusacle, import/export rexpaint ASCII art\
    <https://gitlab.com/medusacle/rs-rexpaint>
* **Swift**
  * REXPaintImage by Steve Johnson, , an `.xp` reader\
    <https://gist.github.com/irskep/1830b1255c1d73c8dd28da8b83998433>
* **Java**
  * xpreader by Stinus Petersen\
    <https://github.com/biscon/xpreader>
* **Javascript**
  * rex_sprite by chiguireitor, a Node.js module for loading and drawing REXPaint sprites\
    <http://www.gridsagegames.com/blogs/files/rex_sprite.js>
  * glyph-image.js by Dominus-Sicarum, a Node.js module for loading `.xp` files as an Array of Maps\
    <https://gist.github.com/Dominus-Sicarum/8ed5354e65c36d0910819b1d32087652>
* **Haxe**
  * REXPaintLoaderHaxe by Matt Johnson\
    <http://lib.haxe.org/p/REXPaintLoaderHaxe/>
* **Clojure**
  * rockpick by Aaron Santos, an `.xp` import library\
    <https://github.com/aaron-santos/rockpick>
* **Nim**
  * rexpaint_nim by Steve Landey, an `.xp` parser\
    <https://github.com/irskep/rexpaint_nim>
* **LOVE2D**
  * rexpaint.lua by Vriska Serket, a lightweight REXPaint `.xp` file reader\
    <https://gist.github.com/vriska-serket/334bfcfa7dfe7265ddbe089e4a51e522>

Other tools:

* **image2xp**: python script to convert an image file to ASCII or .xp (sample output), by mtvee. ([sample output](https://i.imgur.com/rAwIWeu.jpg))\
  <https://gist.github.com/mtvee/5629a2caa34dbf3ece95>
* **png2rex**: utility for converting `.png`s to `.xp`, by thebracket\
  <https://github.com/thebracket/png2rex>
* **txt2xp**: python script to convert a txt file to `.xp`, by mtvee\
  <https://gist.github.com/mtvee/d7a4bd450e3cd6766580>
* **txt to .xp**: C code to convert a `.txt` file to `.xp` (minus the gzip step), by gumix\
  <http://www.gridsagegames.com/forums/index.php?topic=416.msg3677#msg3677>
* **rex2ansi**: utility for converting `.xp` files to 24-bit `.ans`, by Sludge.
  <https://github.com/mlabbe/rex2ansi/releases>

## Appendix D: ANSI Art `.ans`

For the ANSI artists out there, REXPaint also supports exporting to `.ans`.

Creating ANSI art is a little bit different from REXPaint's normal use, so you'll want to follow some basic guidelines:

* Before starting, copy the contents of the `data/ansi` directory to their respective data folders:

  * all files in `data/ansi/fonts` to `data/fonts` (overwrite `_config.xt` when prompted)
  * all files in `data/ansi/palettes` to `data/palettes`
  * `REXPaint.cfg` to the main directory (overwrite).

  Copying these files gives you access to the proper palette and an alternate set of more appropriate fonts, but you can always edit `_config.xt` to make even the square fonts accessible again if preferred.
* Open REXPaint, make your masterpiece, and when done press `Ctrl-a` to create the `.ans` file (there is no button for `.ans` export—it's a "secret" :).

Miscellaneous Notes:

* Separate layers can be used in the editing process, and any that are visible (not hidden) when the `.ans` is exported will be merged together, so you always get what you see.
* REXPaint does not currently import `.ans` files, so make sure you keep the `.xp` files as well for later editing should you need them (`.xp` files are compressed and extremely tiny, so size certainly won't be an issue).
* ANSI palette colors are identified by their position in the palette, not the actual color. Therefore, you can create any other ANSI palette you like (or modify the existing one), so long as it follows the same positioning: black, red, green, yellow, blue, magenta, cyan, then white (with normal colors in the first row, and bright/bold text colors in the second row). A table of color values for common ANSI palettes on different system can be found [on this page](http://en.wikipedia.org/wiki/ANSI_escape_code).
* **Do not** use a different palette with an image after it has already been created (without doing a full palette-based color swap) because REXPaint needs to find the image colors in the palette when exporting the `.ans` file to determine which color type it is. This means that when exporting an `.ans` file, the same palette used to make the image must be showing.

Further Explanation:

* The alternate `.cfg` file sets the `defaultImageWidth` value to 80. You can use a different view width (`canvasWidth`) if you like, but always leave the image width at 80, the value which REXPaint will set in the `.ans` file. Image height can be resized to anything you want in REXPaint, but leave the view height something reasonable for your screen size.
* It also changes `startPalette` from `Palette` to `ANSI VGA`.
* Most importantly it changes `ansiMode` to 1, an option only available by editing the `.cfg` manually (i.e. not listed in the options menu). This prevents all but the first 8 colors from being set as the background (a standard ANSI limitation), so if you want to use REXPaint for normal true color painting you'll have to close the program and set this value back to 0. ANSI mode also makes the color picker inaccessible through the brush color, forcing you to use the palette.

## Appendix E: Exportable Text Formats (`.txt`, `.csv`, `.xml`, `BBCode`)

Export an image as pure text by pressing `Ctrl-t`. This will only output the glyphs, thus no color information is stored in the file. By default, `.txt` export uses UTF8 encoding, but this includes unicode hard space encoding so anyone who wants pure ASCII characters should set `txtOutputUTF8=0` in REXPaint.cfg.

---
While `.xp` is the ideal format for use in other programs (see [**Appendix B**](#appendix-b-xp-format-specification-and-import-libraries)/[**C**](#appendix-c-external-libraries-and-tools)), if you don't want (or are unable) to work with a binary file there are other export options that produce files both human readable and potentially useful in other applications. Naturally all other formats will create files significantly larger than their `.xp` counterparts, but some users may still prefer or need them for transferring or converting the data. Unlike `.xp` files, these formats do not store each layer separately, instead merging all visible layers into a single image and storing that.

---

### `.csv`

The first line stores header information, and all following lines contain the image data in the following format: X,Y,ASCII,Foreground,Background. ASCII values are stored in integer form, and colors are stored as hex values.

### `.xml`

All image rows are enclosed in `<data></data>` tags, each row of image data is enclosed in `<row></row>` tags, and there will be `<height>` number of rows, each with `<length>` number of cell data. Within each row, each cell is enclosed in `<cell></cell>` tags, and contains `<ascii>`, `<fgd>`, and `<bkg>` tags indicating that cell's ASCII index (stored as an integer, not a character), foreground, and background colors, respectively. Colors are stored as hex values.\
`.xml` files are quite bulky due to the amount of markup required.

### `BBCode`

Properly formatted monospaced is output to a text file from where you can copy it to a forum. Mostly a novelty—though I'm sure creative users will find some interesting uses for it.

Unlike pure text output, `BBCode` retains both the ASCII (stored as unicode) and foreground color. Since most forums do not support background colors, those in the image will be ignored. (I could add it as a configurable option if there's any demand, since some forums do have background color tags.)

For now, if you plan to export `BBCode` I suggest filling the background with whatever color the forum uses, so you have an idea of what the image will actually look like; that and load up a taller narrow font more like what a website will use (also to have a better perspective). REXPaint's standard version only comes with square fonts right now, but others can be found on the website's Resources page, or are included in the ANSI version.\
Another difference you'll notice when copying `BBCode` to a forum is that line spacing will cause a divide between each row, which may or may not impact the image's appearance depending on what glyphs are used.

**important**: Space characters are usually collapsed when entered into a web browser. To avoid this issue and ensure that glyphs are arranged/indented properly in an image, a "hard space" unicode character is used in place of each normal space. Copying the `BBCode` from the output text file will also copy these hard space characters normally and maintain the image's appearance, but it seems that secondary copying from within a forum itself does **not** retain the proper spacing—it converts them to normal spaces, which will then collapse. The only way around this seems to be always copy the `BBCode` content from the original source text file. An alternative is to fill unused image space with the "full block" ASCII character (this is easy to do with the fill tool, and can be done before starting to draw). This method can also be used to create makeshift "backgrounds."

## Appendix F: Importing Text Files

REXPaint normally only edits its native `.xp` format, but it is also possible to use command line instructions to convert an existing `.txt` file into an `.xp` file for editing. While the process is not incredibly convenient since REXPaint wasn't really meant for this purpose, it can be helpful in some situations and was therefore added by request :D.

To convert a `.txt` file to `.xp`, simply put it in the `/images/` directory and run REXPaint with the command line argument `-txt2xp:XXX`, where `XXX` is the name of the file to convert. The file name as provided can include or exclude the extension (e.g. `image.txt` or just `image`), but the file itself is expected to have a proper `.txt` extension. The width of the image produced will be determined by the longest line in the `.txt` file, and by default will use black glyphs on a white background, but once in REXPaint you can easily swap the colors or perform any other normal edits.

Note that only plain text files are supported (glyphs 0~127, no UTF encoding), and if an `.xp` file of the same name already exists, **it will be overwritten**!

See also [**Appendix C**](#appendix-c-external-libraries-and-tools) for some third-party tools/code also capable of converting `.txt` files to `.xp`.

## Appendix G: Importing `.png`s

REXPaint is capable of partially converting `.png` images to `.xp` files for editing. This is a special feature developed for my own use in roguelike development, which I've included for the heck of it in case someone else finds it useful. Like `.txt` imports, it requires use of the command line.

To convert a `.png` file to `.xp`, put it in the `/images/` directory and run REXPaint with the argument `-png2xp:XXX`, where `XXX` is the name of the file to convert. The file name as provided can include or exclude the `.png` extension, but the file itself is expected to have a proper `.png` extension. Moreover, the file name must include `_WWWxHHH` at the end, where `WWW` and `HHH` are the pixel width and height of an individual cell in the image. E.g. a Nethack screenshot using an 8x16 monospaced font should be named something like `NetHack_8x16.` (This feature was intended to read in images of grid-based terminal output, such as roguelike screenshots.)

While the resulting `.xp` image will properly assign all foreground and background colors, it cannot actually identify glyphs for what they are. Instead any glyph-containing cell will simply use "?" (in the proper color) to represent a glyph at that location. (Actually identifying glyphs would be a far more complex process requiring OCR etc.) You can also add the `-uniqueGlyphs` switch to the command line, which instead of representing glyphs as "?", will at least distinguish between glyphs within the image that are different from each other and use a unique glyph to represent each one (but the same unique glyph for those that match). Because this was originally developed to as a roguelike screenshot reader, it will also automatically use "." to represent the most commonly found glyph in the original image.

A wider application of this feature would be for simple pixelwise conversion of any `.png` image into an `.xp` file, where each pixel represents the background color for a single cell. In that case, either specify that is the intent by appending `_1x1` to the filename (basically "each pixel is a cell"), or simply append nothing and it will be assumed this is the purpose.

It is assumed the `.png` source has no transparency layer.

## Appendix H: Batch Exporting `.png`s

Simultaneously exporting every `.xp` image found in the `/images/` directory (and its subdirectories) is supported via command line, simply add the `-exportAll` switch when running REXPaint to create a `.png` image for each file. The font and character size used for all images is determined by your current `REXPaint.cfg` settings, and therefore font size is normally limited to those options which REXPaint can normally display on your device, although this restriction can be circumvented by enabling the `unlimitedFontSize` option described earlier. A summary of the conversion process can be found in the `run.log` file.

## Appendix I: Exporting ANSI art for C:DDA

REXPaint can also export art in the format used for the roguelike Cataclysm: Dark Days Ahead (`C:DDA`). It's a text format somewhat similar to `BBCode`, but with its own quirks. Use `Ctrl-j` to export to this format.

For the export to produce a file that can be directly used by C:DDA, it may not have a width greater than 41 characters, thus it is recommended to set your `Default Image size` to that width in the options menu so that all art starts at that width by default. (No restrictions on height.) Also only C:DDA-compatible colors are exported, and for your convenience there's a premade palette including those colors attached to [this post](https://www.gridsagegames.com/forums/index.php?topic=1463.msg9345#msg9345).

For the best editing experience, consider using the standard font used by C:DDA, Unifont 8x16, available on the website's Resources page.

Other references:

* [C:DDA Ascii_arts format](https://github.com/CleverRaven/Cataclysm-DDA/blob/master/doc/JSON_INFO.md#ascii_arts)
* [C:DDA Colors](https://github.com/CleverRaven/Cataclysm-DDA/blob/master/doc/COLOR.md)

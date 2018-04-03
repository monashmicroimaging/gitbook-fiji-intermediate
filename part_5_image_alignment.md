# PART 5: IMAGE ALIGNMENT {#part-3-image-alignment}

Sometimes we have multiple images that belong together in one larger image. Often times these can be captured and processed to create this larger image during acquisition, but in some circumstances we need to combine the images manually after acquisition. In those cases, we can use tools in FIJI to combine or align these images into a seemless single image.

For stictching we use the demo images **Tile01.tif**\_** **\_through to **Tile06.tif** found in the Demo Images sub-folder titled 'Manual Stitching'. For TrackEM2 alignment we use the image set found in the demo images sub-folder titled 'TrackEM2'.

## Pairwise Stitching {#stitching}

Stictching combines multiple tiled image into a single large format image. One option to do this in FIJI is to use the **pairwise Stitching** plugin, found under the  **Plugins -&gt; Stitching **menu. This option allows you to combine images 2 at a time and is useful for small numbers of images, where there is no specific order.

First you need to open at least 2 images that you want to sticth. Here we will use the the two demonstration images **Tile\_03.tif** and **Tile\_04.tif**. Select Pairwise Stiching from the menu by going to** Plugins -&gt; Stichting -&gt; Pairwise Stitching**.

![](/assets/part 5/Stitching 1 menu.jpg)

In the Pairwaise stitching window, select Tile\_03 and Tile\_04 as your images from the drop down menus \(the order doesn’t matter\) then click **OK**.

![](/assets/part 5/Stitching 2 options.jpg)

In the second options window, you can give your final image a new name, but no other settings should need adjusting. Click **OK** to begin the stitching process.

![](/assets/part 5/Stitching 3 options 2.jpg)

A log window will show progress and your stiched image will open in a new window upon completion.

![](/assets/part 5/Stitching 4 Log.jpg)

![](/assets/part 5/Stitching 5 original vs stitched .jpg)

You can then repeat the steps to add other panels if you have more than two images, by opening the next image and using that plus your newly stitched image as your 2 images to combine.

## Grid Stitching

There also is a grid stitching option that you can use for larger numbers of images that were recorded with a motorized stage in a defined pattern. This is also found under the  **Plugins -&gt; Stichting **menu.

You do not need to have your images open in FIJI, but they must been named in specific manner and all must be named in the same format \(ie: here they are all named Tile\_xx.tif\).

Begin the process by going to **Plugins -&gt; Stitching -&gt; Grid/Collection Stitching**.



## TrakEM2 Advanced Image Alignment {#trackem2-advanced-image-alignment}

Go to File&gt;New&gt;TrakEM2 \(blank\) and create a storage folder as prompted by the software. Drag and drop _**folder TrakEM2**_** **into the main window \(large black area\) and open as stack. Enter the distance between images or the thickness of your sections depending on if you’re aligning a confocal z-stack or tissue sections. For the workshop data, please enter 20um.

TrakEM2 will now load and display the images. You can zoom in and out by holding down Ctrl and turning the mouse wheel. You can play through the slices with the slider in the lower left corner of the main window. You can pan around by clicking with the mouse on the image and drag it around.

Left-click with the mouse on the image and then right-click and choose Align&gt;Align stack slices from the right-click menu. Accept all defaults by clicking ‘Ok’ three times.

If you scroll through the slices now, you see that the sections are all aligned to each other. To save your aligned image stack, right-click again, select Export&gt;Make flat image…, make sure that Scale is set to 100% \(you can reduce your image size here if you like but not recommended as you lose data\), select Type: RGB Color for histology images \(use 8-bit greyscale for single channel fluorescence images\), select Start: layer 1 and End: layer 7 \(or the last layer of you stack\). For Background Color set all three base colours to 255 which will give the final image a white background. If you have a fluorescence stack, you want to have a black background so you would need to set the three base colours to 0. Tick ‘Best Quality’ and press ‘Ok’. You can save the resulting final image as a tif image.


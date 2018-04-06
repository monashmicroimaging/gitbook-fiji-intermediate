# PART 5: IMAGE ALIGNMENT {#part-3-image-alignment}

Sometimes we have multiple images that belong together in one larger image. Often times these can be captured and processed to create this larger image during acquisition, but in some circumstances we need to combine the images manually after acquisition. In those cases, we can use tools in FIJI to combine or align these images into a seemless single image.

For stictching we use the demo images _Tile01.tif _through to _Tile06.tif_ found in the demo images sub-folder titled 'Manual Stitching'. For TrackEM2 alignment we use the image set found in the demo images sub-folder titled 'TrackEM2'.

## Pairwise Stitching {#stitching}

Stictching combines multiple tiled image into a single large format image. One option to do this in FIJI is to use the **pairwise Stitching** plugin, found under the  **Plugins -&gt; Stitching **menu. This option allows you to combine images 2 at a time and is useful for small numbers of images, where there is no specific order.

First you need to open at least 2 images that you want to sticth. Here we will use the the two demonstration images _Tile\_03.tif _and _Tile\_04.tif_. Select Pairwise Stiching from the menu by going to** Plugins -&gt; Stichting -&gt; Pairwise Stitching**.

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

Begin the process by going to **Plugins -&gt; Stitching -&gt; Grid/Collection stitching**.

![](/assets/part 5/Stitching 7 menu - grid.jpg)

In the first window, select the pattern of image acquisiton from the drop down menus for **Type** and **Direction**. The image below these menus will illustrate the selected pattern for clarity. Here the image were captured as "Snake by Rows" and "Right & Down".

Click **OK** to proceed.

![](/assets/part 5/Stitching 8 - colleciton pattern.jpg)

In the next options window, check the grid size is correct and adjust to the correct number of rows \(x\) and Columns \(y\) as needed. Here we had 3 rows x 2 columns.

Adjust the overlap to that used during automatic aquisiton or an estimate \(over-estimating is better than under\) is captured manually. Here we use 20% overlap.

Enter the number of the first image in the sequence, or leave as 1 if all images are being included.

Select the folder where your images are saved by browsing under **Directory**. Then finally ensure the file name format is entered as used for your files.

![](/assets/part 5/Stitching 9 - grid stitch options.jpg)

No other stitching/blending options should need to be altered from the default.

Click **OK** to proceed with stitching.

![](/assets/part 5/Stitching 10 - grid stitch log.jpg)

Again a log window will display your progress and the final image will open in a new image window upon completion.

![](/assets/part 5/Stitching 11 - grid stitch result.jpg)

Often times, especially when images were acquired manually \(as done here\), there will be black space at the edges where shifts were required to line up images accurately. The final image may be cropped to ensure smooth edges without these blank sections.

## TrakEM2 Advanced Image Alignment {#trackem2-advanced-image-alignment}

To align z-stack images or histological serial sections that have been imaged in different oritentations you can use the **TrackEM2 **tool.

Go to begin go to **File -&gt; New -&gt; TrackEM2 \(blank\)**.

![](/assets/part 5/TrackEM2 1 - menu.jpg)

Create a storage folder in your desired directory as prompted by the software.

![](/assets/part 5/TrackEM2 2 - storage folder.JPG)

This will open a working area with several different windows.

![](/assets/part 5/TrackEM2 3 - windows.JPG)

Drag and drop your folder containing all images \(and only those images\)** **into the main window \(large black area\). In the demo images we have a folder called _TrackEM2_ with images for use here.

![](/assets/part 5/TrackEM2 4 - drag and drop.jpg)

Select **Open as stack** when prompted. The enter the distance between images \(for z-stacks\) or the thickness of your sections \(for histological serial sections\). For the workshop data, please enter 20um.

![](/assets/part 5/TrackEM2 5 - open as stack.JPG)

![](/assets/part 5/TrackEM2 6 - slice thickness.JPG)

TrakEM2 will now load and display the images. You can zoom in and out by holding down Ctrl and turning the mouse wheel. You can play through the slices with the slider in the lower left corner of the main window, below the thumbnails. The red outline in the thumbnails shows the image area \(which will enable you to easily see the area of each section within the image and how they do or don't line up\). You can pan around by clicking with the mouse on the image and drag it around.

![](/assets/part 5/TrackEM2 6b - images open.JPG)

Left-click with the mouse on the image to activate the window, then right-click and choose **Align -&gt; Align stack slices** from the right-click menu.

![](/assets/part 5/TrackEM2 7 - align menu.jpg)

Accept all defaults by clicking **OK **three times.

![](/assets/part 5/TrackEM2 8b - align options combined.JPG)

If you scroll through the slices now, you see that the sections are all aligned to each other.

To save your aligned image stack, right-click again, select **Export -&gt; Make flat image…**

![](/assets/part 5/TrackEM2 11 - save flat image.jpg)

Make sure that **Scale** is set to 100% \(you can reduce your image size here if you like but not recommended as you lose data\) and select **Type:** RGB Color \(for histology images\) or  8-bit greyscale \(for single channel fluorescence images\). Set your first and last images as the **Start **and **End** layers. For **Background Color** set all three base colours to 255 to give a white background \(for histology images\) or set all three base colours to 0 to give a black background \(fluorescent images\). Tick **‘Best Quality’** and ensure the final image is saving in .tif format, then click **OK** to save.

![](/assets/part 5/TrackEM2 12 - save options.JPG)


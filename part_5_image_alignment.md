# PART 5: IMAGE ALIGNMENT {#part-3-image-alignment}

## Stitching {#stitching}

Open images _**Heart I.tif**_** **and _**Heart II.tif**_. Go to Plugins&gt;Stitching&gt;Pairwise Stitching. Select Heart I as and heart II as your images, the order doesn’t matter, then press ok. You will get a stitched image as result that you can then use to add other panels if you have more than two.

![](/assets/part3/stitching_images.jpg)

There also is a grid stitching option that you can use if you recorded several images with a motorized stage in a defined pattern.

![](/assets/part3/stitching_options.jpg)

## TrakEM2 Advanced Image Alignment {#trackem2-advanced-image-alignment}

Go to File&gt;New&gt;TrakEM2 \(blank\) and create a storage folder as prompted by the software. Drag and drop _**folder TrakEM2**_** **into the main window \(large black area\) and open as stack. Enter the distance between images or the thickness of your sections depending on if you’re aligning a confocal z-stack or tissue sections. For the workshop data, please enter 20um.

![](/assets/part3/trakEM2_import.jpg)

![](/assets/part3/trakEM2_options.jpg)

TrakEM2 will now load and display the images. You can zoom in and out by holding down Ctrl and turning the mouse wheel. You can play through the slices with the slider in the lower left corner of the main window. You can pan around by clicking with the mouse on the image and drag it around.

Left-click with the mouse on the image and then right-click and choose Align&gt;Align stack slices from the right-click menu. Accept all defaults by clicking ‘Ok’ three times.

If you scroll through the slices now, you see that the sections are all aligned to each other. To save your aligned image stack, right-click again, select Export&gt;Make flat image…, make sure that Scale is set to 100% \(you can reduce your image size here if you like but not recommended as you lose data\), select Type: RGB Color for histology images \(use 8-bit greyscale for single channel fluorescence images\), select Start: layer 1 and End: layer 7 \(or the last layer of you stack\). For Background Color set all three base colours to 255 which will give the final image a white background. If you have a fluorescence stack, you want to have a black background so you would need to set the three base colours to 0. Tick ‘Best Quality’ and press ‘Ok’. You can save the resulting final image as a tif image.

![](/assets/part3/trakEM2_options2.jpg)


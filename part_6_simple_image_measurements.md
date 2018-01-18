# PART 6: SIMPLE IMAGE MEASUREMENTS {#part-9-simple-image-measurements}

Many of the simple FIJI functions that you have previously learnt about can be combined with other tools for more complex processes to analyse and measure your data. Here, our instructions become more speicified as wel go through several examples of common measurements using the different tools in FIJI.

In this section we use the images **RGB-blue, RGB-green, Nuclei-1** and **MovieStack** for demonstration.

## Area Measurements {#area-measurements}

To perform any measurements on our image we must ensure the scale is calibrated. Checking and setting the scale calibration was covered in FIJI Basics.

We also need to select an area within the image that we want to measure. Without a selection, the program would give an area measurement for the entire image, rather than just the area of interest. In this example we will use a threshold, but you can also select a specific area to measure by using an ROI.

Open the image **RGB-blue. **Check that the scale is calibrated before carrying out any further steps.

For colour images I like to apply a grey LUT to allow better contrast between the stain and background during thresholding.** **You may also like to **Duplicate** the original image and work on a copy. This image is already grey, but apply a grey LUT if you are working with a colour image, then duplicate the image if you would like, and go to **Image -&gt; Adjust -&gt; Threshold** \(or use short cut Ctl + Shift + T\).

![](/assets/part 6/Area 1 - Threshold Menu.jpg)

Fit your threshold to the data as best as possible. Here I have used the _Default_ algorithm set at 65 and 255.Find a threshold that works for you.

![](/assets/part 6/Area 2 - Threshold Options.JPG)

Close the options box to keep the selection as a threshold, or click **Apply** to generate mask as previously described.

If you choose to work with the threshold you can skip straight to measurements from here, however the threshold is not always a perfect selection of the data. Which is why we often create the mask.

If you are working with a mask you can perfect your selection using filters. You can see in this image mask but there are a few blemishes that may affect the measurement. You can see below that we have some small speckled areas detected outside the nuclei, as well as some spots within the nuclei that are not masked completely.

![](/assets/part 6/Area 3 - Mask.JPG)

To take care of these 'gaps' in the nuclei mask we are going to use the **Fill Holes** option found under **Process -&gt; Binary -&gt; Fill Holes**.

![](/assets/part 6/Area 4 - Fill Holes Menu.jpg)

This will complete the mask over areas that contained gaps previously.

![](/assets/part 6/Area 5 - Filled Mask.JPG)

Next we will remove the small spots detected outside the nucleus using the **Remove Outliers** filter. Go to **Process -&gt; Noise -&gt; Remove Outliers**.

![](/assets/part 6/Area 6 - Remove Outliers Menu.jpg)

Turn on the preview, ensure it is set to act on the Bright or Dark part of the mask underthe  _Which outliers_ drp down menu \(this will be dependant on your mask colours - for me it needs to be set to Dark\). Set a pixel radius that captures all spots outside the nuclei, in my example the default setting of 2 works nicely. Find an option that works for your image. Click **OK** to apply the filter.

![](/assets/part 6/Area 7 - Remove Outliers Options.JPG)

You should now have a mask that nicely represents the nuclei in the original image.

![](/assets/part 6/Area 8 - Final Mask.JPG)

To measure the area in either your thresholded image or your mask, you first need to set your output parameters. Go to **Analyse -&gt; Set Measurements**.

![](/assets/part 6/Area 9 - Set Measurements Menu.jpg)

In the **Set Measurements** window you can choose what you want to measure by clicking on or off the checkboxes beside different parameters. Here we will turn on **Area** only.

Ensure you also have **Limit to threshold **selected in the options so that FIJI does not measure the entire image.

Click **OK** to save the output parameters.

![](/assets/part 6/Area 10 - Set Measurements Options.JPG)

Now that the parameters are set, to measure the area of the nuclei using the parameters you have just set go to **Analyze -&gt; Measure** \(or shortcut Ctrl+M\).

![](/assets/part 6/Area 11 - Measure Menu.jpg)

This will give you a results table with the area of the nuclei. You will notice there is only one measurement. This is because this method measures the mask or threshold as a single entity.

![](/assets/part 6/Area 12 - Measurement Result Mask.JPG)

If you have used a mask for your measurement, you may notice a rather large number. Compare here the measruements from a Mask and a threshold on the same image.

![](/assets/part 6/Area 13 - Measurement Mask vs Threshold.JPG)

Sometimes FIJI will measure a mask as expected perfectly fine. But often It will still easure the entire image, disregarding the selected/masked area. You can fix this with a simple additional step.

Go to **Edit -&gt; Selection -&gt; Create selection**. \(Masked area must be black on a white background here and the ROI selection will be for the black component of the image\)

![](/assets/part 6/Area 14 - Create Selection.jpg)

ROIs will apprear around all of the masked nuclei.

![](/assets/part 6/Area 15 - Selected Mask.JPG)

Repeat the measurement \(**Analyze -&gt; Measure**\). You should have the correct value now. Compare this result to the previous 2 values.

![](/assets/part 6/Area 16 - Selected Mask Result.JPG)

## Mean Intensity Measurements {#mean-intensity-measurements}

To generate a basic intensity measurement we apply a similar method as the basic area measurement. However, for intesntiy measurements, even with the output parameters set to **Limit to threshold**, or using ROIs, if we try to measure a mask we will only get intensity readings on the intensity values within the mask itself \(0 and 255 as it is a black and white image\), not in the image. Therefore, when measuring intensity the threshold MUST be maintained, never converted to a mask or binary.

To do this, open the image **RGB\_Blue.tif** and repeat your thresholding. Go to **Image -&gt; Adjust Threshold**.

![](/assets/part 6/Intensity 1 - threshold menu.jpg)

Find the threshold to best fit the data \(I have again used Default at 65 and 255\). But DO NOT press apply! Close the options box using the cross at the top.

![](/assets/part 6/Intensity 2 - threshold options.jpg)

This will give you an image with the stain selected by threshold, but not converted to a mask.

![](/assets/part 6/Intensity 3 - thresholded image.jpg)

With a threshold we can no longer make modifications in order to perfect our seelction. What we see here is what we will measure.

So we can now go straight to setting our measurement paramenters. Again go to **Analyse -&gt; Set Measurements**.

![](/assets/part 6/Area 9 - Set Measurements Menu.jpg)

This time we want to set **Area, Min & max gray value** and **Mean gray value**.

Again ensure the checkbox next to **Limit to threshold** is selected.

Select **OK** to save the changes.

![](/assets/part 6/Intensity 4 - set measurement options.jpg)

Repeat the measurement process as before by going to to **Analyze -&gt; Measure** \(or shortcut Ctrl+M\).

![](/assets/part 6/Intensity 5 - measure menu.jpg)

This will give you a measurement for the intensity in the original image, limited to the area under the threshold you have set.

![](/assets/part 6/Intensity 6 - measurement.jpg)

## Intensity Map \(Rainbow RGB LUT\) {#intensity-map-rainbow-rgb-lut}

For a visual representation of the intensity, you can map the intensities across the image very simply using a LUT.

Open he image **NeuralTubeRed.tif** and go to **Image -&gt; Look up Tables**, and select the LUT **Rainbow RGB** from the bottom of the list \(or select the Rainbow LUT form the LUT menu in the tool bar\).

![](/assets/part 6/RainbowLut 1 - menu.jpg)

This will apply a multi-coloured LUT to your image, in shades of red, blue or green. The highest 33% of intensities are reds, the middle 33% are greens and the bottom 33% are blues. This gives the viewer the ability to easily see the range of intensities present in the image.

![](/assets/part 6/RainbowLut 2 - LUT on.jpg)

You can add a calibration bar for the intensities by going to **Analyze -&gt; Tools -&gt; Calibration Bar**.

![](/assets/part 6/RainbowLut 3 - Calibration bar Menu.jpg)

In the **Calibration Bar** window you can specify the position and configuration of the calibration bar. The **Overlay** tick box allows you to create the bar as an overlay of the original image, instead of burning it into the image permanently.

![](/assets/part 6/RainbowLut 4 - Calibration bar options.jpg)

Click **OK** to add the calibration bar to your image.

![](/assets/part 6/RainbowLut 5 - Calibration bar added.jpg)

## Simple Counting {#simple-counting}

Often we want to know how many cells or object we have in an image. For a low number of objects you can easily count manually using the multi-point tool.

Open **RGB-Blue.tif** and select the multi-point tool from the FIJI tool bar.

If multiple points are showing in the tool icon \(as below\), you can simply click it on.

![](/assets/part 6/Simple Count 1 - multipoint tool.JPG)

If only a single point is visible on the icon, switch it to multi-point by right clikcing and selecting **Multi-point Tool** from the options.

![](/assets/part 6/Simple Count 1b - multipoint tool selection.JPG)

Once the tool is active \(indented\), double click on the icon again to open the **Point Tool** options window. Set up your points as you want them to appear on your image by selectin colour and size from the drop down menus. Ensure **Label Points** and **Show All** are selected. Leave the window open.

![](/assets/part 6/Simple Count 2 - multipoint tool settings.JPG)

Return to your image and click once on every object you want to count. A point will appear on the image for each click. As you click you will see a counter increasing at the bottom of the **Points Tool** window. Once you have clicked on all of your objects, the final number will be your object count. Each object will also be marked in the image as a check of whether you correctly counted the object.

![](/assets/part 6/Simple Count 3 - multipoint tool count.JPG)

The window shows that we have 9 nuclei in this image. We always exclude partial nuclei/cells/objects at the edges of an image from analysis such as counts.

## Analyse Particles {#analyse-particles}

For an image with a large number of objects manually clicking to count can be a laborious task. For these images you can use the **Analyze Particles** tool. This tool also enables you to measure other aspects of teh objects \(such as area\) at the same time as counting.

To use this tool, you first need to threshold your image as previously shown. Open the image **Nuclei-1.tif. **Apply a grey LUT if you desire. I find this makes thresholding easier.

![](/assets/part 6/Analyze particles 1 - grey LUT.jpg)

Select a threshold that fits your data then click **Apply** to create a mask \(here, I used the Huang algorithm\).

![](/assets/part 6/Analyze particles 2 - Threshold menu.jpg)

![](/assets/part 6/Analyze particles 3 - Threshold options.jpg)

You will see several issues with this mask; gaps within the nuclei and small particles detected outside the nuclei.

![](/assets/part 6/Analyze particles 4 - initial mask.jpg)

For counting these small particles can be problematic as they will be counted as an object, when they are in fact a false positive. To clean up the mask a little, we will apply the **Fill Holes** and **Despeckle** tools to the mask. Find these under the **Process **menu.

![](/assets/part 6/Analyze particles 5 - fill holes.jpg)

![](/assets/part 6/Analyze particles 6 - despeckle.jpg)

Another problem that will result in a false count with this mask is several areas where nuclei were touching, resulting in them being masked as a single object. To separate these we need to apply a **Watershed** binary filter to the mask. Select this from the **Process -&gt; Binary** menu as previously described to separate touching objects.

![](/assets/part 6/Analyze particles 7 - watershed.jpg)

This gives us a fairly neat mask for analysis. There are still a number of small objects that will be counted as false positives but we can exclude them during the analysis process.

![](/assets/part 6/Analyze particles 8 - final mask.jpg)

Before we do our analysis, check the measurements you need are set by going to **Analyze -&gt; Set Measurements**. Here we will only check **Area.**

![](/assets/part 6/Analyze particles 9 - set measurements menu.jpg)

![](/assets/part 6/Analyze particles 10 - set measurements options.jpg)

We can now count our objects using **Analyze Particles **tool. Find this under the **Analyze** menu.

![](/assets/part 6/Analyze particles 11 - AP menu.jpg)

In the resulting options box, we can adjust the size to exclude smaller objects. This eliminates those false positive specks thatremain in the mask. I have set the lower limit to 15 for this example. Leave the upper limit unchanged \(infinity\). Leave **Circularity** at the default values. Set **Show:** to **Outlines** and tick the boxes to **Display Results, Summarize, Add to Manager **and** Exclude on Edges** as shown below. Press **OK** to measure the objects.

![](/assets/part 6/Analyze particles 12 - AP options.jpg)

This set up will result in a number of new "results" windows. you will now have a results table displaying the selected measurements for each individual object detected \(in tihs example, Area only\). The Summary box will display the total count for you. An image of the outlines, numbered to matcht he results will be created, which you can save for future reference. We also have all objects added to the ROI manager which can be overlayed other images for measurements \(ie intesity in another channel\), or saved for future use.

![](/assets/part 6/Analyze Particles 13 - Results.JPG)

You can also see in the original image that the small outliers that we didn't want to count have been excluded from the analysis \(no ROI outline\) by adjusting the size. We would use the Outline map and the original image here to ensure we have measured only the objects we want, and adjust our optins and re-measure as needed.

## Redirect Measurements {#overlay-masks}

Masks, thresholds or ROIs generated on one image can also be used to make measurements on another image. This allows you to measure the same area in different channels or images.

One method for applying your selection to a different image during measurement is to use 'redirect'.

To demonstrate this we will use the images **RGB-blue.tif** and **RGB-green.tiff**. We will generate a threshold of the nuclei \(blue\) image and use that to measure the intensity of the stain in the "nucleus" only on the green image. We will also measure the area under the threshold in both the original image, then the green image to confrim it is measuring the same area in both images.

Open both images and generate a threshold for your nuclei using the methods previously described.

![](/assets/part 6/Redirect 1 - threshold on nuclei menu.jpg)

![](/assets/part 6/Redirect 2 - Threshold on nuclei settings.JPG)



Ensure the thresholded nuclei image is active \(click on the imge\) then go to **Analyze -&gt; Set Measurements**.

![](/assets/part 6/Redirect 3 - Set Measurements menu.JPG)

In the **Set Measurements** window, select **Area** as the measurement criteria. Make sure you have **Limit to Threshold** ticked, then click on **OK** to set the paramenters.

![](/assets/part 6/Redirect 4 - Set Measurements Option Area only.JPG)

Once your parameters are set, go to **Analyze -&gt; Measure** to generate teh measurement.

![](/assets/part 6/Redirect 5 - Measure menu.JPG)

We now have the area of the "threshold" as a control for ensuring we are measuring the same part on the green image.

![](/assets/part 6/Redirect 6 - Area Blue image.JPG)

To make sure this is the case, we want to generate a selection fo the thresholded area. To do this, go to **Edit -&gt; Selection -&gt; Create Selection**.

![](/assets/part 6/Redirect 7 - Create Selection Menu.JPG)

This will 'outline' the thresholded area as an ROI in the nuclei image.

![](/assets/part 6/Redirect 8 - Threshold with selection.JPG)

We can now tell FIJI to measure any parameters we want in the green image, using this selection. To do this we open the **Set Measurements** settins again.

![](/assets/part 6/Redirect 3 - Set Measurements menu.JPG)

In **Set Measurements**, add **Mean Grey Value** to the measurement settings, then select **RGB-Green.tif** from the drop down menu under **Redirect to:**.

![](/assets/part 6/Redirect 9 - Set Measurements Option redirect.JPG)  


Click **OK** to perform the measurements on the second image. You will now get measurement for the second image in the areas under the original mask.

![](/assets/part 6/Redirect 10 - measurements on green.JPG)

you can see fromt he comparisson with the blue image measurement that we have measured the exact same area in the green image. And we now have the mean intensity for the pixels \(ie: your green stain\) within that area.

## Overlay ROIs {#masks-to-rois}



## Individual Measurements from Multiple ROIs

To get individual measurements for areas in a mask, generate your mask as required then go to **Analyze -&gt; Anylze Particles**. 

This time in the **Analyze particles** window, tick off every options box except **Add to Manager**. Select **OK**.



The mask will be converted to ROIs in the ROI manager.



You can now use this to make multiple measurements on your original image. Set your measurements and then click on **Measure** in the ROI manager. Note that for intensity measurements you should apply the ROIs or redirect to the original image as intensity can’t be measured in a mask.

To apply the ROIs to another image, select your second image and go to **Image -&gt; Overlay -&gt; From ROI Manager**.



The ROIs generated from the mask will be applied to the second image and you can now set your measurements for the second image and measure the same area.






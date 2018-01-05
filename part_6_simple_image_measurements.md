# PART 6: SIMPLE IMAGE MEASUREMENTS {#part-9-simple-image-measurements}

Many of the simple FIJI functions that you have previously learnt about can be combined with other tools for more complex processes to analyse and measure your data. Here, our instructions become more speicified as wel go through several examples of common measurements using the different tools in FIJI.

In this section we use the images **RGB-blue, RGB-green, Nuclei-1** and **MovieStack** for demonstration.

## Area Measurements {#area-measurements}

To make a simple measure of the stained area, we first want to threshold the image. Without a threshold, the program would give an area measurement for the entire image, rather than just the stained area. We will use a threshold here, but you can also select a specific area to measure by using an ROI.

Open the image **Nuclei-1**, and go to **Image -&gt; Adjust -&gt; Threshold**.

Fit your threshold to the data as best as possible.

Click **Apply**, or generate mask as previously described.

We now have a mask for the nuclei in this image but there are a few blemishes that may affect the measurement. You can see below we have some areas detected outside the nuclei, as well as some spots within the nuclei that are not masked.

To fix this we are first going to **Fill Holes** in the mask using the binary tool. Go to **Process -&gt; Binary -&gt; Fill Holes**.

Then we will remove the small spots detected outside the nucleus using the **Remove Outliers** filter. Go to **Process -&gt; Noise -&gt; Remove Outliers**. Turn on the preview and set a pixel radius that captures all spots outside the nuclei and the click **OK** to apply the filter.

![](/assets/part9/remove_outliers_options.jpg)

You should now have a mask that nicely represents the nuclei in the original image.

![](/assets/part9/result_filtered_binary_image.jpg)

To measure the area you first need to set your output parameters. Go to **Analyse -&gt; Set Measurements**.

![](/assets/part9/set_measurements_menu.jpg)

In the **Set Measurements** window you can choose what you want to measure by clicking on or off the checkboxes beside different parameters.

![](/assets/part9/set_measurements_options.jpg)

Here we will turn on **Area** only.

Ensure you have **Limit to threshold** selected, or the program will measure the entire image, not just the masked areas.

Select **OK** to save the output parameters.

To measure the area of the nuclei using the parameters you have just set go to **Analyze -&gt; Measure** \(or shortcut Ctrl+M\).

![](/assets/part9/measure_menu.jpg)

This will give you a results table with the area of the nuclei.

![](/assets/part9/measure_results_table.jpg)

You will notice there is only one measurement. This is because this method measures the mask as a whole.

## Mean Intensity Measurements {#mean-intensity-measurements}

To generate a basic intensity measurement we apply a similar method as the basic area measurement. Although, even with the output parameters set to **Limit to threshold**, if we try to measure a mask we will only get intensity readings on the pixel intensity values within the mask itself, not in the image. Meaning all values will be shown as 255, the upper limit of the mask.

![](/assets/part9/results_table_measurements_BEFORE.jpg)

Therefore, for intensity measurements, we need to measure the image before turning it into a mask. To do this, open your image and repeat your thresholding. Go to **Image -&gt; Adjust Threshold**. Find the threshold to best fit the data. But this time DO NOT press apply!

Leaving the threshold window open, without applying the mask, go to the **Analyze** window and set your measurements as before.

![](/assets/part9/set_measurements_options_limit_to_threshold.jpg)

This time we want to set **Area, Min & max gray value, Integrated density** and **Mean gray value**.

Again ensure the checkbox next to **Limit to threshold** is selected.

Select **OK** to save the changes.

Repeat the measurement process as before. Go to **Analyze -&gt; Measure** \(or shortcut Ctrl+M\).

This will give you a measurement for the intensity in the original image, limited to the area under the threshold you have set.

![](/assets/part9/results_table_measurements_AFTER.jpg)

## Intensity Map \(Rainbow RGB LUT\) {#intensity-map-rainbow-rgb-lut}

For a visual representation of the intensity, you can map the intensities across the image very simply using a LUT.

Open your image and go to **Image -&gt; Look up Tables**, and select the LUT **Rainbow RGB** from the bottom of the list \(or select the Rainbow LUT form the LUT menu in the tool bar\).

This will apply a multi-coloured LUT to your image, in shades of red, blue or green. The highest 33% of intensities are reds, the middle 33% are greens and the bottom 33% are blues. This gives the viewer the ability to easily see the range of intensities present in the image.

![](/assets/part9/lookup_table_rainbow_menu.jpg) ![](/assets/part9/lookup_table_rainbow_result.jpg)

You can add a calibration bar for the intensities by going to **Analyze -&gt; Tools -&gt; Calibration Bar**.

![](/assets/part9/calibration_bar_menu.jpg)  ![](/assets/part9/calibration_bar_options.jpg)

In the **Calibration Bar** window you can specify the position and configuration of the calibration bar. The **Overlay** tick box allows you to create the bar as an overlay of the original image, instead of burning it into the image permanently.

Click **OK** to add the calibration bar to your image.

![](/assets/part9/calibration_bar_result.jpg)

## Simple Counting {#simple-counting}

Often we want to know how many cells or object we have in an image. For a low number of objects you can easily count using the multi-point tool.

Open your image and select the multi-point tool from the FIJI tool bar.

![](/assets/part9/count_cells_point_tool.jpg)

Right click the tool and open the **Point Tool** options window. Set up your points as you want them to appear on your image. Ensure **Label Points** and **Show All** are selected. Leave the window open.

![](/assets/part9/count_points_options.jpg)

Return to your image and click once on every object you want to count. A point will appear on the image for each click. As you click you will see a counter increasing at the bottom of the **Points Tool** window. Once you have clicked on all of your objects, the final number will be your object count. Each object will also be marked in the image as a check of whether you correctly counted the object.

![](/assets/part9/count_cells_point_tool_results.jpg)

## Analyse Particles {#analyse-particles}

For an image with a large number of objects manually clicking to count can be a laborious task. For these images you can use the **Analyze Particles** tool.

To use this tool, you first need to threshold your image as previously shown. Select a threshold that fits your data then click **Apply** to create a mask.

![](/assets/part9/threshold_options.jpg)

You will see several issues with this mask; gaps within the nuclei and small particles detected outside the nuclei. For counting these small particles can be problematic as they will be counted as an object, when they are in fact a false positive.

To remove these errors, apply the **Fill Holes** and **Remove Outliers** tools to the mask. This will give a mask covering the objects to be counted.

![](/assets/part9/threshold_mask_result.jpg)

There is one problem remaining that will result in a false count with this mask. In several areas, nuclei were touching resulting in them being masked as a single object. To separate these we need to apply a **Watershed** binary filter to the mask. Select this from the **Analyze -&gt; Binary** menu as previously described to separate touching objects.

![](/assets/part9/threshold_watershed_result.jpg)

Now that we have an appropriate mask for the data we can count our objects using **Analyze Particles**. Find this under the **Analyze** menu.

![](/assets/part9/analyze_particles_menu.jpg)

In the resulting window, leave **Size** and **Circularity** at their default values. Set **Show:** to **Outlines** and tick the boxes as below. Press **OK** to measure the objects.

![](/assets/part9/analyze_particles_options.jpg)

The results, including count, area and size, are shown in the table and counted objects are shown in the outline image.

![](/assets/part9/analyze_particles_result.jpg)

Outliers are still visible in the outlines image. You can go back and alter the size to remove these smaller objects and remeasure for more accurate results.

## Manual Tracking {#manual-tracking}

We can get several pieces of information from time series by tracking the objects over time. The simple method for tracking objects over time is to manually track them using the **Manual Tracking** tool.

Open your time series and then open the **Manual Tracking** tool from the menu **Analyze -&gt; Tracking**.

![](/assets/part9/tracking_menu.jpg)

![](/assets/part9/tracking_options.jpg)

In the **Tracking** window set your parameters, including **Time Interval** \(5mins for this example\).

If the xy calibration \(scale\) is not set automatically, enter the calibration value too.

Select the option to show the tracks on the image if required by checking the box next to **Show path?**

When you have set your parameters, click **Add Track** to start your first track.

If you make a mistake during tracking you can **Delete the last point** or **Delete track** and select the track number to remove it entirely.

To begin tracking, after selecting **Add track** click on the image in the centre of the object you want to track. The series will automatically move to the next frame. Click the centre of the object again.

Continue until you have reached the end of the series. If you have selected an option to show the track it will be visible overlayed in the image as a yellow segmented line. Measurements for the object will be displayed in a results table.

![](/assets/part9/tracking_result.jpg)

Measurements will be displayed separately for each time point, these can be exported to excel and averaged.

Note: the first measurements will not be accurate as the object has not moved yet \(ie: first measurement for distance is -1\) and these should be removed before averaging.

## Overlay Masks {#overlay-masks}

Masks generated on one image can also be used to make measurements on another image. This allows you to measure the same area in different channels or images.

The easiest method for applying your mask to a different image during measurement is to redirect.

Generate a mask for your first image and make any measurements you require. Once that is complete, open your second image. Click on the mask again then go to **Analyze -&gt; Set Measurements**.

In the **Set Measurements** window, select the measurement criteria, if different from the previous, then select your second image from the drop down menu under **Redirect to:**.

![](/assets/part9/set_measurements_redirect_option.jpg)

Click **OK** to perform the measurements on the second image. You will now get measurement for the second image in the areas under the original mask.

![](/assets/part9/set_measurements_results_table.jpg)

## Masks to ROIs {#masks-to-rois}

To get individual measurements for areas in a mask, generate your mask as required then go to **Analyze -&gt; Anylze Particles**. This time in the **Analyze particles** window, tick off every options box except **Add to Manager**. Select **OK**.

![](/assets/part9/analyze_particles_options_add_rois_to_manager.jpg)

The mask will be converted to ROIs in the ROI manager.

![](/assets/part9/analyze_particles_result_rois_in_manager.jpg)

You can now use this to make multiple measurements on your original image. Set your measurements and then click on **Measure** in the ROI manager. Note that for intensity measurements you should apply the ROIs or redirect to the original image as intensity can’t be measured in a mask.

To apply the ROIs to another image, select your second image and go to **Image -&gt; Overlay -&gt; From ROI Manager**.

![](/assets/part9/overlay_roi_manager_menu.jpg)

The ROIs generated from the mask will be applied to the second image and you can now set your measurements for the second image and measure the same area.

![](/assets/part9/overlay_roi_manager_result.jpg)

![](/assets/part9/overlay_roi_manager_results_table.jpg)


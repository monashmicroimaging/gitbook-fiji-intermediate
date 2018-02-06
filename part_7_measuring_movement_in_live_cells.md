## PART 7: MEASURING MOVEMENT IN LIVE CELLS {#manual-tracking}

When we capture cells over time, also known as times series or live cell imaging, we are presented with more analysis options. along with the other types of analysis presented above, we can also get several pieces of information from time series by tracking objects over time or exmining the dynamics of the cells or their organelles.

In this section we will show you two different methods for tracking objects in time series, as well as how to present the dynamics of a cellular component in a single imge \(known as a kymograph\). We will use the images **MovieStack.tif**, **Track.tif **and **Kymograph.tif **for demonstration.

## Manual Tracking

The simple method for tracking objects over time is to manually track them using the **Manual Tracking** tool.

Open the time series **MovieStack.tif **and then open the **Manual Tracking** tool from the menu **Plugins -&gt; Tracking**. 

![](/assets/part 7/Manual tracking 1 - menu.jpg)

In the **Tracking** window, tick on **Show Parameters?** to see and set all calibration settings. You can then set your parameters, including **Time Interval** \(5mins for this example\). If the xy calibration \(scale\) is not set automatically, enter the calibration value too \(in this example it is automatically set correctly\).

Select the option to show the tracks on the image if required by checking the box next to **Show path?**

![](/assets/part 7/Manual tracking 2 - options.jpg)

When you have set your parameters, click **Add Track** to start your first track. 

![](/assets/part 7/Manual tracking 3 - add track.jpg)

Then to begin tracking, click on the image in the centre of the object you want to track. The series will automatically move to the next frame. Click the centre of the object again.

Continue until you have reached the end of the series. If you have selected an option to show the track it will be visible overlayed in the image as a yellow segmented line. Measurements for the object will be displayed in a results table. 

Measurements will be displayed separately for each time point, these can be exported to excel and averaged.

Note 1: results are cumulative. You can check the "track number" column in the results to see which results belong to which track, or save and then clear results between each cell or each image to ensure you know which results belong to which cell. 

Note 2: the first measurements will not be accurate as the object has not moved yet \(ie: first measurement for distance is -1\) and these should be removed before averaging.

![](/assets/part 7/Manual tracking 4 - track.jpg)

Repeat the process above \(from **Add track**\) for each cell you want to track in the image. Generally we would avoid tracking cells that divide, leave or enter the field of view, or cross paths \(especially if you are unable to determine which cell is which once they separate again\).

If you make a mistake during tracking you can **Delete the last point** \(1 below\) or select the track number from the drop down list and click on **Delete track **\(2 below\) to remove it entirely.

![](/assets/part 7/Manual tracking 5 - delete options.jpg)

## TrackMate: Automated Live Cell Tracking {#trackmate-automated-live-cell-tracking}

Open **Track.tif** in Fiji. Go to Plugins&gt;Tracking&gt;TrackMate. This opens the TrackMate window. In the first window, you can set the scale of your image \(should be pre-filled if your image is scaled correctly\) and a region of interest if you only want to analyse part of your image. We want to analyse the whole image, so just click next.

There’s different methods of detecting cells, the most common ones are LoG \(Laplacian of Gaussian\) and DoG \(Difference of Gaussian\). Basically, it uses two different Gaussian filters, one slightly wider than the other one, and subtracts the two images to result a sharper image without background. Similar to what we did before in the Flattening paragraph.

![](/assets/part4/trackmate.jpg)

Choose DoG detector and enter the expected size of your cells and a threshold. Here, please enter Diameter 10 micron and Threshold 30. Press preview and see which signal it detects. Scroll through time, press preview at several different time points and make sure the threshold is set correctly so that all cells but no random background signal gets picked up. Just for fun, change diameter and threshold to see how it changes the detection of cells. But Diameter 10 micron and Threshold 30 are good settings for this data set, so go back to those before pressing ‘Next’. The software will now

analyse all images of the time series and detect all cells with the given parameters. Once the detection is finished, press ‘Next’ again. Now there’s options to filter out cells according to their quality. For this data set, we’ll ignore this filter and press ‘Next’. Another set of filter options will come up. Click on the green plus button; in the drop-down menu you can see which filters you can choose: quality, radius, intensity and many more. You can add several filters by pressing the green plus button again and choose a different filter and the corresponding threshold. For this data set, we’re again going to ignore these filters. So remove any filters by pressing the red minus button and press next.

Now we’re at the tracking options. Choose LAP \(Linear Assignment Problem\) tracker from the drop- down menu. All the options are different algorithms on how to connect the detected spots. Descriptions of the algorithm and how they work are given in TrackMate below the selected algorithm.

Simple LAP Tracker is a simplified version of the LAP Tracker and will work well in most cases. Here, we want to use penalties, so we need to choose the LAP Tracker. In the next window, you can set distances on how far you expect your cells to travel per frame.

Try the following options:

1. Frame to frame linking: 10um, Gap closing: 10um  
   You will see that some tracks are broken up into several tracks as the cells moved more than 10um between frames.  
   ![](/assets/part4/trackmate_1.jpg)

2. Frame to frame linking: 50um, Gap closing: 20um.  
   You will see that the tracks are now better connected but there’s also many wrong connections in y direction.  
   ![](/assets/part4/trackmate_2.jpg)

3. Now we’re going to apply penalties, as this is a flow experiment, cells are more likely to be found at longer distances in x \(with flow\) than in y. Try; Frame to frame linking: 50um, Penalty Y: 40um, Gap closing: 20um. You will see that all tracks are now well connected.  
   ![](/assets/part4/trackmate_3.jpg)

As always, you will have to find the right settings for your experiment. In the next step, you can filter tracks, similar to the spot selection filters before. This time, we’re going to use it: press on the green plus button. Check the drop-down menu for options available. Add a filter ‘Number of spots in track’ and set the filter between 2 and 3 so that we only get cells that appear in more than two frames. This leaves us with 106 out of 132 tracks.

![](/assets/part4/trackmate_options.jpg)

Now we’re ready to export the results of our analysis. Press ‘Next’ and then press the ‘Analysis’ button. This will open tables with all the information on all your detected tracks and spots. You can save those as .csv and open in Excel or Prism for further analysis. Check out the Track Statistics window now: We have 106 tracks listed and get information such as duration, displacement, and speed on each of the tracks.

## Kymographs {#kymographs}

Kymographs are a way to represent a dynamic process as a single image. They are particularly useful to monitor and characterize the movement of a cell or organelle. They can be seen as an _x-t_ scan, where the intensity along a given line is plotted for all images of a stack. Each time point gives an intensity line, plotted _e.g._ along the x axis of the kymograph. These lines are stacked along the y axis for all frames. So we get an image where we move through space in the x direction and time in the y direction.

Open **Kymograph.tif **and draw a line across one of the cells that stay in the same area for the whole time series.

![](/assets/part4/kymograph_image.jpg)

Go to Image&gt;Stacks&gt;Reslice and press **OK**.

![](/assets/part4/kmograph_result.jpg)

The resulting image displays space on the x-axis, an intensity profile across the cells in brightfield and fluorescence. Time is displayed on the y-axis \(top: start, bottom: end\), you can see the green fluorescence intensity increase over time and the cell move left and right in the brightfield image.


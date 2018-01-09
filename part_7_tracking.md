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


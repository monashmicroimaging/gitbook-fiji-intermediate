## 3D Projections {#3d-projections}

When working with z-stacks, you can create a 3D projection of the stack by going to **Image -&gt; Stacks -&gt; 3D Project**.

![](/assets/part7/3d_project_menu.jpg)

For most 3D projections you can leave the settings in the **3D Projection** window as default.

If you check the box next to **Interpolate**, FIJI will guess at the image information between slices. While this helps to create a smooth projection it is adding information that is not in the original image. For quantitation this should be avoided, for presentation of your 3D projection you can use it.

If the image is calibrated the **Slice spacing** should be populated correctly from the metadata. Note that this uses the z-step size, not the m/px calibration size.

![](/assets/part7/3d_project_options.jpg)

Select **OK** to create the projection.

The resulting projection will have a slider at the bottom \(similar to a stack\) which you can use to rotate the 3D image.

![](/assets/part7/3d_project_result.jpg)

## Orthogonal Views {#orthogonal-views}

An orthogonal projection is a view created in the YZ or XZ dimension of an image stack. An orthogonal projection allows you to visualise depth information one slice at a time in your sample.

To generate orthogonal slices select your z-stack and go to **Image -&gt; Stack -&gt; Orthogonal View** \(or use shortcut Ctrl+Shift+H\).

![](/assets/part7/orthogonal_views_menu.jpg)

Two windows will open to the right of and below the original stack. These windows show the orthogonal projections in YZ and XZ respectively.

![](/assets/part7/orthogonal_views_window.jpg)

To change the view seen in each window, move the yellow cross hair in the original stack and scroll through the stack to change plans as usual. Each of these projections can be saved for use later.

## Reslice Z {#reslice-z}

The orthogonal projection only lets you see one slice at a time and it has the overlay lines in the way. Sometimes it can be useful to generate a stack of orthogonal slices instead. This is easily achieved by reslicing the stack along a different axis.

To generate an orthogonal stack go to **Image -&gt; Stacks -&gt; Reslice.**

![](/assets/part7/reslice_menu.jpg)

In the window that opens you can set how the stack should be resliced \(top, bottom, left, right\) from the drop down menu and, if not already calibrated, set the distance between slices.

There is a tick box to select that says **Avoid Interpolation**. This should usually be ticked. As with the 3D projection, while interpolation will make the end result look better, it does this by adding extra data that wasn’t in the original image.

Select **OK** to generate the resliced stack.

![](/assets/part7/reslice_options.jpg)

The program will then ‘scan’ through the image from the selected direction and generate the new stack.

![](/assets/part7/reslice_result.jpg)

## Times Series and Saving Movies {#times-series-and-saving-movies}

Time series will also open as a stack that you can work with in a similar manner to colour or z-series stacks.

![](/assets/part7/time_series.jpg)

Here, the slider or play button move through the time points, rather than the channels or z-slices.

You can save your time series as a movie using FIJI by selecting **File -&gt; Save As**, and choosing **AVI **as the file type.

![](/assets/part7/save_movie_menu.jpg)

A window with saving options will open, which will allow you to set specific aspects of the movie.

![](/assets/part7/save_movie_options.jpg)

Where possible you should create your movie without compression. The frame rate will be dependent on your images and time interval. Sometimes a trial an error of different frame rates will be needed to generate a movie that plays at an appropriate speed. Generally, something around 8 frames per second \(fps\) is a good starting point.

![](/assets/part7/save_movie_8fps.jpg)

Click **OK** to create and save the movie.

The movie will not open and play automatically. You can open and play the movie file in programs QuickTime, Windows media Player or VCL Media Player to check the frame rate.

![](/assets/part7/save_movie_file_icon.jpg)

![](/assets/part7/save_movie_result.jpg)

Before saving your movie you can also include add a time stamp using FIJI. To add a time stamp, select your time series stack and go to **Image -&gt; Stack -&gt; Time Stamper**.

![](/assets/part7/time_stamp_menu.jpg)

In the **Time Stamper** window you will need to enter the interval between images and the format you want the time stamp to be in. You can also specify the location in pixels.

In this example, the time interval is 5mins. Time needs to be entered in seconds in the options, so you would need to put ‘300’ into the interval box. Pixels for an approximate location can be found by hovering the mouse over the area of the image you wish to use. Pixel co-ordinates will be displayed in the information bar.

You can also choose to include a suffix \(sec, min, etc\) or use the time format ‘00:00’.

![](/assets/part7/time_stamp_options.jpg)

Select **OK** to insert the time stamp into the stack. The timer will automatically run as you scroll through the stack.

![](/assets/part7/time_stamp_result.jpg)

You can now save your time series as a movie, using the same method as above, and the time stamp will remain embedded.

## Hyperstacks {#hyperstacks}

Often images will be captured with a 4th or 5th dimension; that is they will have a combination of multiple channels, z-sections and time. For these images the data will be presented as a hyperstack.

Each stack is presented independently with its own navigation bar, within a single window.

![](/assets/part7/hyperstack.jpg)

You can scroll through each dimension independently, you can also use the same tools to alter and navigate the stack as above \(ie: delete slice\), but you will be asked which dimension you want to alter.

![](/assets/part7/hyperstack_delete.jpg)

You can also use hyperstack tools to reduce dimensionality. To find these go to **Image -&gt; Hyperstack**.

![](/assets/part7/myperstack_menu.jpg)

**Hyperstack to Stack** will combine all dimensions into a single stack with c\_z\_t frames \(ie; here 61 z- planes \* 25 time points = 1525 frames\).

![](/assets/part7/hyperstack_to_stack.jpg)

**Reduce Dimensionality** will allow you to pick one dimension to remove or keep in the hyperstack.

![](/assets/part7/hyperstack_reduce_dimensionality.jpg)

For example you can select time only \(by un-checking the box beside 61 slices\) and a single stack of all time points at the current z-plane will be generated.

![](/assets/part7/hyperstack_reduce_dimensionality_result.jpg)


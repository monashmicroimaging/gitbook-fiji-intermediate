## PART 8: MORPHOLOGY MEASUREMENTS {#morphology-changes}

Some of the basic analysis tools we have already used can also be adapted to give us more detailed information about the data we are analysing. For example, we previously used the **Analyse Particles** tool to count nuclei. You can use the same tool for analysing the morphology of your cells.

In this section we use the image  for demonstration.



## Morphology Changes



Under Analyse&gt;Set measurements select Area, Perimeter, Skewness, and Kurtosis. Open

_**Morphology.tif**_, duplicate, autothreshold and binarize the image.

Make sure, ROI Manager is empty then run Analyse Particles on the binary image. You will get one ROI that outlines the cell, the results window shows you the perimeter of the cell.

![](/assets/part4/morphology_changes.jpg)

Now select the original image and press ‘Measure’ in the ROI Manager. You will get a second results line that gives you Skewness and Kurtosis of the cell.

![](/assets/part4/morphology_changes_result.jpg)

Skewness and Kurtosis provide information on the intensity distribution within the cell. **Skewness** is a measure of symmetry, or more precisely, the lack of symmetry. A distribution, or data set, is symmetric if it looks the same to the left and right of the centre point. **Kurtosis** is a measure of whether the data are heavy-tailed or light-tailed relative to a normal distribution.

![](/assets/part4/skewness_and_kurtosis.jpg)

Now select the cell ROI in the ROI Manger and go to Edit&gt;Selection&gt;Convex Hull. This will draw a closed circumference around the ROI.

Go to Analyse&gt;Measure, this will give you a third line in the results window with the perimeter of the convex hull.

![](/assets/part4/convex_hull.jpg)

The ratio between convex hull perimeter and cell ROI perimeter is a measure of the sphericity or ‘spikiness’ of the cell. If the ratio is close to 1 then the cell is almost spherical, the closer the ratio goes towards zero, the spikier the cell.

If you have a time series of images, you can look at morphology changes over time with these methods.


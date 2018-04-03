## PART 8: MORPHOLOGY MEASUREMENTS {#morphology-changes}

Some of the basic analysis tools we have already used can also be adapted to give us more detailed information about the data we are analysing. For example, we previously used the **Analyse Particles** tool to count nuclei. You can use the same tool for analysing the morphology of your cells.

In this section we use the image **Morphology.tif** for demonstration.

## Morphology Changes

Open the demo image, _**Morphology.tif.**_ Duplicate it, then set a treshold and create a binary of the image. Here I have used the Huang algorithm set at 12 and 255. Following binary creation I have used the 'fill holes', 'despeckle' and 'remove outliers' filters to clean up the binary.



Under **Analyze -&gt; Set Measurments** select Area, Perimeter, Skewness and Kurtois and click **OK.**



Open the ROI Manager and check it is empty then run Analyse Particles on the binary image. You will get one ROI that outlines the cell, the results window shows you the perimeter of the cell.



Now select the original image and press ‘Measure’ in the ROI Manager. You will get a second results line that gives you Skewness and Kurtosis of the cell.



Skewness and Kurtosis provide information on the intensity distribution within the cell. **Skewness** is a measure of symmetry, or more precisely, the lack of symmetry. A distribution, or data set, is symmetric if it looks the same to the left and right of the centre point. **Kurtosis** is a measure of whether the data are heavy-tailed or light-tailed relative to a normal distribution.



Now select the cell ROI in the ROI Manger and go to Edit&gt;Selection&gt;Convex Hull. This will draw a closed circumference around the ROI.

Go to Analyse&gt;Measure, this will give you a third line in the results window with the perimeter of the convex hull.



The ratio between convex hull perimeter and cell ROI perimeter is a measure of the sphericity or ‘spikiness’ of the cell. If the ratio is close to 1 then the cell is almost spherical, the closer the ratio goes towards zero, the spikier the cell.

If you have a time series of images, you can look at morphology changes over time with these methods.


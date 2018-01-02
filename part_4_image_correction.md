# PART 4: IMAGE CORRECTION {#part-2-image-correction}

There are a number of tools in FIJI that can be useful for advanced correction of your images and image series. In this section we will go through the different tools available for correcting imaging artefacts and flaws. The images used for demonstration purposes are given in each sub-section.

## Flatten {#flatten}

Sometimes, your image might have an uneven background that hinders image analysis because you can’t threshold your features of interest without also thresholding some of the background. Flattening the image can help with that.

Open the image \_**Dapi – uneven.tif. **As shown in previous workshops/sections, duplicate the image and then apply a large Gaussian blur \(e.g. radius 20\) to the duplicated image.

![](/assets/part 4/Flatten 1 - blur duplicate b.JPG)

Using the image calculator described in Part 3 of this manual \(**Process -&gt; Image Calculator**\) and subtract the blurred image 9image 2\) from the original image \(image 1\).

![](/assets/part 4/Flatten 2 - image calculator b.jpg)

This results in a flattened image which will now be easier to threshold accurately.

![](/assets/part 4/Flatten 3 - result.JPG)

![](/assets/part 4/Flatten 4 - threshold comparisons b.JPG)

Note:** **there is also a background subtraction in \(**Process -&gt; Subtract Background**\) which will remove even background but won’t help with uneven background and consequent thresholding issues.

## Bleach Correction {#bleach-correction}

Open the demonstration image _**Dapi – time.tif**_** **and go to **Image -&gt; Adjust -&gt; Bleach Correction**.

![](/assets/part 4/Bleach Correction 1 - menu.jpg)

Choose **Histogram Matching** from the drop down menu in the pop-up window and then click **OK**.

![](/assets/part 4/Bleach Correction 2 - options.jpg)

There is other options that you can try \(Simple Ratio and Exponential Fit\) which are quicker but in our experience don’t work as well. Have a try with your images and see which one works best for your data.

FIJI will display a log displaying the progress as each frame is corrected.

![](/assets/part 4/Bleach Correction 3 - Log.JPG)

A new window will open with your result when the correction is completed. \(Here I have duplicated the final frame to demonstrate he difference between the original and corrected image\)

![](/assets/part 4/Bleach Correction 4 - comparison.JPG)

## Image Registration / Drift Correction {#image-registration-drift-correction}

Correction of image shifts or drift during imaging requires installation of two stack registration plugins. If you have not already done this, do so now by Googling ‘StackReg FIJI’ and ‘TurboReg FIJI’ and download both plugins. They will appear as .zip files. Unzip both files and then move the .jar file into the plugins folder of your FIJI software and restart FIJI. 

Once you have the plugins installed, open _**Spheroid – shift.tif**_** **and scroll through the stack. You will see that the image shifts \(the spheriod makes a sudden jump to the left\) at frame 51. 

![](/assets/part 4/Registration 1 - frame shift.JPG)

Go to **Plugins -&gt; StackReg**. 

![](/assets/part 4/Registration 2 - menu.JPG)

Select **RigidBody** from the drop down menu next to **Transformation** in the pop up boxin the pop-up window, then click **OK**. 

![](/assets/part 4/Registration 3 - options.JPG)

**NOTE:** There are four selections for the type of transformation.

**Translation:** Will move planes in X and Y

**Rigid Body:** Will move planes in X and Y as well as rotate \(most often provides the best correction without image distortion\)

**Scaled Rotation:** Same as rigid body but will scale/zoom planes as well

**Affine:** Same as scaled rotation but can also deform images into trapezoid shapes



FIJI will move through the stack as it corrects for the unwanted movements. Results will display in the original image window. For this reason it can be useful to work with a duplicate in case the first correction is not acceptable.

This plugin can be used in the same way for drift correction over time.

## Image Deconvolution {#image-deconvolution}

Deconvolution is a mathematical process that takes into account the shape of the laser focus \(point spread function or PSF\) and uses that to remove out-of-focus light from the image thus improving resolution and signal-to-noise ratio.

The PSF can easily be recorded on a microscope by imaging 100nm fluorescent beads and used for the deconvolution in FIJI.

Open _**Malaria.tif**_** **and _**PSF.tif**_. Scroll through the PSF file to see what it looks like. It’s a z-stack of a fluorescent bead.

Download Iterative\_Deconvolve\_3D.class from [http://imagej.net/Iterative\_Deconvolve\_3D](http://imagej.net/Iterative_Deconvolve_3D) if you have not already done so.

Copy Iterative\_Deconvolve\_3D.class into your Fiji Plugins folder, go to Plugins &gt; Iterative Deconvolve 3D. Select Malaria.tif under Image and PSF.tif under Point Spread Function, then select number of iterations \(try 10 and 100 and compare the resulting images\), press ok, wait and save image when deconvolution is finished.

![](/assets/part2/deconvolution_options.jpg)

![](/assets/part2/deconvolution.jpg)


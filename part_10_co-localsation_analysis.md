## Co-localisation Analysis {#co-localisation-analysis}

This workshop will concentrate on two different algorithms to calculate co-localization: Manders and Pearsons.

### Manders…

…thresholds both images and calculates how many pixels above threshold in channel 1 are also above threshold in channel 2 and vice versa. You get two Manders coefficients, one for channel 1 and one for channel 2. Values will range between 1, for complete co-localization i.e. all channel 1 pixels above threshold are also above threshold in channel 2, and 0, for no co-localization i.e. no channel 1 pixels above threshold are above threshold in channel 2.

### Pearsons…

…takes into account the fluorescence intensity of each pixel. If all bright pixels in channel 1 are also bright in channel 2, and all dim pixels in channel 1 are also dim in channel 2 then the Pearsons coefficient is 1. If there’s no co-localization, i.e. fluorescence intensities are randomly distributed in channel 1 and 2, then the Pearsons coefficient is 0. The two channels can also be anti-correlated, which means that all bright pixels in channel 1 are dim in channel 2, and vice versa. In other words, where there’s green signal, there is no red signal. In this case, the Pearsons coefficient is -1. Pearsons co-localization does not require thresholding and is therefore more robust than Manders. It also provides you with more information as fluorescence intensity is being taken into account and you get information on anti-correlation.

Open _**Co-localization.tif**_** **and split channels. Duplicate the red channel and autothreshold and binarize the duplicated image to separate cells from background. Go to Analyze&gt;Colocalization&gt;Coloc2. Choose the red image as channel 1, the green image as channel 2, and the binary image as mask. Coloc2 will use autothresholding \(Costes method\) to calculate the Manders coefficients so no need for us to threshold the images. Tick the following boxes:

![](/assets/part4/colocalization_options.jpg)

And press ‘Ok’. After some calculation time, we get the following results:

![](/assets/part4/colocalization_results.jpg)

Let’s try to understand these values. Manders coefficients without thresholds is 1. That will be the case for almost all images and just means that there is some kind of signal in all pixles. Not useful!

Manders with thresholds is better: we have a Manders coefficient of 0.37 for the red channel and 0.41 for the green channel. That means that inside the mask, 37% of the red pixels are also green, 41% of the green pixels are also red, which makes sense when you look at the images.

Pearsons coefficient without threshold is 0.71, which means the signal in both channels is correlated, the above and below values are not really crucial, but a nice control. Above threshold is also correlated, while below threshold is randomly distributed.

The scatter plot shows fluorescence intensity of one channel on the x-axis and fluorescence intensity of the other channel on the y-axis. Correlated or co-localized signal will show up along the white line.000000


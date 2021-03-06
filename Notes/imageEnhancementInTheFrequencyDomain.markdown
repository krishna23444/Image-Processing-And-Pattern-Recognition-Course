# Image Enhancement in the Frequency Domain

Recall : The purpose of image enhancement is to improve the 
interpretability or precision of information in images for 
human viewers and providing better input for other image processing
and image processing vision techniques. 

This is achieved by changing the attributes of images to make them 
more suitable for a given task.

Image enhancement doesn't increase the amount of data in an image, it 
just changes the dynamic range of the chosen feature so they 
can be detected easily.

We already talked about image enhancement in the spatial domain. Today 
we will be talking about image enhancement in the **frequency domain**. 
This is mostly done using the **fourier transform**.

There is no "general theory" to determine what a good image is when 
judged by humans. The rule of thumb is : if it looks good, it is good.

However, when we use image enhancement as preprocessing for other image
processing or computer vision techniques, there are quantitative techniques
to find out of the image is good. An example of this is histograms
to determine if the contrast is suitable or not.

In Frequency domain images, The image is first transferred into the 
frequency domain. This means we take the fourier transform of the image first, 
do operations on that, then we perform the **inverse** fourier transform
to get the resultant image.

These methods enhance the image by performing a convolution operation on the image with a linear,
position invariant operator --> this means that the image will have the 
same signature regardless of the position of the pixels in the image. They
modify the distribution of the gray-level values. As a consequence, 
the values of the pixels in the image change. It is important to know that **It is 
possible for 2 images to have the same signature in the frequency domain**

The Pixel values of the input image will be changed according to the transformation
function applied. For an image F and output G This is given by  :

> s = T\(r\)

where r and s represent the pixels in F and G respectively.

The process is as follows :

> F(x,y) --> preprocessing(normalization) --> Fourier Transform --> Filter function --> Inverse Fourier Transform --> Post-Processing --> G(x,y)

Alternatively, we can do this directly 

> G(u,v) = H(u,v)F(u,v) 

where H is the transfer function of the image.

Using the frequency domain allows us to capture properties that are 
not present in the spatial representation of the image, mainly the
shape and texture of the image. 

We also use the frequency domain because 
It is computationally faster to apply filters in the frequency domain.
This is particularly useful for larger filters. 


## Definition of frequency

Frequency is formally defined as:

> The number of times in a specified period that a 
> phenomenon occurs within a specified interval.


## The Fourier Transformation

The basic principle is that any equation that repeats itself can 
be expressed by the sum of sines and cosines in various frequencies.

Essentially, its the sum of the different periods of a periodic function expressed
as multiple sines.

For example, Here is a Fourier transform for a sound wave:

![fourier drawing](http://hearinghealthmatters.org/waynesworld/files/2012/06/Fourier-Analysis.gif)

The more terms there are to the Fourier function(series), the closer the approximation 
of the original function(since we rarely get a perfectly periodic wave).

An image that has had the fourier transform applied to it is represented
as the variation of its colors and brightness. 

It is important to know that 2 images can have the same fourier transformations. This
might happen if they contain the same objects. 

Because the fourier transform tells us what is happening in an image,
It is often convenient to describe image processing operations to describe
what happens to the frequencies in the image. For example, eliminating 
low frequencies gives us edges. eliminating high frequencies blurs the 
image. 

There are many applications for Fourier Transform Image processing, some 
of them include :

- Feature Extraction
- Image Filter
- Image Compression

## Discrete fourier transform 

A Discrete Fourier transform is calculated over a sample window of samples.
Calculating A DFT assumes that the image is repeated horizontally and 
vertically since it is a continuous signal.

To counteract this, we can do **windowing**, which is a function applied
to the edges of the image before the DFT to reduce sharp 
transitions between the edges of the image.


## The Fast Fourier Transform

The Fast Fourier Transform is extensively used in image processing and computer vision. 
It is faster than a regular fourier transform. It is a type of Discrete
Fourier Transform. The Wiener Filter, used for blurring, is defined in terms of
the fourier transform.


**TODO INSERT Function**

Instead of an integral, we now have a finite sum.

The FFT can be computed by dividing the original vector, calculating the FFT for each part recursively,
and joining them together.

## 2D Fourier Transform 

It is essentially the wighted sums of sines and cosines in 2 dimensions.

## Centering Signals

After doing a DFT, the resultant transformation might not have the
things we are interested in at the centre. In that case, we can 
shift the Fourier Transform, resulting in a change of where
the frequencies are to make it easier to understand.

Centering effectively swaps the 4 quadrants of the image diagonally.

## Displaying Transformations 

As elements are complex numbers, we can view the magnitudes directly. 
Displaying the magnitudes of Fourier transforms is called spectrum 
of the transform. Often, we have to apply a log transformation
on the spectrum so its more processable. 


## Image Filtering in the Frequency Domain

- Image Filtering is performed using signal filters.

- Low pass filters have a smoothing/blurring effect.
  - Ideal, Butterworth, Gaussian. 
  
- High pass filters have a sharpening effect.
  - Ideal, Butterworth, Gaussian. 
  

# Image Enhancement - Convolution

## Some Interesting things
Suppose we want to search for an object in an image. We can try to 
compare every pixel in the object with the image. This is a very 
expensive process, as we have to move the mask pixel by pixel. This 
is called **sliding window**, where we compare every pixel in the object we 
desire with the pixels in the image.

Another way we can do this is via **machine learning**. We create
a certain model based n the object we want to find and we have
the computer search for the object(or similar objects) in the image. 
This is known as **object recognition**. 

One way of doing this is to take the object, detect its edges, and 
create a vector of some sort and have the machine learning algorithm
search for a similar set of vectors within the image. this vector is
the signature of the object. 

## Sliding Windows

Assume that a matrix A is the image with dimensions(Ma,Na), and 
matrix B is the object with dimensions(Mb,Nb). The image
would be present where the subtraction of B from A is zero.

## Convolution

Convolution is multiplying 2 arrays of numbers to produce a third array
of numbers. This can be used to implement operations where the output
is simple linear vectors. 

Convolution is applied by sliding the **kernel** of the image. Each Kernel
position responds to a single output pixel. The value of which is equal
to the result of multiplying the section of the image by the kernel.

The equations related to convolution can be found 
[here](https://en.wikipedia.org/wiki/Convolution).

The kernel is usually a n*n matrix, where n is odd, and the multiplication 
is applied on an  n*n neighborhood around the pixel i.

The general equation is given by :

> C = A &otimes; B. 

where A is the image, B is the convolution kernel(mask/filter),and
the weights in B are the filter values.

2D convolution needs 2 loops, and is slow for larger kernels, so we
usually use smaller kernels.

If the sum of the elements in the kernel is bigger than 1, the image
will be brighter. else, it will be darker. We can do 
truncation or absolute values may be applied after the convolution.

Simply put, convolution is just applying filters.

if we have two three-by-three matrices, the first a kernel,
and the second an image piece, convolution is the process of flipping
both the rows and columns of the kernel and then multiplying locally
similar entries and summing. The element at coordinates \[2, 2\]
(that is, the central element) of the resulting image would be a
weighted combination of all the entries of the image matrix, with
weights given by the kernel.
 

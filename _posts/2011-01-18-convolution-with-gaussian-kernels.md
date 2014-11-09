---
layout: page
title: Convolution with Gaussian kernels
date: 2011-01-18 15:11:30.000000000 -05:00
category: course-material
topic: imaging
comments: false
description: In the case of *good enough* functions in real spaces, one is able to perform this operation by passing to the Fourier domain, multiplying, and coming back through the inverse Fourier transform.   In the setting of digital signals one can also profit from this principle, but by using instead the *discrete and inverse discrete Fourier transforms*.  With the aid of the `fft` algorithms to calculate the discrete Fourier transform, convolution via the frequency domain can be faster than directly convolving the time domain signals (`scipy.ndimage.convolve` in `sage`), and the final result is the same except maybe at the borders of the image.  Some care must be taken when producing the convolution this way, since zero-padding needs to be applied.

---

Recall the definition of <a href="http://blancosilva.wordpress.com/teaching/distributions/convolution-of-integrable-functions/">convolution of integrable functions</a>.  In the case of *good enough* functions in real spaces, one is able to perform this operation by passing to the Fourier domain, multiplying, and coming back through the inverse Fourier transform.   In the setting of digital signals one can also profit from this principle, but by using instead the *discrete and inverse discrete Fourier transforms*.  With the aid of the `fft` algorithms to calculate the discrete Fourier transform, convolution via the frequency domain can be faster than directly convolving the time domain signals (`scipy.ndimage.convolve` in `sage`), and the final result is the same except maybe at the borders of the image.  Some care must be taken when producing the convolution this way, since zero-padding needs to be applied.

The following example shows several ways to proceed, and offers some intuition on how these approaches differ to each other:

{% highlight python linenos %}
from numpy import *
import scipy.ndimage
import scipy.signal

image = float32(random_matrix(ZZ, 6, 6))
kern = float32(random_matrix(ZZ, 3, 3))

result1 = scipy.ndimage.convolve(image,kern)
result2 = fft.ifft2( multiply(fft.fft2(image), fft.fft2(kern,image.shape) )
result3 = scipy.signal.fftconvolve(image,kern)

l, w = image.shape[0] + kern.shape[0] - 1, image.shape[1] + kern.shape[1] - 1

result4 = fft.ifft2( multiply(fft.fft2(image,[l,w]), fft.fft2(kern,[l,w])) )
{% endhighlight %} 

<table style="margin-left:auto;margin-right:auto;width:75%;">
<tbody>
<tr>
<td style="width:50%;"><img src="https://i0.wp.com/farm6.static.flickr.com/5208/5369149286_9a995c1856_o_d.jpg" alt="" width="100%" /></td>
<td style="width:50%;"><img src="https://i0.wp.com/farm6.static.flickr.com/5087/5369149338_7346296bf0_o_d.jpg" alt="" width="100%" /></td>
</tr>
<tr>
<td style="width:50%;text-align:center;">`result1`</td>
<td style="width:50%;text-align:center;">`real(result2)`</td>
</tr>
<tr>
<td style="width:50%;"><img src="https://i0.wp.com/farm6.static.flickr.com/5005/5368539629_9968266318_o_d.jpg" alt="" width="100%" /></td>
<td style="width:50%;"><img src="https://i0.wp.com/farm6.static.flickr.com/5005/5368539629_9968266318_o_d.jpg" alt="" width="100%" /></td>
</tr>
<tr>
<td style="width:50%;text-align:center;">`real(result3[1:7,1:7])`</td>
<td style="width:50%;text-align:center;">`real(result4[1:7,1:7])`</td>
</tr>
</tbody>
</table>



**[Note:** Both `result1` and `result2` are matrices with size <span>\\( 6\times 6, \\)</span> while the matrices `result3` and `result4`, which are identical, have size <span>\\( 8\times 8. \\)</span>**]**

Another word of advise: one might feel tempted to create a Gaussian of the same size and shape of the original image.  For example, if the original image has size <span>\\( 512 \times 512, \\)</span> to create the Gaussian <span>\\( G_{16} \\)</span> one could proceed in `sage` as follows:

{% highlight python linenos %}
from numpy import *
import scipy

# Create a 512x512 radial matrix
[X,Y] = mgrid[-256:256, -256:256]
A = X + i*Y
R=abs(A)

# Create a full(!?) 512x512 gaussian kernel Gt
t = 16.0
Gt = exp(-multiply(R,R)/4.0/t)/4.0/pi/t
Gt = float32(Gt)
{% endhighlight %}

The procedure of convolution of a noisy version of an image with this kernel could be done as follows:

{% highlight python linenos %}
# Consider the lena image
image = scipy.misc.lena().astype(float32)

# Add some white Gaussian noise mu=0 sigma=16
NoisyImage = image + random.normal(0, 16, size=image.shape)
NoisyImageBase = multiply( NoisyImage>=0 , NoisyImage<=255 )
NoisyImage = multiply( NoisyImage, NoisyImageBase) + 255*(NoisyImage>255.0)

# Compute the convolution of lena with Gt.
convImageGt = scipy.ndimage.convolve(NoisyImage, Gt)
{% endhighlight %}

<table style="width:100%;">
<tbody>
<tr>
<td style="width:33%;"><img src="https://i0.wp.com/farm6.static.flickr.com/5042/5366863591_3b00e8f053_o_d.png" alt="" width="100%" /></td>
<td style="width:33%;"><img src="https://i0.wp.com/farm6.static.flickr.com/5164/5367475002_4275491e81_o_d.png" alt="" width="100%" /></td>
<td style="width:33%;"><img src="https://i0.wp.com/farm6.static.flickr.com/5083/5367860350_722fcc41a8_o_d.png" alt="" width="100%" /></td>
</tr>
<tr>
<td style="width:33%;text-align:center;">`original: image`</td>
<td style="width:33%;text-align:center;">`image + noise`</td>
<td style="width:33%;text-align:center;">`convImageGt`</td>
</tr>
</tbody>
</table>

Granted:  It accomplishes the requested operation, but at the expense of too many computations and storing unnecessary data—especially in cases where the original image contains millions of pixels!

Note the structure of the Gaussian kernel <span>\\( G_{1} \\)</span> (below, left).  This function is effectively zero more than about three standard deviations from the mean, so it does not make sense to store more than a small center window (below, right).  We therefore collect the important values in a small matrix and use it as a kernel instead, at the time of computing the convolution.

<p style="text-align:center;"><img src="https://i0.wp.com/farm6.static.flickr.com/5005/5367837394_f3c2d026fe_o_d.png" alt="" width="300px" /></p>

<div>
\begin{equation}
 \texttt{Gt} = \dfrac{1}{273} \begin{pmatrix} 1&4&7&4&1\\ 4&16&26&16&4\\ 7&26&41&26&7\\ 4&16&26&16&4\\ 1&4&7&4&1 \end{pmatrix}
 \end{equation}
</div>

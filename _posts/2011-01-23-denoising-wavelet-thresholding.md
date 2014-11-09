---
layout: page
title: 'Denoising: wavelet thresholding'
date: 2011-01-23 14:25:48.000000000 -05:00
category: course-material
topic: imaging
comments: false
---

We have seen a naïve way to perform denoising on images by a simple <a href="http://blancosilva.github.io/course-material/2011/01/18/convolution-with-gaussian-kernels.html">convolution with Gaussian kernels</a>.  In this post I would like to compare that simple method with a more elaborate one: *wavelet thresholding*.  The basic philosophy is based upon the local knowledge that wavelet coefficients offer us: Intuitively, small wavelet coefficients are dominated by noise, while wavelet coefficients with a large absolute value carry more signal information than noise.  Being that the case, it is reasonable to obtain a fast denoising of a given image if we perform two basic operations:

* Eliminate in the wavelet representation those elements with small coefficients, and
* Decrease the impact of elements with large coefficients.

In mathematical terms, all we are doing is *thresholding* the absolute value of wavelet coefficients by an appropriate function. For example, if we chose to eliminate all coefficients with absolute value less than a given threshold <span>\\( \theta \\)</span>, and keep the rest of the coefficients untouched, we end up with the thresholding function <span>\\( \tau_\theta \colon \mathbb{R}^+ \to \mathbb{R} \\)</span> given by:

<p style="text-align:center;"><img src="https://i0.wp.com/farm6.static.flickr.com/5124/5381177149_15bb17a09e_m_d.jpg" style="width:50%"></p>
<div>
	\begin{equation}
	\tau_\theta (x) = \begin{cases} 0 &\text{if } 0 \leq x\leq \theta \\ x &\text{if } x > \theta\end{cases}
	\end{equation}
</div>

We refer to this function as a *hard thresholding*.  But we might want to decrease the impact of the elements with large coefficients in absolute value—this is what we refer as *soft thresholding*.   A common way to perform this thresholding is by simple imposition of continuity of the function; e.g.:

<p style="text-align:center;"><img src="https://i0.wp.com/farm6.static.flickr.com/5047/5381815942_112bef03cf_m_d.jpg" style="width:50%"></p>
<div>
	\begin{equation}
	\tau_\theta (x) = \begin{cases} 0 &\text{if } 0\leq x\leq \theta \\ x-\theta &\text{if }x > \theta \end{cases} 
	\end{equation}
</div>

Other thresholding functions are of course possible, and the reader is encouraged to come up with different examples, and experiment with them.

The wavelet module `PyWavelet` is <a href="http://blancosilva.github.io/course-material/2011/01/23/wavelets-in-sage.html">easily embedded in `sage`</a>, and allows us to perform very fast and elegant denoising codes.  The following session shows an example: We load the image of Lena as an array of size <span>\\( 512 \times 512 \\)</span> containing values between `0` and `255`.   We contaminate the image with white noise <span>\\( (\sigma=16.0) \\)</span> and perform denoising with this technique.  Since <span>\\( 512 = 2^9, \\)</span> we require all nine levels of the Haar wavelet coefficients of the image.

{% highlight python linenos %}
from numpy import *
import scipy
import pywt

image = scipy.misc.lena().astype(float32)

noiseSigma = 16.0
image += random.normal(0, noiseSigma, size=image.shape)

wavelet = pywt.Wavelet('haar')
levels  = Integer( floor( log2(image.shape[0]) ) )

WaveletCoeffs = pywt.wavedec2( image, wavelet, level=levels)
{% endhighlight %}

The object `WaveletCoeffs` is a tuple with ten entries: the first one is the approximation at the highest level: 9; the second entry is a 3-tuple containing the three different details (horizontal, vertical and diagonal) at the same level.  Each consecutive entry is a 3-tuple containing the three different details at lower levels <span>\\( (n=8,7,6,5,4,3,2,1) \\)</span>

The module `pywt` has several threshold functions implemented.  Let us use the soft thresholding indicated above, with a made-up threshold <span>\\( \theta = \sigma \sqrt{2 \log_2(\texttt{image.size})}. \\)</span>

In order to apply this threshold to each single wavelet coefficient, we will make use of the powerful tools of functional programming from `sage`.  We need:

* A thresholding function.  We use the ones provided by the `pywt` package: `pywt.thresholding.soft`, and in particular its lambda expression:
{% highlight python %}
lambda x: pywt.thresholding.soft(x, threshold)
{% endhighlight %}
* `Python`'s built-in function `map(func, seq1, seq2, ...)`
* The tuple of objects over which we need to apply the thresholding:  In this case, the set of wavelet coefficients `WaveletCoeffs` computed above.

Once computed the new coefficients, we use `pywt.waverec2` to obtain the corresponding reconstruction:

{% highlight python linenos %}
threshold = noiseSigma*sqrt(2*log2(image.size))
NewWaveletCoeffs = map (lambda x: pywt.thresholding.soft(x,threshold),
WaveletCoeffs)
NewImage = pywt.waverec2( NewWaveletCoeffs, wavelet)
{% endhighlight %}

<table style="width:100%;border-width:0;">
<tbody>
<tr>
<td style="width:50%;border-width:0;"><img src="assets/5367475002_4275491e81_o_d.png" alt="" width="100%" /></td>
<td style="width:50%;border-width:0;"><img src="assets/5382329870_e3ee536df5_o_d.png" alt="" width="100%" /></td>
</tr>
<tr>
<td style="text-align:center;border-width:0;">original + noise</td>
<td style="text-align:center;border-width:0;">denoised (`haar`)</td>
</tr>
</tbody>
</table>

Denoising is good, but the overall visual quality of the resulting image is very poor: there are many artifacts, due mainly to the blocky nature of the Haar wavelet.  Also, the choice of threshold is artificial: it has a priori no relationship with the structure of the image.  Let's put a temporary solution to this problem by using a smoother wavelet, while keeping the same threshold.  To avoid excessive typing, we will wrap the code above into a neat function with variables being the image to be treated, the standard deviation of the noise added, and the name of the wavelet employed:

{% highlight python linenos %}
def denoise(data,wavelet,noiseSigma):
    levels = Integer(floor(log2(data.shape[0])))
    WC = pywt.wavedec2(data,wavelet,level=levels)
    threshold=noiseSigma*sqrt(2*log2(data.size))
    NWC = map(lambda x: pywt.thresholding.soft(x,threshold), WC)
    return pywt.waverec2( NWC, wavelet)
{% endhighlight %}

We can now perform the same operation with different wavelets.  The following script creates a `python` dictionary that assigns, to each wavelet, the corresponding denoised version of the corrupted Lena image.

{% highlight python linenos %}
Denoised={}
for wlt in pywt.wavelist():
    Denoised[wlt] = denoise( data=image, wavelet=wlt, noiseSigma=16.0)
{% endhighlight %}

The  four images below are the respective denoising by soft thresholding of wavelet coefficients on the same image with the same level of noise <span>\\( (\sigma = 16.0), \\)</span> for the symlet `sym15`, the Daubechies wavelet `db6`, the biorthogonal wavelet `bior2.8`, and the coiflet `coif2`.  Note that, except in the case of the denoising by biorthogonal wavelet, all of the others present clear artifacts:

<table style="width:100%;border-width:0;">
<tbody>
<tr>
<td style="width:50%;border-width:0;"><img src="assets/5381872501_e9296eb13c_o_d.png" alt="" width="100%" /></td>
<td style="width:50%;border-width:0;"><img src="assets/5382434292_891d198cdd_o_d.png" alt="" width="100%" /></td>
</tr>
<tr>
<td style="text-align:center;border-width:0;">denoised (`sym15`)</td>
<td style="text-align:center;border-width:0;">denoised (`db6`)</td>
</tr>
<tr>
<td style="width:50%;border-width:0;"><img src="assets/5382484863_5a054f4f3f_o_d.png" alt="" width="100%" /></td>
<td style="width:50%;border-width:0;"><img src="assets/5382485013_0683a07128_o_d.png" alt="" width="100%" /></td>
</tr>
<tr>
<td style="text-align:center;border-width:0;">denoised (`bior2.8`)</td>
<td style="text-align:center;border-width:0;">denoised (`coif2`)</td>
</tr>
</tbody>
</table>

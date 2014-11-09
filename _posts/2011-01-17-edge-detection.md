---
layout: page
title: 'Edge detection: The Scale Space Theory'
date: 2011-01-17 13:43:24.000000000 -05:00
category: course-material
topic: imaging
comments: false
---

Consider an image as a bounded function <span>\\( f: \square_2 \to \mathbb{R} \\)</span> with no smoothness or structure assumptions a priori.  Most relevant information of a given image is contained in the contours of the mapped objects: Think for example of a bright object against a dark background—the area where these two meet presents a curve where the intensity <span>\\( f(\boldsymbol{x}) \\)</span> varies strongly.  This is what we refer to as an "edge."

Initially, we may consider the process of detection of an edge by the simple computation of the gradient <span>\\( \nabla f(\boldsymbol{x}) = \big( \tfrac{\partial f}{\partial x_1}, \tfrac{\partial f}{\partial x_2} \big): \\)</span>  This gradient should have a large intensity <span>\\( \lVert \nabla f(\boldsymbol{x}) \rVert \\)</span> and a direction <span>\\( \tfrac{\nabla f(\boldsymbol{x})}{\lVert \nabla f(\boldsymbol{x}) \rVert} \\)</span> which indicates the perpendicular to the curve.  It therefore looks sound to simply compute the gradient of <span>\\( f \\)</span> and choose the points where these values are *large*.   This conclusion is a bit unrealistic for two reasons:

1. The points where the gradient is larger than a given threshold are open sets, and thus don't have the structure of curves.
2. Large gradient may arise in certain locations of the image due to tiny oscillations or noise, but completely unrelated to the objects being mapped.  As a matter of fact, there is no reason to assume the existence or computability of any gradient at all in a given digital image.

The second objection is solved by defining a smoothing process:  We associate with the image a smoothed version <span>\\( f_t(\boldsymbol{x}) \\)</span> depending upon a scale parameter <span>\\( t \\)</span> measuring the amount of smoothing.  This smoothing can be made by convolution of the image with a gaussian kernel of increasing width:

<div>
\begin{equation}
 f_t(\boldsymbol{x}) = \big( f \ast G_t \big)(\boldsymbol{x}), \text{ where } G_t(\boldsymbol{x}) = \dfrac{1}{4\pi t} \exp \bigg( -\dfrac{x^2+y^2}{4t} \bigg). 
 \end{equation}
</div>

The first objection is solved by defining edge points not as points where the gradient is large alone, but as points where some maximality property of the gradient is observed.  Let us take an example in dimension one:

> Let <span>\\( f: \mathbb{R} \to \mathbb{R} \\)</span> be a <span>\\( C^2 \\)</span> function and consider points where <span>\\( \lvert f'(x) \rvert \\)</span> is maximal.  At these points, the second derivative might change sign.  Thus, we can look for the "edge points" of the smooth signal among the points where <span>\\( f''(x) \\)</span> crosses zero.

Generalizing this idea in two dimensions leads to the Hildreth-Marr edge detection theory, or alternatively to the Canny edge detection theory.  The only difference is that Hildreth and Marr replace, in dimension two, <span>\\( f''(x) \\)</span> by the Laplacian of <span>\\( f: \\)</span>

<div>
\begin{equation} \mathop{\Delta}f(\boldsymbol{x}) = \dfrac{\partial^2 f}{\partial x_1^2}(\boldsymbol{x})+\dfrac{\partial^2 f}{\partial x_2^2}(\boldsymbol{x}). 
\end{equation}
</div>

Canny instead, gives up the linearity of the Laplacian and defines edge points as points where *the gradient is maximal in the direction of the gradient*.  This means that an edge point satisfies <span>\\( g'(0)=0, \\)</span> where

<div>
\begin{equation} g(t) = \bigg\lVert \nabla f \big( \boldsymbol{x} + t \tfrac{\nabla f(\boldsymbol{x})}{\lVert \nabla f(\boldsymbol{x}) \rVert} \big) \bigg\rVert. 
\end{equation}
</div>

Note that this condition is equivalent to the simpler:

<div>
\begin{equation} \begin{pmatrix} \dfrac{\partial f}{\partial x_1} & \dfrac{\partial f}{\partial x_2} \end{pmatrix} \cdot \begin{pmatrix}   \dfrac{\partial^2 f}{\partial x_1^2}& \dfrac{\partial^2 f}{\partial x_1 \partial x_2}\\ \\ \dfrac{\partial^2 f}{\partial x_1 \partial x_2}& \dfrac{\partial^2 f}{\partial x_2^2} \end{pmatrix} \cdot \begin{pmatrix}  \dfrac{\partial f}{\partial x_1}\\ \\ \dfrac{\partial f}{\partial x_2}\end{pmatrix} = 0. 
\end{equation}
</div>

Let us proceed to code these two edge detection algorithms:  In both cases, we start by convolving the image with Gaussians <span>\\( G_t \\)</span> of increasing widths (usually for a sequence of dyadic scales <span>\\( t=2, 4, 8, 16, \dotsc, 2^m \\)</span>) [see <a href="http://blancosilva.github.io/course-material/2011/01/18/convolution-with-gaussian-kernels.html">Convolution with Gaussian kernels</a>]

<hr />

## Hildreth-Marr

* At each scale <span>\\( t, \\)</span> compute the *zero-crossings* of the Laplacian: those points <span>\\( \boldsymbol{x} \\)</span> where <span>\\( \nabla f(\boldsymbol{x}) \neq \boldsymbol{0}, \\)</span> and <span>\\( \mathop{\Delta}f \\)</span> changes sign.
* Eliminate zero-crossings with small gradient.

<hr />

Both gradient and Laplacian are easy to compute in `sage`:

{% highlight python linenos %}
from numpy import *
import scipy.ndimage
import scipy.signal

image = scipy.misc.lena().astype(float32)

# Convolve with a Gaussian Gt for t=2
[X,Y]=numpy.mgrid[-6:7,-6:7]
A=X+i*Y
R=abs(A)
t=2.0
Gt=exp(-R*R/4.0/t)/4.0/pi/t
convImage = scipy.signal.convolve(image,Gt)

# Gradient
Grdnt = numpy.gradient(convImage)
# Magnitude of the gradient
magn  = sqrt( Grdnt[0]*Grdnt[0] + Grdnt[1]*Grdnt[1] )
# Laplacian
Lplz  = scipy.ndimage.laplace(float32(convImage))
{% endhighlight %}

<table style="width:100%;border-width:0;">
<tbody>
<tr>
<td style="width:100%;text-align:center;border-width:0;" colspan="2"><img src="https://i0.wp.com/farm6.static.flickr.com/5082/5373118608_ca48a3009e_o_d.png" alt="" width="50%" /></td>
</tr>
<tr>
<td style="width:100%;text-align:center;border-width:0;" colspan="2">Gradient (in blue) and perpendicular to the gradient (in red); detail from the center of the image</td>
</tr>
<tr>
<td style="width:50%;border-width:0;"><img src="https://i0.wp.com/farm6.static.flickr.com/5083/5372795316_ecbbfca9bc_o_d.png" alt="" width="100%" /></td>
<td style="width:50%;border-width:0;"><img src="https://i0.wp.com/farm6.static.flickr.com/5201/5369466100_ec687f8de5_o_d.png" alt="" width="100%" /></td>
</tr>
<tr>
<td style="width:50%;text-align:center;border-width:0;">Magnitude of the gradient (`magn`)</td>
<td style="width:50%;text-align:center;border-width:0;">Laplacian of the image (`Lplz`)</td>
</tr>
</tbody>
</table>

For the purposes of this post, we will consider that a pixel <span>\\( (x_1,x_2) \\)</span> is a zero-crossing, provided at least one of the following conditions holds:

* *Horizontal crossing*:
<div>
\begin{equation}
 \mathop{\Delta} f(x_1-1,x_2) \cdot \mathop{\Delta} f(x_1+1,x_2) > 0. 
 \end{equation}
</div>

* *Vertical crossing*:
<div>
\begin{equation}
 \mathop{\Delta} f(x_1,x_2-1) \cdot \mathop{\Delta} f(x_1,x_2+1) >0. 
 \end{equation}
</div>

* *NW-SE crossing*:
<div>
\begin{equation}
 \mathop{\Delta} f(x_1-1,x_2-1) \cdot \mathop{\Delta} f(x_1+1,x_2+1) > 0. 
 \end{equation}
</div>

* *NE-SW crossing*:
<div>
\begin{equation}
 \mathop{\Delta} f(x_1+1,x_2-1) \cdot \mathop{\Delta} f(x_1-1,x_2+1) >0. 
 \end{equation}
</div>


A quick way to code a matrix that collects all the pixels where any of these crossings occur can be done as follows:

{% highlight python linenos %}
# Four matrices holding the crossings...
WWEE = zeros(Lplz.shape)
NNSS = zeros(Lplz.shape)
NWSE = zeros(Lplz.shape)
NESW = zeros(Lplz.shape) 

WWEE[1:Lplz.shape[0]-1,:] = sign(multiply(Lplz[0:Lplz.shape[0]-2,:],
                                          Lplz[2:Lplz.shape[0],:]))>0
NNSS[:,1:Lplz.shape[1]-1] = sign(multiply(Lplz[:,0:Lplz.shape[1]-2],
                                          Lplz[:,2:Lplz.shape[1]]))>0
NWSE[1:Lplz.shape[0]-1,1:Lplz.shape[1]-1] =
         sign(multiply(Lplz[0:Lplz.shape[0]-2,0:Lplz.shape[1]-2],
                       Lplz[2:Lplz.shape[0],2:Lplz.shape[1]]))>0
NESW[1:Lplz.shape[0]-1,1:Lplz.shape[1]-1] =
         sign(multiply(Lplz[2:Lplz.shape[0],0:Lplz.shape[1]-2],
                       Lplz[0:Lplz.shape[0]-2,2:Lplz.shape[1]]))>0

# ...combined into a single matrix holding all the crossings
ZeroCrossings = maximum( maximum( maximum(NNSS, WWEE), NWSE), NESW)
{% endhighlight %}


It only remains to throw away those zero-crossings (below, left) where the magnitude of the gradient is small.  I decided to set as threshold <span>\\( \theta = 3. \\)</span>   In that case, the edge map (below, right) is computed as follows:

{% highlight python linenos %}
theta=3.0
Edges = multiply(ZeroCrossings, magn>theta)
{% endhighlight %}

<table style="width:100%;border-width:0;">
<tbody>
<tr>
<td style="width:50%;border-width:0;"><img src="https://i0.wp.com/farm2.static.flickr.com/1416/5369723851_3df658ddbc_o_d.png" alt="" width="100%" /></td>
<td style="width:50%;border-width:0;"><img src="https://i0.wp.com/farm6.static.flickr.com/5282/5372231161_dc4628f77e_o_d.png" alt="" width="100%" /></td>
</tr>
<tr>
<td style="width:50%;text-align:center;border-width:0;">`ZeroCrossings`</td>
<td style="width:50%;text-align:center;border-width:0;">`Edges`</td>
</tr>
</tbody>
</table>

We need to repeat the same procedure on the smoothing <span>\\( f_t \\)</span> for different scales, say the dyadic <span>\\( t=2^k \\)</span> for <span>\\( k=2, \dotsc, 5, \\)</span> and then collect all the corresponding results.  Note that the same threshold <span>\\( \theta=3 \\)</span> must be applied to the magnitude of the different gradients.

<hr />

## Canny

* At each scale <span>\\( t, \\)</span> compute points <span>\\( \boldsymbol{x} \\)</span> satisfying <span>\\( \nabla f(\boldsymbol{x})\neq \boldsymbol{0}, \\)</span> and where the expression below changes sign:

<div>
  \begin{equation}
  \begin{pmatrix} \dfrac{\partial f}{\partial x_1} & \dfrac{\partial f}{\partial x_2} \end{pmatrix} \cdot \begin{pmatrix}   \dfrac{\partial^2 f}{\partial x_1^2}& \dfrac{\partial^2 f}{\partial x_1 \partial x_2}\\ \\ \dfrac{\partial^2 f}{\partial x_1 \partial x_2}& \dfrac{\partial^2 f}{\partial x_2^2} \end{pmatrix} \cdot \begin{pmatrix}  \dfrac{\partial f}{\partial x_1}\\ \\ \dfrac{\partial f}{\partial x_2}\end{pmatrix}. 
  \end{equation}
</div>

* At each scale <span>\\( t \\)</span> fix a threshold <span>\\( \theta(t) \\)</span> and discard the points <span>\\( \boldsymbol{x} \\)</span> computed in the previous step that satisfy <span>\\( \lVert \nabla f(\boldsymbol{x}) \rVert \leq \theta(t). \\)</span>

<hr />

We start by computing a matrix `N` where we collect, for each index <span>\\( (x_1,x_2), \\)</span> the corresponding value of the expression above.  We perform on this matrix a similar search for zero-crossings as we computed for the algorithm of Hildreth-Marr:

{% highlight python linenos %}
D1,D2=numpy.gradient(convImage)
D11,D12=numpy.gradient(D1)
D21,D22=numpy.gradient(D2)
N = D1*D11*D1 + D1*D12*D2 + D2*D21*D1 + D2*D22*D2

WWEE[1:N.shape[0]-1,:] = sign(N[0:N.shape[0]-2,:]*N[2:N.shape[0],:])>0
NNSS[:,1:N.shape[1]-1] = sign(N[:,0:N.shape[1]-2]*N[:,2:N.shape[1]])>0
NWSE[1:N.shape[0]-1,1:N.shape[1]-1] =
          sign(N[0:N.shape[0]-2,0:N.shape[1]-2]*
               N[2:N.shape[0],2:N.shape[1]])>0
NESW[1:N.shape[0]-1,1:N.shape[1]-1] =
          sign(N[2:N.shape[0],0:N.shape[1]-2]*
               N[0:N.shape[0]-2,2:N.shape[1]])>0

ZeroCrossings = maximum( maximum( maximum(NNSS, WWEE), NWSE), NESW)

theta=3.0
Edges=multiply(ZeroCrossings, magn>theta)
{% endhighlight %}

<table style="width:100%;border-width:0;">
<tbody>
<tr>
<td style="width:50%;border-width:0;"><img src="https://i0.wp.com/farm6.static.flickr.com/5006/5373382878_5d902f615a_o_d.png" alt="" width="100%" /></td>
<td style="width:50%;border-width:0;"><img src="https://i0.wp.com/farm6.static.flickr.com/5001/5372783863_4db21d4754_o_d.png" alt="" width="100%" /></td>
</tr>
<tr>
<td style="width:50%;text-align:center;border-width:0;">`ZeroCrossings (Canny)`</td>
<td style="width:50%;text-align:center;border-width:0;">`Edges (Canny)`</td>
</tr>
</tbody>
</table>

As in the algorithm of Hildreth-Marr, we need to repeat the same procedure on the smoothing <span>\\( f_t \\)</span> for different dyadic scales and collect all the corresponding results.  The difference is that here we allow a scale-dependent threshold <span>\\( \theta(t). \\)</span>  A selection that works well is, for example, to choose the mean value of the magnitudes of the gradient of <span>\\( f_t. \\)</span>  I encourage you to play around with different images, and investigate what characteristics will dictate a good choice in this case.

## Miscellaneous

### The Scale Space Theory

What do we do with all different edge maps at different scales?  For most images it is enough to "choose" the edge map at a certain scale—that one that visually satisfies whatever constraints we might require for a particular problem.  Sometimes it pays off to collect them all, or start with the edges at the lowest level scale, and add a selection of the new edges from the larger scales… There is no single best method, as far as I am concerned.

### Codes for graphics

The code that produced most of the images above is straightforward, except maybe the addition of the vector fields of the gradient and its normal on top of the windowed image.  This was accomplished with the following commands:

{% highlight python linenos %}
matplotlib.pyplot.figure()
# Plot the Gradient (note the switching of derivatives and sign)
matplotlib.pyplot.quiver(-D2[300:450:4,300:450:4],D1[300:450:4,300:450:4],
                                  color='b', pivot='mid', units='x')
# Plot the perpendicular to the Gradient
matplotlib.pyplot.quiver(D1[300:450:4,300:450:4],D2[300:450:4,300:450:4],
                                  color='r', pivot='mid', units='x')
matplotlib.pyplot.quiver(-D1[300:450:4,300:450:4],-D2[300:450:4,300:450:4],
                                  color='r', pivot='mid', units='x')
# Place the corresponding window of the image as background
matplotlib.pyplot.gray()
matplotlib.pyplot.imshow(float32(convImage[300:450:4,300:450:4]))
matplotlib.pyplot.savefig('/Users/blanco/Desktop/quiver.png')
{% endhighlight %}

Note that the first and second derivatives *seem to have switched places*.  One needs to be very careful when dealing with matrices of numbers, since the logical position of the pixels depends very heavily the software/language/libraries that handles them.  With `sage` this is a constant issue, especially since we might be using different (and unrelated) libraries to deal with the same objects.

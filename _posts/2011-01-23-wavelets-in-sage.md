---
layout: page
title: Wavelets in sage
date: 2011-01-23 11:56:44.000000000 -05:00
category: course-material
topic: imaging
comments: false
---

There are no native wavelet packages in `sage`.  But there is a great module in `python` that contains, among other things, forward and inverse discrete wavelet transforms (for one and two dimensions).  It comes bundled with seventy-six wavelet filters, and allows support to build your own!   The name is PyWavelets, written by Tariq Rashid, and can be retrieved from <a href="http://pypi.python.org/pypi/PyWavelets/">pypi.python.org/pypi/PyWavelets</a>.  In order to install it in `sage`, take the following steps:

Download the latest version, and unpack it.

{% highlight bash %}
% tar xvfz PyWavelets-0.2.0.tar.bz2
{% endhighlight %}

Navigate to the top-level directory of the newly created PyWavelets folder, and install the package in `sage`.

{% highlight bash %}
% /Applications/sage/sage -python setup.py install
{% endhighlight %}

This should be enough!  Open a `sage` session, and import the `pywt` module:

{% highlight text %}
>>> import pywt
>>> dir(pywt)
['BaseNode', 'MODES', 'Node', 'Node2D', 'Wavelet', 'WaveletPacket', 'Wavelet
Packet2D', '__all__', '__author__', '__builtins__', '__doc__', '__file__',
'__license__', '__name__', '__package__', '__path__', '__version__', '_pywt'
, 'centfrq', 'downcoef', 'dwt', 'dwt2', 'dwt_coeff_len', 'dwt_max_level', 'd
wtn', 'families', 'functions', 'idwt', 'idwt2', 'intwave', 'numerix', 'orthf
ilt', 'qmf', 'release_details', 'scal2frq', 'swt', 'swt2', 'swt_max_level',
'thresholding', 'upcoef', 'wavedec', 'wavedec2', 'wavelist', 'waverec', 'wav
erec2']
{% endhighlight %}

It might happen that the installation is not very clean:

{% highlight text %}
>>> import pywt
---------------------------------------------------------------------------
ImportError                               Traceback (most recent call last)

/Users/blanco/Documents/Research/PyWavelets-0.2.0/ in ()

/Users/blanco/Documents/Research/PyWavelets-0.2.0/pywt/__init__.py in ()
     11 """
     12
---> 13 from _pywt import *
     14 from multilevel import *
     15 from multidim import *

ImportError: No module named _pywt
{% endhighlight %}

In that event, simply find where the `_pywt.so` library is in your PyWavelet package, and place a link in your `sage` libraries:

{% highlight bash %}
% sudo ln -sv ./PyWavelets-0.2.0/build/lib.macosx-10.6-i386-2.6/pywt/_pywt.so /Applications/sage/local/lib/.
{% endhighlight %}

<hr />

Once installed, you can get a flavor of what it means to work with this module by exploring a little.  For example, to find out how many different families of wavelets are implemented, or the names of each of the filters present in the package, simply issue

{% highlight text %}
>>> pywt.families()
['haar', 'db', 'sym', 'coif', 'bior', 'rbio', 'dmey']

>>> pywt.wavelist()
['bior1.1', 'bior1.3', 'bior1.5', 'bior2.2', 'bior2.4', 'bior2.6', 'bior2.8', '
bior3.1', 'bior3.3', 'bior3.5', 'bior3.7', 'bior3.9', 'bior4.4', 'bior5.5', 'bi
or6.8', 'coif1', 'coif2', 'coif3', 'coif4', 'coif5', 'db1', 'db2', 'db3', 'db4'
, 'db5', 'db6', 'db7', 'db8', 'db9', 'db10', 'db11', 'db12', 'db13', 'db14', 'd
b15', 'db16', 'db17', 'db18', 'db19', 'db20', 'dmey', 'haar', 'rbio1.1', 'rbio1
.3', 'rbio1.5', 'rbio2.2', 'rbio2.4', 'rbio2.6', 'rbio2.8', 'rbio3.1', 'rbio3.3
', 'rbio3.5', 'rbio3.7', 'rbio3.9', 'rbio4.4', 'rbio5.5', 'rbio6.8', 'sym2', 's
ym3', 'sym4', 'sym5', 'sym6', 'sym7', 'sym8', 'sym9', 'sym10', 'sym11', 'sym12'
, 'sym13', 'sym14', 'sym15', 'sym16', 'sym17', 'sym18', 'sym19', 'sym20']
{% endhighlight %}

To compute one level of the Haar-wavelet coefficients of a given image (the top level alone), we proceed as follows:

{% highlight python linenos %}
from numpy import *
import scipy

image=scipy.misc.lena().astype(float32)

Aprox, Details = pywt.dwt2( image, pywt.Wavelet('haar') )
HorizDetail, VertDetail, DiagDetail = Details
{% endhighlight %}

<table style="width:75%;border-width:0;margin-left:auto;margin-right:auto;">
<tbody>
<tr>
<td style="width:50%;border-width:0;"><img src="https://i0.wp.com/farm6.static.flickr.com/5090/5380674347_bf597e9638_o_d.png" alt="" width="100%" /></td>
<td style="width:50%;border-width:0;"><img src="https://i0.wp.com/farm6.static.flickr.com/5164/5381268874_74d710da83_o_d.png" alt="" width="100%" /></td>
</tr>
<tr>
<td style="width:50%;text-align:center;border-width:0;">Approximation</td>
<td style="width:50%;text-align:center;border-width:0;">Horizontal Detail</td>
</tr>
<tr>
<td style="width:50%;border-width:0;"><img src="https://i0.wp.com/farm6.static.flickr.com/5124/5381268740_d1005150e7_o_d.png" alt="" width="100%" /></td>
<td style="width:50%;border-width:0;"><img src="https://i0.wp.com/farm6.static.flickr.com/5164/5381277076_7b1d2eb5a7_o_d.png" alt="" width="100%" /></td>
</tr>
<tr>
<td style="width:50%;text-align:center;border-width:0;">Vertical Detail</td>
<td style="width:50%;text-align:center;border-width:0;">Diagonal Detail</td>
</tr>
</tbody>
</table>

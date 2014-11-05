---
layout: post
title: The Nonlocal-means Algorithm
date: 2010-04-28 00:58:00.000000000 -04:00
category: post
comments: true
---

The nonlocal-means algorithm [<a href="http://www.google.com/url?sa=t&amp;source=web&amp;ct=res&amp;cd=8&amp;ved=0CC0QFjAH&amp;url=http%3A%2F%2Fciteseerx.ist.psu.edu%2Fviewdoc%2Fdownload%3Fdoi%3D10.1.1.108.6427%26rep%3Drep1%26type%3Dpdf&amp;ei=urzZS42wFZLK8ATlr-DYAQ&amp;usg=AFQjCNF5nJo_13bxj53H8ZMOvHFD8duWSg&amp;sig2=RgRUCN-tGpij-YOp1WjdLA">Buades, Coll, Morel</a>] was designed to perform noise reduction on digital images, while preserving the main geometrical configurations, as well as finer structures, details and texture.  The algorithm is consistent under the condition that one can find many samples of every image detail within the same image.

<table width="100%" style="border-width:0;">
<tbody>
<tr>
<td width="30%" style="border-width:0;"><img src="http://farm4.static.flickr.com/3267/4561651402_faa7cfdfc6_o.jpg" alt="" width="100%" /></td>
<td width="30%" style="border-width:0;"><img src="http://farm3.static.flickr.com/2723/4561651532_1befae6b32_o.jpg" alt="" width="100%" /></td>
<td width="30%" style="border-width:0;"><img src="http://farm4.static.flickr.com/3557/4561651320_217822c20f_o.jpg" alt="" width="100%" /></td>
</tr>
<tr>
<td style="text-align:center;font-family:modern;font-size:12pt;border-width:0;">Barbara</td>
<td style="text-align:center;font-family:modern;font-size:12pt;border-width:0;">Noise added, <tt>std=30</tt></td>
<td style="text-align:center;font-family:modern;font-size:12pt;border-width:0;">Denoised image, <tt>h=93</tt></td>
</tr>
</tbody>
</table>

The algorithm has the following closed form:  Given a finite grid <span>\\( \Lambda \subset \mathbb{Z}^2 \\)</span> of the form <span>\\( \Lambda = \Omega \cap \mathbb{Z}^2 \\)</span> for some compact set <span>\\( \Omega \subset \mathbb{R}^2 \\)</span>, a signal <span>\\( f \in L_2(\Lambda,\mathbb{R}^+) \\)</span>, and a family of *windows* <span>\\( \\{ \mathcal{R}\_k \\}\_{k \in \Lambda} \\)</span> satisfying the conditions

1. <span>\\( k \in \mathcal{R}_k \\)</span> for all <span>\\( k \in \Lambda \\)</span>.
2.  If <span>\\( j \in \mathcal{R}_k \\)</span>, then <span>\\( k \in \mathcal{R}_j \\)</span>,

the nonlocal-means operator <span>\\( \text{NL}_h\colon \ell_2(\Lambda,\mathbb{R}) \to \ell_2(\Lambda,\mathbb{R}) \\)</span> with filtering parameter <span>\\( h&gt;0 \\)</span>, is defined by

<div>
	\begin{equation}
\text{NL}_h f(k) = \sum_{j \in \Lambda} \omega_h(j,k) f(j),
\end{equation}
</div>

where the weights <span>\\( \{ \omega_h(j,k) \}_{j,k \in \Lambda} \\)</span> are defined by

<div>
\begin{equation}
 \omega_h(j,k) = \frac{ \exp \bigg( -\frac{\left\lVert f(\mathcal{R}_j) - f(\mathcal{R}_k) \right\rVert_{2,a}^2}{h^2} \bigg) }{ \sum_{j \in \Lambda} \exp \bigg( - \frac{\left\lVert f(\mathcal{R}_j) - f(\mathcal{R}_k) \right\rVert_{2,a}^2}{h^2} \bigg)}.
\end{equation}
</div>

Here, <span>\\( f(\mathcal{R}) \\)</span> denotes a *patch* of the image <span>\\( f \\)</span> supported on the window <span>\\( \mathcal{R} \\)</span>.

Notice that the *similarity* between patches is nothing but a simple Gaussian weighted Euclidean distance, which accounts for difference of grayscales alone. <a href="http://www.google.com/url?sa=t&amp;source=web&amp;ct=res&amp;cd=1&amp;ved=0CAgQFjAA&amp;url=http%3A%2F%2Fgraphics.cs.cmu.edu%2Fpeople%2Fefros%2Fresearch%2FNPS%2Fefros-iccv99.pdf&amp;ei=w7vZS8udFZLK8ATlr-DYAQ&amp;usg=AFQjCNHVEBaLtGLRS97qyp56MEPJ1aeRXg&amp;sig2=b_w4DZt33t0wWIkY0zW6jQ">Efros and Leung</a> prove that this distance is a reliable measure for the comparison of texture patches, and at the same time copes very well with additive white noise; in particular, if <span>\\( f \\)</span> and <span>\\( g \\)</span> are respectively the noisy and original images, and <span>\\( \sigma^2 \\)</span> is the noise variance, then the most similar patches in the noisy image are also expected to be the most similar in the original:

<div>
	\begin{equation}
 \mathbb{E} \left\lVert f(\mathcal{R}_j) - f(\mathcal{R}_k) \right\rVert_{2,a}^2 = \left\lVert g(\mathcal{R}_j) - g(\mathcal{R}_k) \right\rVert_{2,a}^2 + 2\sigma^2 .
 \end{equation}
</div>

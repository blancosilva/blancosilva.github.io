---
layout: page
title: Research
date: 2010-07-06 22:35:36.000000000 -04:00
crumbs: false
main: false
permalink: /research/
---

<ul class="nav nav-tabs" role="tablist">
	<li role="presentation"><a href="/about/">About me</a></li>
	<li role="presentation"><a href="/resume/">Résumé</a></li>
	<li role="presentation"><a href="/cv/">Curriculum Vitae</a></li>
	<li role="presentation" class="active"><a href="/research/">Research</a></li>
	<li role="presentation" class="active"><a href="/resume/">Teaching Interests</a></li>
</ul>

<br />

This is a description of my current research, both at the level of development of theoretical tools, as well as at the level of applications to real-life problems. I have thus divided the exposition in two parts.

In the first section, I describe my work in Approximation Theory derived from my dissertation, briefly explain the importance of these results to applications in Image Processing, and present some examples in which I am actively investigating.

In the second section, I describe some of the applied problems in which I have been involved:

* Super-resolution applied to Electron Microscopy Imaging, and
* Modeling the impact of ebola and bushmeat hunting in Western Lowland gorillas.

The former comes from a collaboration of the Nanotechnology Center of the University of South Carolina with the Interdisciplinary Mathematics Institute, for which I have been a post-doctoral researcher for the last three years. The latter is a pet-project that started as a collaboration among mathematicians, statisticians and forestry engineers, with a pasion for our environment.

### Approximation Theory

My dissertation [BS07], “The Curvelet Transform—A Generalized Definition and Approximation Properties” was aimed to the construction of families of function spaces spanned by curvelet frames, as well as the computation of the associated approximation spaces. My work covered an improvement on the construction of curvelets defined by Candés and Donoho in [CD05a] and [CD05b], which offers the simple expression below for its corresponding transform, and allows the treatment of low-frequency functions with the same curvelet-like elements:

<div class="well">
	Curvelets is an example of a family of square-integrable, complex-valued functions \( \gamma_{\alpha \beta \theta} \) indexed by three parameters (\( \alpha&gt;0 \)  for scale, \( \beta \in \mathbb{R}^2 \) for shift, and \( \theta \in \mathbb{S}^1 \) for angle) with the following fundamental property: For all functions \( f, g \in L_2(\mathbb{R}^2) \)
	<div>
		\begin{equation*}
		\langle f, g \rangle = \int_0^\infty \int_{\mathbb{S}^1} \int_{\mathbb{R}^2} \langle f, \gamma_{\alpha \beta \theta} \rangle \overline{\langle g, \gamma_{\alpha \beta \theta} \rangle}\, d\beta\, d\sigma(\theta)\, d\alpha, 
		\end{equation*}
	</div>
	where \( d\sigma(\theta) \) denotes the surface integral on the sphere.

	One can choose a discrete set of this family to form a frame in \( L_2(\mathbb{R}^2) \): If we denote \( \phi_{nk\ell} = \gamma_{\alpha \beta \theta} \) for carefully chosen values \( \alpha = \alpha_n \), \( \theta = \theta_{nk} \) and \( \beta = \beta_{nk\ell} \), then there exist constants \( 0 &lt; A \leq B \) such that for all square-integrable functions \( f \in L_2(\mathbb{R}^2) \)
	<div>
		\begin{equation*}
		A\lVert f \rVert_{L_2(\mathbb{R}^2)}^2 \leq \sum_n \sum_k \sum_\ell \langle f, \phi_{n k \ell} \rangle^2 \leq B\lVert f \rVert_{L_2(\mathbb{R}^2)}^2. 
		\end{equation*}
	</div>
</div>

I presented an exhaustive analysis of my Curvelet Transform and show how to use it, for example, to study regularity of square-integrable complex-valued functions <span>\\( f \in L_2(\mathbb{R}^2) \\)</span>.

I also developed a discretization of this particular Curvelet Transform that allows the construction of tight frames of curvelets (frames where <span>\\( A = B = 1 \\)</span>), and the posterior organization of these frames to build families of approximants (sequences of homogeneous spaces spanned by partial frames, whose union is dense in <span>\\( L_2(\mathbb{R}^2) \\)</span>)

These spaces, together with the regularity results produced above, are the building block for studying the approximation properties of the corresponding frames, in the following sense:  The regularity results are a previous step in the construction of spaces <span>\\( Y \subset L_2(\mathbb{R}^2) \\)</span> for which Jackson and Bernstein inequalities are satisfied by the families of approximants spanned by curvelet frames. With both these inequalities, it is trivial to construct and compute the approximation spaces stated above.

The techniques I use are mostly based on the work of Ronald Devore ([DeV98] and [DL93]). My treatment of the Curvelet Transform pretends to mimic that of wavelets presented by Ingrid Daubechies in [Dau92].

The natural continuation of this work is to extend the same type of results to general frames with the edge-detection property: bandelets, chirplets, contourlets, dual-tree complex wavelets, noiselets, ridgelets, shearlets, wedgelets, wavelet packets, etc.

As a first step in this direction, I am currently working on the equivalence of description of smoothness spaces as decomposition spaces generated from frames of curvelets and shearlets (see below)

At the same time, I am exploring the computational advantages of using frames constructed from overcompleting well-known bases. The main example is given by the Dual-tree Complex Wavelet transform: a smart complexification of two different wavelet transforms related by a phase shift. I present below more information, as well as a good set of background citations.

The solution to the questions posed above serve as a starting point to developing new strategies to problems in Image Processing, where treatment of data with curved singularities is needed. This is one of the driving forces of my work.

#### Equivalence of Approximation Spaces generated from different frames.

This is a natural problem when facing frames with a similar construction and structure. For example, in the search for frames with the edge-detection property, two stand out: the curvelets of Donoho and Candés defined above, and the shearlets of Guo, Kutyniok, Labate and Weiss (see e.g. [GKL06]).  At implementation time (for signal processing purposes), shearlets have a great advantage over curvelets: not only are their elements easily represented in the lattice in Fourier domain, but also the shearlets' construction is based on multiresolution analysis, which makes design of algorithms very convenient and fast.  On the other hand, the polar nature of elements from curvelet frames makes them a more desirable pick when proving Theorems.  Yet, elements in both frames share very similar geometric properties: their support in frequency domain is compactly supported in slits of growing annulae (be it circular or square), and they are both indexed by a triple, that indicates frequency, location and some sense of directionality in the plane.

It is thus conjectured that both frames have the same approximation properties:  If this is true, a researcher may regard them as the same object (only for approximation purposes) and make use of one or another depending on the situation at hand.

The generalization of this idea to general frames is an ambitious long-term project, in which I mean to devote many of my efforts.  My personal take for a successful resolution of this problem requires a treatment of function spaces similar to that of computation of invariants of manifolds in the scope of Algebraic Topology.  I aim to describe invariants of function spaces by means of (properly defined) homology groups associated to these spaces, in a similar fashion as in the theory of Loop spaces as complex manifolds.

Baby steps in this direction start by defining this machinery for smoothness spaces defined from frames by decomposition methods (see e.g.[FG85] or [BN07]).  They are a natural first step prior to attacking the general problem stated above, from which one will certain learn valuable techniques to deal with approximation spaces in the future. 

#### The Dual-Tree Complex Wavelet Transform

Although the discrete wavelet transform (DWT) is a powerful signal-processing tool, it has three disadvantages that undermine its usage in many applications. First, it is shift sensitive because input-signal shifts generate unpredictable changes in DWT coefficients. Second, the DWT suffers from poor directionality because DWT coefficients reveal only three spatial orientations. Third, DWT analysis of real signals lacks the phase information that accurately describes non-stationary signal behavior. To overcome these problems, Kingsbury [Kin01] created the dual-tree complex wavelet transform (<span>\\( \mathbb{C} \\)</span>WT), a redundant, complex wavelet transform with excellent directionality, reduced shift sensitivity and explicit phase information. Because of these advantages, the <span>\\( \mathbb{C} \\)</span>WT yields excellent results in applications where redundancy is acceptable.

The wavelets associated with the filter banks are an almost-Hilbert pair (see [YCW07]). This property is critical since it provides the advantages of reduced shift sensitivity, improved directionality and explicit phase information. However, the design of Kingsbury’s <span>\\( \mathbb{C} \\)</span>WT filters is very complicated because it requires an iterative optimization over the space of “perfect-reconstruction” filter banks. To simplify and generalize the <span>\\( \mathbb{C} \\)</span>WT design procedure, Selesnick [Sel01] proposed a new method to obtain filters that may be used instead.

Design of similar frames that overcome these computational difficulties is part of my research. We mainly aim to reduce the redundancy and further simplify the design procedure: since transform coefficients require more storage space than the input signals, the Dual-tree complex wavelet transform cannot be used in applications such as image/video compression where thriftier signal representations are crucial.

I am also involved in researching the advantages of using these transforms in applications to lower-level analysis in Image Processing: edge-detection, horizon-detection, and computation of smoothness are an example of the tasks I have analyzed in my work.

### Applications

#### Super-resolution applied to Electron Microscopic Imaging

This work is a collaboration among mathematicians, material and electrical engineers, chemists and electron microscopists. It is an ongoing effort to solve an ambitious question in Nanotechnology: extracting structural information (at the atomic level) from micrographs of molecules of different materials. A successful outcome will provide scientist with precise information on how the structural defects of a material provide its chemical properties, thus leading to the possibility of nano- manufacturing a similar (cheaper) product with the same properties.

Modern electron microscopic imaging has reached resolutions significantly better than 100pm, which allows for unprecedented measurements of the composition and structure of materials. However, one faces several severe obstacles to fully exploiting the information provided by aberration-corrected instruments. On the one hand, one needs to constantly remediate and reduce environmental perturbations such as air flow, acoustic noise, floor vibrations, AC and DC magnetic fields, and temperature fluctuations. On the other hand, high resolution and a good signal to noise ratio requires a high density of electrons per square nanometer. Unfortunately, soft materials are very susceptible to beam damage, and can only be visualized with low dose beams, resulting in poor resolution and a prohibitively low signal to noise ratio. Imaging matter using electron microscopes, in particular STEM (scanning transmission electron microscopes), will become increasingly important in the near future, especially in Biology.

By using a STEM and a high-angle annular detector, it is possible to obtain atomic resolution images where the contrast is directly related to the atomic number. As for beam sensitivity, a critical issue in electron microscopy is the amount of dose needed to produce an image. Higher dose scans can damage the specimen while lower dose scans result in very low signal to noise ratio. In STEM mode, the electron dose onto the sample can be controlled in a variety of ways: The number of electrons per unit time can be varied by changing the demagnification of the electron source through the strength of the first condenser lens. The dwell time of the probe is typically varied between 7μs and 64μs per pixel in practice, although a much larger range is possible. The size of the image can be varied from a very small number of pixels in a frame (256 × 256) to over 64 million pixels per image (8192 × 8192). Finally, the magnification of the image sets the area of the specimen exposed to the electrons and thereby affects the dose per unit area onto the specimen.

This leads us to the concept of super-resolution. We aim to recover the level of resolution set by the microscope, but by using a time series of low resolution— viz. low dose—images.

The standard way of producing high resolution reconstructions from a series of low resolution/noisy images is classically formulated as a global model (with local noise <span>\\( \boldsymbol{n} \\)</span>) of the form

<div>
	\begin{equation} \label{eq:1}
	\boldsymbol{y}_t = (D \cdot B_t \cdot M_t) \boldsymbol{x} + \boldsymbol{n}_t
	\end{equation}
</div>

where <span>\\( \boldsymbol{x} \\)</span> is the desired high-resolution image which is assumed constant during the acquisition of the multiple micrographs, except for any motion and degradation allowed by the model. Therefore, the observed low-resolution images result from warping (<span>\\( M_t \\)</span>), blurring (<span>\\( B_t \\)</span>), and sub-sampling (<span>\\( D \\)</span>) operators performed on <span>\\( \boldsymbol{x} \\)</span>. It is also assumed that each micrograph is corrupted by additive noise <span>\\( \boldsymbol{n}_t \\)</span> only.

Unfortunately, this paradigm is not applicable in this form: Tracking and estimating the motion by a sufficiently accurate model <span>\\( M_t \\)</span> in <span>\\( \eqref{eq:1} \\)</span> based on low resolution possibly very noisy data, is not feasible. Thus, standard super-resolution concepts as described above that are based on registration and motion tracking are not applicable.

We propose an alternative strategy that is motivated by the above observations and can be summarized as follows:

* *Time Series:* As before, a high resolution image is to be recovered from a timeseries of HAADF STEM micrographs <span>\\( \boldsymbol{y}_t \\)</span> of the same object, where the time <span>\\( t \\)</span> is the frame index and runs through a finite set.
* *The key tool:* Denoising based on time series is based on averaging the same specimen portion appearing in different frames. As explained above it is impossible to identify such portions from the low resolution frames. It is therefore crucial to employ a technique that avoids an explicit registration and motion tracking. The concept of nonlocal means, developed by Buades, Coll and Morel in [BCM05] as a denoising algorithm, offers exactly this property. The key point is to average image portions whose intensity distributions are close to each other. This can be done as follows: With every pixel position <span>\\( p \\)</span> we associate a neighborhood <span>\\( N_p \\)</span> centered at <span>\\( p \\)</span> as well as a (small) patch <span>\\( R(p,t) \\)</span> in the frame <span>\\( \boldsymbol{y}_t \\)</span> also centered at <span>\\( p \\)</span>. We wish to produce an updated (target) value <span>\\( \boldsymbol{z}(p,t) \\)</span> at position <span>\\( p \\)</span> in the frame at <span>\\( t \\)</span> from source values <span>\\( \boldsymbol{y}(p,t) \\)</span> at positions <span>\\( p \\)</span> in a (usually different) frame at <span>\\( t \\)</span> by computing
	<div>
	\begin{equation*}
	\boldsymbol{z}(p,t) = \displaystyle{\frac{\sum_{p' \in N_p, t' \in N_t} \omega(p,p',t,t') \boldsymbol{y}(p',t')}{\sum_{p' in N_p, t' \in N_t} \omega(p,p',t,t')}}
	\end{equation*}
	</div>
where <span>\\( N_t \\)</span> denotes a time neighborhood of <span>\\( t \\)</span>, i.e. a collection of timewise neighboring frames that are to be taken into account for the averaging process.  Here the weights <span>\\( \omega(p,p',t,t') \\)</span> have the form
	<div>
	\begin{equation*}
	\omega(p,p',t,t') = \exp \left\{ - \frac{\text{dist} \big( R(p,t), R(p',t') \big)}{2h^2} \right\},
	\end{equation*}
	</div>
where <span>\\( h \\)</span> is a filtering parameter that is thought to be solely related to the variance of the noise corrupting the data, and the distance between two patches quantify the *similarity* between those patches.  The distance notion is a crucial parameter of such a scheme which, in particular, allows us to incorporate knowledge about data acquisition and special artifacts.
* *A two-stage approach:* Nonlocal means alone does not yet provide super-resolution. On the one hand, it should be complemented by a deblurring step. On the other hand, in order to exploit the full potential of nonlocal means we propose an iterated averaging procedure. This procedure may be viewed as gradually refining the image formation in HAADF STEM and modeling the distortions encountered during the imaging process.

#### Modeling the impact of ebola and bushmeat hunting on Western Lowland Gorillas.

The 2003 outbreak of ebola in the Republic of Congo killed 114 people and up to 800 western lowland gorillas. This outbreak and all outbreaks between 2001–2003 began with human handling of infected animal carcasses. Ebola has since spread, putting the entire gorilla population at risk.

We presented an epidemiological model in [RBSG07] to describe the combined effects of ebola and hunting on persistence of gorillas. This model is initially based on dynamical systems, more concretely on the so-called SIR models (Susceptible- Infected-Recovered). For the numerical solution of the system, we employed solving techniques that account for environmental stochasticity (in the form of future ebola outbreaks).

<p style="text-align:center;"><img src="https://i0.wp.com/farm6.static.flickr.com/5162/5201886578_b0dc28ee08_b_d.jpg" />
<p style="text-align:center;"><img src="https://i0.wp.com/farm5.static.flickr.com/4092/5201304021_bc45756b22_o_d.jpg" />

<script type="text/x-mathjax-config">
  MathJax.Hub.Config({ TeX: { equationNumbers: {autoNumber: "all"} } });
</script>

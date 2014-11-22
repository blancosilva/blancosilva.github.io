---
layout: post
title: Basic examples of Maximum Likelihood Estimation
date: 2011-01-14 10:24:08.000000000 -05:00
category: post
comments: true
---

In this post, we see how to use maximum likelihood to estimate the best parameters for a few of the most common distributions.

## Estimation of best parameter for iid Exponential Distributions

Let <span>\\( X_1, X_2, \dotsc, X_m \\)</span> be a random sample from the exponential distribution with probability density functions of the form <span>\\( f_\theta(x) = \tfrac{1}{\theta}e^{-x/\theta} \\)</span> for <span>\\( x &gt;0 \\)</span> and any parameter <span>\\( \theta &gt;0. \\)</span>  The likelihood function is then given as the product

<div>
	\begin{equation}
	\mathcal{L}(\theta; x_1,\dotsc, x_m) = f_\theta(x_1)\dotsb f_\theta(x_m) = \dfrac{1}{\theta^m} \exp \bigg( -\dfrac{1}{\theta} \sum_{k=1}^m x_k \bigg)
	\end{equation}
</div>

We look for the parameter value <span>\\( \theta&gt;0 \\)</span> that offers an absolute maximum of <span>\\( \mathcal{L}. \\)</span>  Notice that, since the logarithm is a one-to-one increasing function, the maximum of <span>\\( \mathcal{L} \\)</span> coincides with the maximum of <span>\\( \log\mathcal{L}. \\)</span>  The latter expression is easier to handle than the former, so we use this one to look for the extrema in the usual way:

Set <span>\\( g(\theta) = \log \mathcal{L}(\theta; x_1, \dotsc, x_m) = -m \log(\theta) - \tfrac{1}{\theta} \sum_{k=1}^m x_k; \\)</span> it is then <span>\\( g'(\theta) = -\tfrac{m}{\theta} - \tfrac{1}{\theta^2}\sum_{k=1}^m x_k. \\)</span>  Note that <span>\\( g'(\theta) = 0 \\)</span> if and only if <span>\\( \theta = \tfrac{1}{m} \sum_{k=1}^m x_k, \\)</span> which happens to be positive and actually a maximum of <span>\\( \mathcal{L}(\theta;x_1,\dotsc,x_m). \\)</span>

Note that the found parameter <span>\\( \theta \\)</span> is nothing but the arithmetic mean <span>\\( \bar{x} \\)</span> of <span>\\( \{x_1, \dotsc, x_m\}. \\)</span>

## Estimation of best parameter for iid Geometric Distributions

In this case, the random sample <span>\\( X_1, \dotsc, X_m \\)</span> for the Geometric distribution has probability density functions of the form <span>\\( f_p(n) = p (1-p)^{n-1} \\)</span> for any <span>\\( n \in \mathbb{N} \\)</span> and parameter <span>\\( p \in [0,1]. \\)</span>  We operate as in the previous example, by looking for extrema of the log-likelihood function:

* Set <span>\\( \mathcal{L}(p;n_1,\dotsc,n_m) = p^m (1-p)^{-m+n_1+\dotsb+n_m} \\)</span> for <span>\\( 0 \leq p \leq 1. \\)</span>
* Consider <span>\\( g(p) = \log \mathcal{L}(p;n_1, \dotsc, n_m) = m\log(p) + \bigg( -m + \displaystyle{\sum_{k=1}^m} n_k \bigg) \log(1-p), \\)</span> but only for <span>\\( 0&lt;p&lt;1. \\)</span>
* It is then <span>\\( g'(p) = \dfrac{m}{p} - \dfrac{1}{1-p}\bigg( -m + \displaystyle{\sum_{k-1}^m} n_k\bigg) \\)</span>
* <span>\\( g'(p) = 0 \\)</span> if and only if <span>\\( p =\dfrac{m}{\sum_{k=1}^m n_k}. \\)</span>

This time, the solution <span>\\( p \\)</span> coincides with the *inverse* of the arithmetic mean <span>\\( \bar{n} \\)</span> of the samples <span>\\( \{n_1, \dotsc, n_m\} \\)</span> (which is trivially positive and less than one).  It is not hard to prove that this critical point is a maximum, and therefore is the parameter that we are looking for.

## Estimation of best parameter for iid Poisson Distributions

The random variables in this case have probability density functions given by <span>\\( f_\lambda(n) = \dfrac{\lambda^n e^{-\lambda}}{n!} \\)</span> for any <span>\\( n \in \mathbb{N}, \\)</span> and parameter <span>\\( \lambda&gt;0. \\)</span>

* Set <span>\\( \mathcal{L}(\lambda;t_1,\dotsc,t_m) = e^{-m\lambda} \dfrac{\lambda^{n_1+\dotsb+n_m}}{n_1! \dotsb n_m!}. \\)</span>
* Set <span>\\( g(\lambda) = \log \mathcal{L}(\lambda; n_1, \dotsc, n_m) = -m\lambda -\log (n_1! \dotsb n_m!)+(\log \lambda) \displaystyle{\sum_{k=1}^m} n_k . \\)</span>
* Its derivative is given by <span>\\( g'(\lambda) = -m + \dfrac{1}{\lambda} \displaystyle{\sum_{k=1}^m} n_k. \\)</span>
* Note that <span>\\( g'(\lambda) = 0 \\)</span> only for <span>\\( \lambda = \dfrac{1}{m} \displaystyle{\sum_{k=1}^m} n_k, \\)</span> which is trivially a maximum for <span>\\( \mathcal{L}. \\)</span>

As in the case of exponential distributions, the computed parameter <span>\\( \lambda \\)</span> is  the arithmetic mean <span>\\( \bar{n} \\)</span> of <span>\\( \{n_1, \dotsc, n_m\}. \\)</span>

## Estimation of best parameter for iid Normal Distributions

This case is a bit different, since we are dealing with two parameters instead of one: Assume <span>\\( X_1, X_2, \dotsc, X_m \\)</span> is a random sample from the normal distribution with probability density functions of the form <span>\\( f_{\mu,\sigma}(t) = (2\pi\sigma^2)^{-1/2} \exp \big( - \tfrac{(t-\mu)^2}{2\sigma^2} \big) \\)</span> for any <span>\\( t \in \mathbb{R}, \\)</span> and parameters <span>\\( \mu,\sigma \in \mathbb{R}. \\)</span>  For ease of computations below, and since the parameter <span>\\( \sigma \\)</span> appears always squared on the expression of <span>\\( f \\)</span>, we prefer to work instead with <span>\\( f_{\mu,\theta}(t) = (2\pi\theta)^{-1/2} \exp \big( - \tfrac{(t-\mu)^2}{2\theta} \big), \\)</span> and require the parameter <span>\\( \theta \\)</span> to be non-negative.  Note the abuse of notation, and how this does not really affect the final result.  We proceed to compute the likelihood function and its logarithm as before:

* <span>\\( \mathcal{L}(\mu,\theta;t_1,\dotsc,t_m) = \bigg( \dfrac{1}{\sqrt{2\pi\theta}} \bigg)^m \exp \bigg(  \dfrac{1}{2\theta} \displaystyle{\sum_{k=1}^m} (t_k-\mu)^2 \bigg) \\)</span>
* <span>\\( g(\mu,\theta) = \log\mathcal{L}(\mu,\theta;t_1,\dotsc,t_m) = -\dfrac{m}{2}\log(2\pi\theta) - \dfrac{1}{2\theta} \displaystyle{\sum_{k=1}^m} (t_k-\mu)^2. \\)</span>
* The partial derivatives of <span>\\( g \\)</span> are given by
    <div>
	\begin{equation}
	\dfrac{\partial g}{\partial \mu}(\mu,\theta) = \dfrac{1}{\theta} \displaystyle{\sum_{k=1}^m} (t_k - \mu),\qquad \dfrac{\partial g}{\partial \theta}(\mu,\theta) = -\dfrac{m}{2\theta} + \dfrac{1}{2\theta^2} \displaystyle{\sum_{k=1}^m} (t_k-\mu)^2
	\end{equation}
    </div>
* Note that <span>\\( \dfrac{\partial g}{\partial \mu}(\mu,\theta) = 0 \\)</span> if and only if <span>\\( \mu = \dfrac{1}{m} \displaystyle{\sum_{k=1}^m} t_k. \\)</span>  Let us denote it by <span>\\( \bar{t}, \\)</span> since it represents the mean of the values <span>\\( \{ t_1, \dotsc, t_m \}. \\)</span>
* Also, by virtue of the previous statement, a solution for <span>\\( \dfrac{\partial g}{\partial \theta}(\mu,\theta) = 0 \\)</span> is given uniquely by <span>\\( \theta = \dfrac{1}{m} \displaystyle{\sum_{k=1}^m} \big(t_k - \bar{t}\big)^2 \\)</span>.  Note that this value (which is positive, and hence satisfies the constraints) coincides with the variance <span>\\( s^2 \\)</span> of the set <span>\\( \{ t_1, \dotsc, t_m\}. \\)</span>  It is a priori a valid parameter for <span>\\( \theta. \\)</span>
* It is not hard to see that the computed critical point <span>\\( (\mu,\theta) = (\bar{t}, s^2) \\)</span> offers indeed an absolute maximum for <span>\\( \log\mathcal{L}(\mu,\theta;t_1,\dotsc,t_m). \\)</span>  Indeed, the Hessian of <span>\\( g \\)</span> is given by:
    <div>
    \begin{align}
    H(g)(\mu,\theta) &= \begin{pmatrix} \tfrac{\partial^2 g}{\partial \mu^2} &amp; \tfrac{\partial^2 g}{\partial \mu \partial \theta} \\ \tfrac{\partial^2 g}{\partial \theta \partial \mu} &amp; \tfrac{\partial^2 g}{\partial \theta^2}\end{pmatrix} \bigg\rvert_{(\mu,\theta)=(\bar{t},s^2)} \\
    &= \begin{pmatrix} -m/\theta &amp; -\sum_{k=1}^m (t_k-\mu)/\theta^2 \\ -\sum_{k=1}^m (t_k-\mu)/\theta^2 &amp; m/(2\theta^2) - \sum_{k=1}^m (t_k-\mu)^2/\theta^3 \end{pmatrix} \bigg\rvert_{(\mu,\theta)=(\bar{t},s^2)} \\
    &= \begin{pmatrix} -m/s^2 &amp; 0 \\ 0 &amp; -m/(2s^4) \end{pmatrix}.
    \end{align}
	</div>
Its determinant at <span>\\( (\mu,\theta) = (\bar{t},s^2) \\)</span> is always positive: <span>\\( \det H(g)(\bar{t},s^2) = \dfrac{m^2}{2s^6}, \\)</span> and since <span>\\( \dfrac{\partial^2 g}{\partial \mu^2}(\bar{t},s^2) = -\dfrac{m}{s^2} \\)</span> is always negative, a maximum is attained.

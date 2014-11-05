---
layout: post
title: The hunt for a Bellman Function.
date: 2008-09-26 21:22:00.000000000 -04:00
category: post
comments: true
image:
  teaser: "http://farm3.static.flickr.com/2602/4047407579_8397368be9_o.jpg"
---

This is a beautiful and powerful mathematical technique in Harmonic Analysis that allows, among other things, to prove very complicated inequalities in the theory of **Singular Integral Operators**, without using much of the classical machinery in this field.

The Bellman function was the tool that allowed their creators (Fedor Nazarov and <a href="http://www.math.brown.edu/~treil">Sergei Treil</a>) to crack the problem of **weighted norm inequalities with matrix weights for the case <span>\\( \boldsymbol{p} \neq \boldsymbol{2} \\)</span>** and finally solve it completely.

Copies of the original paper can be found at the authors' pages; e.g. [<a href="http://www.math.brown.edu/~treil/papers/bellman/bell3.ps">www.math.brown.edu/~treil/papers/bellman/bell3.ps</a>] (notice the postscript file is huge, as the article has more than 100 pages).

Let me illustrate the use of Bellman functions to solve a simple problem:


> **Dyadic-<span>\\( \boldsymbol{L}_\mathbf{2}(\mathbb{R}) \\)</span> version of the Carleson Imbedding Theorem**
>
> Let <span>\\( \mathcal{D} \\)</span> be the set of all dyadic intervals of the real line.  Given a function <span>\\( f \in L_1^{\text{loc}}(\mathbb{R}) \\)</span>, consider the averages <span>\\( \langle f \rangle_I = \lvert I\rvert^{-1} \int_I f \\)</span>,  on each dyadic interval <span>\\( I \in \mathcal{D} \\)</span>.
>
>Let <span>\\( \{ \mu_I \geq 0 \colon I \in \mathcal{D} \} \\)</span> be a family of non-negative real values satisfying the *Carleson measure condition*—that is, for any dyadic interval <span>\\( I \in \mathcal{D} \\)</span>, <span>\\( \sum_{J \subset I, J~\text{dyadic}} \mu_J \leq \lvert I \rvert. \\)</span>
>
>Then, there is a constant <span>\\( C > 0 \\)</span> such that for any <span>\\( f \in L_2(\mathbb{R}) \\)</span>,
>
><div>
>  \begin{equation*}
> \displaystyle{\sum_{ I \in \mathcal{D} } \mu_I \lvert \langle f \rangle_{I} \rvert^2 \leq C \lVert f \rVert_{L_2(\mathbb{R})}^2}
> \end{equation*}
> </div>
>

Fix a dyadic interval <span>\\( I \in \mathcal{D} \\)</span>, and a vector <span>\\( (x_1, x_2, x_3) \in \mathbb{R}^3 \\)</span>.  Consider all families <span>\\( \{\mu_I \colon I \in \mathcal{D} \} \\)</span> satisfying the Carleson condition

<div>
\begin{equation*}
 \frac{1}{\lvert J \rvert} \displaystyle{\sum_{K \subset J}} \mu_{K} \leq 1, \text{ for all }J \in \mathcal{D}
 \end{equation*}
</div>

and such that

<div>
\begin{equation}
\frac{1}{\lvert I \rvert} \sum_{J \subset I} \mu_J = x_1 \label{(eq1)}
\end{equation}
</div>

Also, consider all functions <span>\\( f \in L_2(\mathbb{R}) \\)</span> for which the following quantities are fixed:

<div>
\begin{align}
\langle f^2 \rangle_I &= \frac{1}{\lvert I \rvert} \int_I f^2 = x_2, &\langle f \rangle_I &= \frac{1}{\lvert I \rvert} \int_I f = x_3 \label{(eq2)}
\end{align}
</div>

If we believe that the Theorem is true, then the quantity

<div>
  \begin{equation*}
 \displaystyle{\mathcal{B}(x_1,x_2,x_3)=\frac{1}{\lvert I \rvert} \sup \bigg\{ \sum_{J \subset I} \mu_J \langle f \rangle^2_J \colon f, \{ \mu_I \} \text{ satisfy }\eqref{(eq1)}, \eqref{(eq2)} \bigg\}} 
 \end{equation*}
</div>

is finite and, moreover, satisfies the inequality <span>\\( \mathcal{B}(x_1,x_2,x_3) \leq C x_2 \\)</span>.

Since <span>\\( \mathcal{B}(x_1,x_2,x_3) \\)</span> does not depend on the choice of an interval <span>\\( I \in \mathcal{D} \\)</span>, we obtain a function of three real variables; this is the *Bellman function associated with the Carleson Imbedding Theorem*.

Notice that:

1. The domain of <span>\\( \mathcal{B} \\)</span> is the set <span>\\( \{ (x_1, x_2, x_3) \in \mathbb{R}^3 \colon 0 \leq x_1 \leq 1, x_3^2 \leq x_2 \}. \\)</span>
2. For each <span>\\( (x_1,x_2,x_3) \\)</span> in the domain of <span>\\( \mathcal{B} \\)</span>, it is <span>\\( 0 \leq \mathcal{B}(x_1, x_2, x_3) \leq C x_2. \\)</span>
3.  If <span>\\( 0 \leq \lambda \leq x_1 \\)</span>, then

    <span>\\( \mathcal{B}(x_1, x_2, x_3)\geq \lambda x_2^2 + \frac{1}{2} \big\{ \mathcal{B}(x_1^+, x_2^+, x_3^+) + \mathcal{B}(x_1^-, x_2^-, x_3^-)\big\} \\)</span>

    whenever the triples <span>\\( (x_1,x_2,x_3) \\)</span>, <span>\\( (x_1^+,x_2^+,x_3^+) \\)</span> and <span>\\( (x_1^-,x_2^-,x_3^-) \\)</span> belong to the domain and

    * <span>\\( x_1 = (x_1^+ + x_1^-)/2 + \lambda \\)</span>,
    * <span>\\( x_2 = (x_2^+ + x_2^-)/2 \\)</span>,
    * <span>\\( x_3 = (x_3^+ + x_3^-)/2. \\)</span>

The entire machine can be run backward: if we have any function <span>\\( \mathcal{B} \\)</span> of three real variables that satisfies properties 1—3, the proof of the Theorem follows immediately. The key property 3 is not very pleasant to verify.  Fortunately, this condition can be replaced by "infinitesimal" conditions (conditions on derivatives), which are easier to check:  If <span>\\( x_1 = \frac{1}{2}(x_1^+ + x_1^-) \\)</span>, <span>\\( x_2 = \frac{1}{2}(x_2^+ + x_2^-) \\)</span> and <span>\\( x_3 = \frac{1}{2}(x_3^+ + x_3^-) \\)</span>, and all triples are in the domain of <span>\\( \mathcal{B} \\)</span>, then the key property 3 implies the concavity of <span>\\( \mathcal{B} \\)</span>:

<div>
  \begin{equation*}
 \mathcal{B}(x_1,x_2,x_3) \geq \frac{1}{2} \big\{ \mathcal{B}(x_1^+,x_2^+,x_3^+) + \mathcal{B}(x_1^-,x_2^-,x_3^-)\big\}
 \end{equation*}
</div>

and furthermore,

<div>
  \begin{equation}
  d^2 \mathcal{B} \leq 0, \qquad \frac{\partial \mathcal{B}}{\partial x_1} \geq x_3^2 \label{(eq3)}
  \end{equation}
</div>

Notice that condition 3 is equivalent to <span>\\( \eqref{(eq3)} \\)</span>. The following function satisfies 1, 2 and <span>\\( \eqref{(eq3)} \\)</span>, and thus the Theorem is proven for  <span>\\( C=4 \\)</span>.

<div>
  \begin{equation*}
 \mathcal{B}(x_1, x_2, x_3) = 4\bigg( \displaystyle{x_2 - \frac{x_3^2}{1+x_1}}\bigg)
\end{equation*}
</div>

<script type="text/x-mathjax-config">
  MathJax.Hub.Config({ TeX: { equationNumbers: {autoNumber: "all"} } });
</script>

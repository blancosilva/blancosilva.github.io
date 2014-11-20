---
layout: page
title: Distributions.  Definition and Basic Properties
date: 2010-09-27 22:44:33.000000000 -04:00
category: course-material
topic: distributions 
comments: true
---

Let <span>\\( X \subset \mathbb{R}^d \\)</span> be an open set.  A linear form <span>\\( \nu \colon C_c^\infty(X) \to \mathbb{C} \\)</span> is called a <strong>distribution</strong> if, for every compact set <span>\\( K \subset X \\)</span>, there is a real number <span>\\( C \geq 0 \\)</span> and a non-negative integer <span>\\( N \\)</span> such that for all <span>\\( \phi \in C_c^\infty(X) \\)</span> with <span>\\( \text{supp } \phi \subset K \\)</span>,

<div>
	\begin{equation}
	\lvert \langle \nu, \phi \rangle \rvert \leq C \displaystyle{\sum_{\lvert \alpha \rvert \leq N} \sup \lvert \partial^\alpha \phi \rvert}
	\end{equation}
</div>

The vector space of distributions on <span>\\( X \\)</span> is denoted by <span>\\( \mathcal{D}'(X) \\)</span>.

The support of a distribution <span>\\( \nu \in \mathcal{D}'(X) \\)</span>, written <span>\\( \text{supp }\nu \\)</span>, is by definition the complement of the set <span>\\( \big\{ x \in X : \nu = 0 \text{ in a neighborhood of } x \big\} \\)</span>.

### Sequencial continuity.

A linear form <span>\\( \nu \\)</span> on <span>\\( C_c^\infty(X) \\)</span> is a distribution if and only if <span>\\( \lim_n \langle \nu, \phi_n \rangle = 0 \\)</span> for every sequence <span>\\( \big\{ \phi_n \big\}_{n \in \mathbb{N}} \\)</span> which converges to zero in <span>\\( C_c^\infty(X) \\)</span>.

### Localization

Let <span>\\( X \subset \mathbb{R}^d \\)</span> be an open set, and let <span>\\( \big\{ X_\lambda \big\}_{\lambda \in \Lambda} \\)</span> be an open cover of <span>\\( X \\)</span> (where <span>\\( \Lambda \\)</span> is an index set).  Suppose that, for each <span>\\( \lambda \in \Lambda \\)</span> there is a distribution <span>\\( \nu_\lambda \in \mathcal{D}'(X_\lambda) \\)</span> and that

<div>
\begin{equation}
\nu_\lambda = \nu_\mu \text{ on } X_\lambda \cap X_\mu \text{ if } X_\lambda \cap X_\mu \neq \emptyset.
\end{equation}
</div>

Then there is a unique distribution <span>\\( \nu \in \mathcal{D}'(X) \\)</span> such that <span>\\( \nu = \nu_\lambda \\)</span> in <span>\\( X_\lambda \\)</span> for each <span>\\( \lambda \in \Lambda. \\)</span>

### Influence of supports

Let <span>\\( \nu \in \mathcal{D}'(X) \\)</span> and let <span>\\( \phi \in C_c^\infty(X). \\)</span>  If the supports of <span>\\( \nu \\)</span> and <span>\\( \phi \\)</span> are disjoint, then <span>\\( \langle \nu, \phi \rangle = 0. \\)</span>

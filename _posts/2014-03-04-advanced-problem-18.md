---
layout: post
title: 'Advanced Problem #18'
category: post
---
Another fun problem, as requested by <a href="https://www.facebook.com/right.li.love">Qinfeng Li</a> in <a href="http://blancosilva.wordpress.com/teaching/ma598r/">MA598R: Measure Theory</a>

> Let   \\(f \in L_2(\mathbb{R})\\) so that \\(g(x)=xf(x) \in L_2(\mathbb{R})\\) too.  Show that \\(f \in L_1(\mathbb{R})\\) and \\(\lVert f \rVert_1^2 \leq 8 \lVert f \rVert_2 \lVert g \rVert_2.\\)

I got this problem by picking some strictly positive value \\(\lambda\\) and breaking the integral \\(\int_{\mathbb{R}} \lvert f \rvert\, d\mu\\) as follows:

$$\begin{array}{rl} \displaystyle{\int_{\mathbb{R}} \lvert f \rvert\, d\mu} &= \displaystyle{\int_{\lvert x \rvert \leq \lambda} \lvert f \rvert\, d\mu + \int_{\lvert x \rvert \geq \lambda} \lvert f \rvert\, d\mu} \\ \\
 &= \displaystyle{\int_{-\lambda}^{\lambda} \lvert f \rvert\, d\mu + \int_{\lvert x \rvert \geq \lambda} \tfrac{1}{\lvert x \rvert} \lvert g(x) \rvert\, d\mu} \\ \\
&= \displaystyle{\int_\mathbb{R} \lvert f \rvert \cdot \boldsymbol{1}_{\lvert x \rvert \leq \lambda}\, d\mu + \int_{\mathbb{R}} \lvert g \rvert \cdot  \big( \tfrac{1}{\lvert x \rvert} \boldsymbol{1}_{\lvert x \rvert \geq \lambda}\big) \, d\mu} \\ \\
&\leq \lVert f \rVert_2 \cdot \big\lVert \boldsymbol{1}_{\lvert x \rvert \leq \lambda} \big\rVert_2 + \lVert g \rVert_2 \cdot \big\lVert \tfrac{1}{\lvert x \rvert} \boldsymbol{1}_{\lvert x \rvert \geq \lambda} \big\rVert_2 \end{array}$$


Let us examine now the factors $$\big\lVert \boldsymbol{1}_{\lvert x \rvert \leq \lambda} \big\rVert_2$$ and \\( \big\lVert \tfrac{1}{\lvert x \rvert} \boldsymbol{1}_{\lvert x \rvert \geq \lambda} \big\rVert_2 \\) above:


$$\big\lVert \boldsymbol{1}_{\lvert x \rvert \leq \lambda} \big\rVert_2 = \sqrt{2\lambda}$$

$$\big\lVert \tfrac{1}{\lvert x \rvert} \boldsymbol{1}_{\lvert x \rvert \geq \lambda} \big\rVert_2 = \displaystyle{ \sqrt{ 2\int_\lambda^\infty \dfrac{dx}{x^2}} = \sqrt{ \dfrac{2}{\lambda}} }$$

We have thus proven that \\(f \in L_1(\mathbb{R})\\) with \\(\lVert f \rVert_1 \leq \sqrt{2\lambda} \lVert f \rVert_2 + \sqrt{\tfrac{2}{\lambda}} \lVert g \rVert_2.\\)  At this point, all you have to do is pick \\(\lambda = \lVert g \rVert_2 / \lVert f \rVert_2\\) (provided the denominator is not zero) and you are done.

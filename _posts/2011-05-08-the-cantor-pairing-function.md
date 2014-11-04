---
layout: post
title: The Cantor Pairing Function
date: 2011-05-08 07:33:30.000000000 -04:00
category: post
comments: true
image:
  teaser: "http://farm6.static.flickr.com/5142/5698724857_7e20970586_o.jpg"
---

The objective of this post is to construct a pairing function, that presents us with a bijection between the set of natural numbers, and the lattice of points in the plane with non-negative integer coordinates.

<div>
	\begin{equation}
	\pi\colon \mathbb{N} \cup \{ 0 \} \to \big( \mathbb{N} \cup \{ 0 \} \big)^2.
	\end{equation}
</div>

We will accomplish this by creating the corresponding map (and its inverse), that takes each natural number <span>\\( z \\)</span> and drops it at a location in the lattice, as the following diagram suggests:

<p style="text-align:center;">
<a href="http://www.flickr.com/photos/eseprimo/5698724857/" title="gCpf by eseprimo, on Flickr"><img src="http://farm6.static.flickr.com/5142/5698724857_7e20970586_o.jpg" width="370" height="364" alt="gCpf" /></a>
</p>

That is: the zero goes at the origin, and then we populate the two positions in the diagonal <span>\\( x+y=1 \\)</span>.  Then we populate the three positions in the diagonal <span>\\( x+y=2 \\)</span>, and so on.  Note that by doing so, when we are done populating the last <span>\\( n+1 \\)</span> positions of the <span>\\( n \\)</span>–th diagonal, we have placed <span>\\( 1+2+3+\dotsb+(n+1) = \tfrac{(n+1)(n+2)}{2} \\)</span> natural numbers (including the zero!) in the lattice.

In particular, note that the triangular numbers <span>\\( t_n = 1 + 2 + \dotsb + n \\)</span> occupy all the positions in the <span>\\( x \\)</span>–axis, precisely where this one intersects the lines <span>\\( x+y=n\\)</span>.

This is the key ingredient to construct the required bijection: Given a natural number <span>\\( z \in \mathbb{N}, \\)</span> there is a **unique** value <span>\\( n = n(z) \\)</span> such that <span>\\( t_n \leq z < t_{n+1} \\)</span> (since the sequence of triangular numbers is strictly increasing).  The number <span>\\( z \\)</span> then belongs to the intersection of the lattice with the diagonal line <span>\\( x+y=n, \\)</span> and it only remains to know how far from the <span>\\( x \\)</span>–axis: the **offset** <span>\\( z-t_n \\)</span> actually indicates the <span>\\( y \\)</span> coordinate of the position of <span>\\( z \\)</span> in the lattice.  We can now find the precise position of <span>\\( z \\)</span> by solving the following simple system of two equations with two variables:

<div>
\begin{equation}
 \left\{ \begin{array}{rl} x+y &amp;= n(z)\\ y &amp;= z - t_{n(z)} \end{array}\right. 
\end{equation}
</div>

Or simply put, the coordinates are given by <span>\\( x=n(z)-z+t_{n(z)} \\)</span>, <span>\\( y=z-t_{n(z)}. \\)</span>  The question remaining is, of course, how to find the value of <span>\\( n(z). \\)</span>

We need to look for the value of <span>\\( n \\)</span> such that

<div>
\begin{equation}
 \displaystyle{\frac{n(n+1)}{2}} \leq z < \displaystyle{\frac{(n+1)(n+2)}{2}}. 
\end{equation}
</div>

One way to accomplish this is to find the closest natural number <span>\\( n \\)</span> to the solution of either side of the inequalities above, say <span>\\( n^2 + n -2z = 0. \\)</span>  By choosing this side, an appropriate expression for this value is given by

<div>
\begin{equation}
 n(z) = \big\lfloor \frac{-1+\sqrt{1+8z}}{2} \big\rfloor. 
\end{equation}
</div>

We have successfully computed for each natural number <span>\\( z \in \mathbb{N} \cup \{ 0 \} \\)</span> a unique position in the lattice <span>\\( \big( \mathbb{N} \cup \{ 0 \}\big)^2. \\)</span>  The construction is also such that for each position <span>\\( (x,y) \\)</span> in the previous lattice, there is a unique natural number that can be sent to that position.  The corresponding expression will lead us to the construction of the inverse function <span>\\( \pi^{-1} \colon \big( \mathbb{N} \cup \{ 0 \} \big)^2 \to \mathbb{N} \cup \{ 0 \}. \\)</span>  The key is again the same system of equations as before:

Given <span>\\( (x,y), \\)</span> we find <span>\\( n=x+y. \\)</span>  This leads us to compute the corresponding <span>\\( t_n, \\)</span> and the second equations gives us

<div>
\begin{equation}
 z = y + t_n = y + \displaystyle{\frac{n(n+1)}{2}} = \underbrace{y + \displaystyle{\frac{(x+y)(x+y+1)}{2}}}_{\pi^{-1}(x,y)}. 
\end{equation}
</div>

### Miscellaneous

Antoine Flattot suggests using this construction to find a proof that the natural numbers are also in bijection with the rational numbers, and thus they both have the same cardinality.  How would the reader go about it?

Also, by using either function above we can obtain elegant diagrams in <span>\\( \LaTeX \\)</span> with the `tikz` package, showing graphically the structure of the location assignments.  For example, with the choice of <span>\\( \pi, \\)</span> we could write a simple function to assign all <span>\\( z+1 \\)</span> positions from 0 to <span>\\( z, \\)</span> including arrows pointing the direction in which the sequence progresses:

{% highlight latex linenos %}
\def\gCpf#1{
% Compute the maximum width of the box that contains all values
% from 0 to #1
\pgfmathparse{0.5+floor(0.5*(sqrt(8*#1+1)-1))}
\let\width\pgfmathresult
% Generate a grid with the corresponding width
\draw (-0.25cm,-0.25cm) grid[step=2cm,ultra thin,gray]
	(2*\width cm+0.25cm, 2*\width cm+0.25cm);
\foreach \x in {0,...,\width} {
	\draw[gray,ultra thin] (2*\x,0.2cm-0.25cm) --
		(2*\x, -0.2cm-0.25cm) node[below]
		{\large $\boldsymbol{\x} $};
	\draw[gray,ultra thin] (0.2cm-0.25cm,2*\x) --
		(-0.2cm-0.25cm,2*\x) node[left]
		{\large $\boldsymbol{\x} $};
% First node, always at the origin
\filldraw(0,0) circle (2pt);
\draw(10pt,8pt) node{\large $0 $};

% For each number z between 1 and #1...
\foreach \n in {1,..., #1}
{
	% Compute the diagonal number n(z) and the previous
	\pgfmathparse{floor(0.5*(sqrt(8*\n+1)-1))}
	\let\thisn\pgfmathresult
	\pgfmathparse{floor(0.5*(sqrt(8*\n-7)-1))}
	\let\prevn\pgfmathresult
	%Compute the triangular number t_n and the previous
	\pgfmathparse{0.5*(\thisn^2+\thisn)}
	\let\thist\pgfmathresult
	\pgfmathparse{0.5*(\prevn^2+\prevn)}
	\let\prevt\pgfmathresult
	% Compute the y coords of this and the previous
	\pgfmathparse{\n-\thist}
	\let\thisy\pgfmathresult
	\pgfmathparse{\n-1-\prevt}
	\let\prevy\pgfmathresult
	% Compute the x coords of this and the previous
	\pgfmathparse{\thisn-\thisy}
	\let\thisx\pgfmathresult
	\pgfmathparse{\prevn-\prevy}
	\let\prevx\pgfmathresult
	% Done.  Let's place the nodes at their locations
	\node (this) at (2*\thisx,2*\thisy) [inner sep=6pt] {};
	\node (prev) at (2*\prevx,2*\prevy) [inner sep=6pt] {};
	\draw (2*\thisx cm+10pt,2*\thisy cm+8pt) node{\large $\n $};
	\filldraw (2*\thisx cm,2*\thisy cm) circle (2pt);
	% If the node belongs in the x-axis, receive a red arrow
	% Otherwise, a black arrow
	\ifthenelse{\lengthtest{\thisy cm = 0 cm}}{
		\draw[->,thick,red] (prev) -- (this);
	}{
		\draw[->] (prev) -- (this);
	}
}
{% endhighlight %}

Note that the <span>\\( \LaTeX \\)</span> libraries `calc` and `ifthen` need to be loaded previously, to be able to handle some of the commands.

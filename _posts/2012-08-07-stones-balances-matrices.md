---
layout: post
title: Stones, balances, matrices
date: 2012-08-07 20:21:31.000000000 -04:00
category: post
comments: true
image:
  teaser: "https://i0.wp.com/farm9.staticflickr.com/8285/7737057646_e02f559a02_o_d.jpg"
---

>We have four stones identical in size and appearance, but one of them is heavier than the rest.  We have a set of scales (a balance): how many weights do we need to determine which stone is the heaviest?

This is a trivial problem, but we will use it to illustrate different ideas, definitions, and the connection to linear algebra needed to answer the harder puzzles below.  Let us start by solving it in the most natural way:

1. Enumerate each stone from 1 to 4.
2. Set stones 1 and 2 on the left plate; set stones 3 and 4 on the right plate.  Since one of the stones is heavier, it will be in the plate that tips the balance.  Let us assume this is the left plate.
3. Discard stones 3 and 4. Put stone 1 on the left plate; and stone 2 on the right plate.  The plate that tips the balance holds the heaviest stone.

This solution finds the stone in two weights.  It is what we call *adaptive measures*: each measure is determined by the result of the previous.  This is a good point to introduce an algebraic scheme to code the solution.

* **The weights matrix**: This is a matrix with four columns (one for each stone) and two rows (one for each weight).  The entries of this matrix can only be <span>\\( -1, 0 \\)</span> or <span>\\( 1, \\)</span> depending whether a given stone is placed on the left plate <span>\\( (1) \\)</span>, on the right plate <span>\\( (-1) \\)</span> or in neither plate <span>\\( (0). \\)</span>  For example, for the solution given above, the corresponding matrix would be

<div>
\begin{equation} W = \begin{pmatrix} 1 & 1 & -1 & -1 \\ 1 & -1 & 0 & 0 \end{pmatrix} \end{equation}
</div>

* **The stones matrix**: This is a square matrix with four rows and columns (one for each stone).  Each column represents a different combination of stones, in such a way that the *n*-th column assumes that the heaviest stone is in the *n*-th position.  The entries on this matrix indicate the weight of each stone.  For example, if we assume that the heaviest stone weights <span>\\( b \\)</span> units, and each other stone weights <span>\\( a \\)</span> units, then the corresponding **stones matrix** is

<div>
\begin{equation} B = \begin{pmatrix} b & a & a & a \\ a & b & a & a \\ a & a & b & a \\ a & a & a & b \end{pmatrix} \end{equation}
</div>

Multiplying these two matrices, and looking at the sign of the entries of the resulting matrix, offers great insight on the result of the measures:

<div>
\begin{equation} \operatorname{sign} \big( W \cdot B \big) = \operatorname{sign} \begin{pmatrix} b-a & b-a & a-b & a-b \\ b-a & a-b & 0 & 0 \end{pmatrix} = \begin{pmatrix} + & + & - & - \\ + & - & 0 & 0 \end{pmatrix} \end{equation}
</div>

Note the columns of this matrix code the behavior of the measures:

* The column <span>\\( \big( \begin{smallmatrix} + \\ + \end{smallmatrix} \big) \\)</span> indicates that the balance tipped to the left in both measures (and therefore, the heaviest stone is the first one)
* The column <span>\\( \big( \begin{smallmatrix} + \\ - \end{smallmatrix} \big) \\)</span> indicates that the heaviest stone is the second one.
* Note that the other two measures can't find the heaviest stone, since this matrix was designed to find adaptively a stone supposed to be either the first or  the second.

Is it possible to design a solution to this puzzle that is not adaptive?  Note the solution with two measures given (in algebraic form) below:

<div>
\begin{equation} \operatorname{sign} \left[ \begin{pmatrix} 1 & 1 & -1 & -1 \\ 1 & -1 & 1 & -1 \end{pmatrix} \cdot B \right] = \begin{pmatrix} + & + & - & - \\ + & - & + & - \end{pmatrix} \end{equation}
</div>

Since each column is different, it is trivial to decide after the experiment is done, which stone will be the heaviest.  For instance, if the balance tips first to the right <span>\\( (-) \\)</span> and then to the left <span>\\( (+) \\)</span>, the heaviest stone can only be the third one.

Let us make it a big harder: Same situation, but now we don't know whether the stone that is different is heavier or lighter.

The solution above is no good: Since we are not sure whether <span>\\( b \\)</span> is greater or smaller than <span>\\( a \\)</span>, we would obtain two sign matrices which are virtually mirror images of each other.

<div>
\begin{equation} \begin{pmatrix} + & + & - & - \\ + & - & + & - \end{pmatrix} \end{equation}</div>

and 

<div>
\begin{equation} \begin{pmatrix} - & - & + & + \\ - & + & - & + \end{pmatrix} \end{equation}
</div>

In this case, in the event of obtaining that the balance tips twice to the left: which would be the different stone?  The first, which is heaviest, or the fourth, which is lightest?  We cannot decide.

One possible solution to this situation involves taking one more measure.  Look at the algebraic expression of the following example, to realize why:

<div>
\begin{equation} \operatorname{sign} \left[ \begin{pmatrix} 1 & 1 & -1 & -1 \\ 1 & -1 & 1 & -1 \\ 1 & -1 & -1 & 1 \end{pmatrix} \cdot B \right] = \begin{pmatrix} + & + & - & - \\ + & - & + & - \\ + & - & - & + \end{pmatrix} 
\end{equation}
</div>

or 

<div>
\begin{equation} \begin{pmatrix} - & - & + & + \\ - & + & - & + \\ - & + & + & - \end{pmatrix} \end{equation}
</div>

In this case there is no room for confusion: if the balance tips three times to the same side, then the different stone is the first one (whether heavier or lighter). The other possibilities are also easily solvable: if the balance tips first to one side, then to the other, and then to the first side, then the different stone is the third one.

The reader will not be very surprised at this point to realize that three (non adaptive) measures are also enough to decide which stone is different (be it heavier or lighter) in a set of twelve similar stones. To design the solution, a good weight matrix with twelve columns and three rows need to be constructed.  The trick here is to allow measures that balance both plates, which gives us more combinations with which to play.  How would the reader design this matrix?

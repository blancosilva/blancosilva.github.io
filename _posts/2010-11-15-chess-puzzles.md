---
layout: post
title: Chess puzzles
date: 2010-11-15 16:12:15.000000000 -05:00
category: post
image:
  teaser: https://i0.wp.com/farm2.static.flickr.com/1257/5179790956_17a83f79fd_b_d.jpg
---

It is no surprise that the game of chess generates such an amount of mathematical puzzles.  The amount of riddles of combinatoric nature alone should have the readers busy for a long while, no matter what their chess strength is.  This is a selection of several puzzles designed with that purpose in mind.

## Gyozo Nagy's "Expensive Armies"

> It is well known that exactly 8 queens can be placed on a chessboard without attacking each other; similarly 8 rooks, or 14 bishops, or 32 knights, or 16 kings.  But, what if we are allowed to mix pieces?
>
> Let us assign values of \\( \frac{1}{8} \\) to a queen; \\( \frac{1}{8} \\) to a rook; \\( \frac{1}{14} \\) to a bishop; \\( \frac{1}{32} \\) to a knight; and \\( \frac{1}{16} \\) to a king.
>
>    * Construct the most expensive army on a chessboard, using any number of these pieces, so that no piece attacks another. (Here "*any number*" includes zero.)
>    * Same thing, but disallowing kings (so our army consists only of queens, rooks, bishops and knights).
>
> Can these mixed armies achieve values greater than one?  In each case give the largest possible value (and a setup achieving it).

For example, the setup on the board below has an army value of

<div>
	\begin{equation}
	\dfrac{1}{8} + 4\cdot\dfrac{1}{8}+0\cdot\dfrac{1}{14}+\dfrac{1}{32}+2\cdot\dfrac{1}{16} =\dfrac{25}{32} = 0.78125
	\end{equation}
</div>

<p style="text-align:center;"><img src="https://i0.wp.com/farm5.static.flickr.com/4110/5179749778_7ea6d796a6_o_d.jpg" alt="" width="50%" /></p>

I found this problem in <a href="http://domino.research.ibm.com/Comm/wwwr_ponder.nsf/challenges/August2003.html"> August 2003 "**Ponder This**" challenge</a> in the pages of `research.ibm.com`.  They offer a couple of solutions (included in the diagram below), and a note indicating that some puzzle solvers used *integer programming* to prove optimality of those.  Note that neither solution uses a single queen.

<p style="text-align:center;"><img src="https://i0.wp.com/farm2.static.flickr.com/1257/5179790956_17a83f79fd_b_d.jpg" alt="" width="100%" /></p>

The diagram on the left shows an example for the first part of the puzzle, with an army of value

<div>
	\begin{equation}
	\dfrac{1}{8} + 6\cdot\dfrac{1}{14}+7\cdot\dfrac{1}{32}+9\cdot\dfrac{1}{16} =\dfrac{299}{224} = 1.3348
	\end{equation}
</div>

The diagram on the right shows an example for the second part of the puzzle, with an army of value

<div>
	\begin{equation}
	4\cdot\dfrac{1}{8} + 8\cdot\dfrac{1}{14}+5\cdot\dfrac{1}{32} =\dfrac{275}{224} = 1.2277
	\end{equation}
</div>

## Martin Gardner's "Minimum and Maximum Attacks"

I found these problems in Martin Gardner's "*The Unexpected Hanging and Other Mathematical Diversions*."  They were posed in the eighteen hundreds, and some variations are still open for optimal solution.

> **The minimum-attack problem**. Place the eight pieces of one color (king, queen, two bishops, two knights, two rooks) on the board so that the *smallest* possible number of squares are under attack.  A piece does not attack the square on which it rests, but of course it may attack squares occupied by other pieces.
>
> **The maximum-attack problem—weak version**.  Place the same eight pieces on the board so that the *largest* possible number of squares are under attack.  In the *weak version*, we do not force both bishops to be on opposite colors.
>
> **The maximum-attack problem—strong version I**.  As before, but forcing the two bishops to be on opposite colors.
>
> **The maximum-attack problem—strong version II**.  As in *strong version I*, but forcing the king into a non-attacked square!

<p style="text-align:center;"><img src="https://i0.wp.com/farm2.static.flickr.com/1415/5179294019_f7899d7343_b_d.jpg" alt="" width="100%" /></p>

## Husserl's "Third-man theme"

> Notice on the board below, the two sole occupants are the kings of opposite sides.  Add a third piece, creating a position that satisfies the following conditions:
>
>    1. Neither king is in check.
>    2. The position can be reached in a legal game.
>    3. It can be proved that neither side has a legal play

<p style="text-align:center;"><img src="https://i0.wp.com/farm5.static.flickr.com/4132/5179928440_d33204db04_o_d.jpg" alt="" width="50%" /></p>

Note the subtlety of the puzzle: we are searching not only for a double stalemate, but one in which neither side can move!  The solution happens to be unique.

## Miscellaneous

All the diagrams in this page are generated in <span>\\( \LaTeX \\)</span> with the package `skak`, by using the command `\fenboard` and the <a href="http://en.wikipedia.org/wiki/Forsyth%E2%80%93Edwards_Notation">Forsyth–Edwards notation</a>.  For example, the first diagram above has the (very simple) code

{% highlight latex linenos %}
\newgame
\fenboard{4Q3/R7/3R4/6N1/7R/1K6/5K2/2R5 w - - 0 0}
\showboard
{% endhighlight %}

The string in the command `\fenboard` is to be interpreted as follows:

* 8-th row: start with four empty squares, then place a white queen (`Q`), followed by three empty squares.
* 7-th row: a white rook (`R`), followed by seven empty squares.
* 6-th row: three empty squares, one white rook, four empty squares.
*  and so on, until the first row, that reads: two empty squares, then a white rook followed by five empty squares.
* The remaining commands (which are optional) indicate that white is to move (`w`), that there are no castling options for neither side (`-`), no *en passant* squares (`-`) no half-moves since the last capture (`0`) and no move number (`0`).

The `skak` package is originally designed to create both an annotated game and its corresponding diagram.  For example, the following annotation of a variant of the Ruy Lopez opening first moves is generated with the simple list of commands included:

<table style="width:100%;border-width:0;">
<tbody>
<tr>
<td style="width:60%;vertical-align:middle;border-width:0;"><img src="https://farm5.static.flickr.com/4124/5179450691_3aafcb88d2_o_d.jpg" alt="" width="100%" /></td>
<td style="width:40%;vertical-align:middle;border-width:0;">
{% highlight latex linenos %}
\newgame
\mainline{1.e4 e5 2.Nf3 Nc6 3.Bb5}
\mainline{3...a6}
(rarely used these days,
\variation{3...Nf6} is more in
fashion since blah blah)

\mainline{4.Ba4}
\vspace{0.25cm}

\showboard
{% endhighlight %}</td>
</tr>
</tbody>
</table>

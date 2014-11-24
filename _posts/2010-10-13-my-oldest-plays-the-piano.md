---
layout: post
title: My oldest plays the piano!
date: 2010-10-13 14:55:41.000000000 -04:00
category: post
comments: true
image:
  teaser: https://farm9.staticflickr.com/8678/15682120759_257ce44a5c_n_d.jpg
---
<div class="well">
	<p>Two old friends, Ernie and Bernie, bump into each other in the street.  It was more than twenty years since they last saw each other, so they decide to spend some time together in a nearby coffee shop, catching up.  At some point, Bernie asks the inevitable: "So, you got married?"</p>

	<p>"Well, yes!"—claims enthusiastically Ernie. "And I have three beautiful children!"</p>

	<p>"That's great, Ernie! And how old are your kids?"—enquired Bernie.</p>

	<p>"I know you are a sucker for puzzles, Bernie, so I will let you figure it out through a few clues.  You should not have any trouble getting it.  First clue: <strong>If you add the ages of my kids, the result is thirteen</strong>"</p>

	<p>"Whoa!  That doesn't help me much, does it?"—complains Bernie. "Couldn't you give me another clue?"</p>

	<p>"Sure, a second clue: <strong>If you multiply their ages together, the result is the same as how much we payed for coffee."</strong></p>

	<p>Bernie scratches his head for a minute, and cannot figure it out yet… Before he complains again, Ernie realizes the mistake, apologizes, and offers Bernie the last clue: "<strong>My oldest plays the piano!"</strong></p>

	<p>Bernie had no trouble finding the ages of the children this time.</p>
</div>

These are all the possible combinations of positive integers <span>\\( x \\)</span>, <span>\\( y \\)</span>, <span>\\( z \\)</span> that add up to thirteen, together with their product:

<div class="row">
	<div class="col-lg-6">
		\begin{equation}
		\begin{array}{|c|c|c||r|} \hline x&amp;y&amp;z&amp; x\cdot y \cdot z \\ \hline 1&amp;1&amp;11&amp;11 \\ \hline 1&amp;2&amp;10&amp;20 \\ \hline 1&amp;3&amp;9&amp;27 \\ \hline 1&amp;4&amp;8&amp;32 \\ \hline 1&amp;5&amp;7&amp;35 \\ \hline 1&amp;6&amp;6&amp;\mathbf{36} \\ \hline 2&amp;2&amp;9&amp;\mathbf{36} \\ \hline \end{array}
		\end{equation}
	</div>
	<div class="col-lg-6">
		\begin{equation}
		\begin{array}{|c|c|c||r|} \hline x&amp;y&amp;z&amp; x\cdot y \cdot z \\ \hline 2&amp;3&amp;8&amp;48 \\ \hline 2&amp;4&amp;7&amp;56 \\ \hline 2&amp;5&amp;6&amp;60 \\ \hline 3&amp;3&amp;7&amp;63 \\ \hline 3&amp;4&amp;6&amp;72 \\ \hline 3&amp;5&amp;5&amp;75 \\ \hline 4&amp;4&amp;5&amp;80 \\ \hline \end{array}
		\end{equation}
	</div>
</div>

Notice that there are only two combinations that offer the same product: <span>\\( (x,y,z) = (1,6,6) \\)</span> and <span>\\( (x,y,z) = (2,2,9) \\)</span>.  The fact that Bernie did not know the answer to the riddle after the second clue, indicates that none of the other possibilities is right.  He thus needs a third clue to decide between the two choices above.

I would not think of stealing the pleasure to solve the puzzle to my reader.  What are the ages of Ernie's children?

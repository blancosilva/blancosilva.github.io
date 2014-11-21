---
layout: page
title: Differentiable Partitions of Unity
date: 2010-10-04 21:25:51.000000000 -04:00
category: course-material
topic: distributions
comments: true
---

This is an extremely useful technique borrowed from Differential Geometry (or is it the other way around?).  The idea is to construct a family of compactly supported smooth functions which "add up to one" in a particular set.  There are several alternative ways to define *Partitions of Unity*, depending mostly on the nature of the objects in which we work (e.g., differential manifolds vs. compact set in measurable spaces).  I will present here one of the most basic results:

<div class="well">
**Theorem** Let \( X \subset \mathbb{R}^d \) be an open set, and let \( K \subset X \) be a compact subset.  Let \( \{ X_k \}_{k=1}^m \) be open subsets of \( X \) whose union contains \( K \).  Then one can find functions \( \phi_1, \dotsc, \phi_m \) such that

1. \( \phi_k \in C_c^\infty (X_k) \), and \( 0 \leq \phi_k \leq 1 \) for all \( k=1, \dotsc, m \).
2. \( \sum_{k=1}^m \phi_k \leq 1 \) on \( X \), and \( \sum_{k=1}^m \phi_k = 1 \) on a neighborhood of \( K \).
</div>

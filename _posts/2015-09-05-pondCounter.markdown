---
layout:     post
title:      "Whiteboard Pond Counter"
subtitle:   "Step by step solution to Pond Counter"
date:       2015-09-05 1:30:00
author:     "Kevin Chiang"
header-img: "img/pondCounter.jpg"
---

<h1>The Problem</h1>
<p>Given a matrix, create a program that can compute how many
ponds there are in an N X M matrix. Ponds can be a single or contiguous block of water</p>
<p>There are no time/memory constraints, and we want to return 0 if there are no
ponds on the grid. Assume that all inputs will be valid.</p>

<h1>Example</h1>
<p>If 0 is water, and 1 is land, and [[0, 0, 1], [0, 1, 0]] is the matrix input,
it means that we will have a total of 2 contiguous blocks of water, so the ouput would be 2. We might be able to
visualize this better by stacking the array inputs:
<pre>
[[0, 0, 1],
 [0, 1, 0]]
</pre>
In this case, the output would be 1.
<pre>
[[1, 0, 1],
 [1, 0, 1]]
</pre>
</p>

<h1>Solution Breakdown</h1>
<p>Let's break this down using some higher level pseudocode:</p>
<code>// Iterate through each array of the matrix</code><br/>
<code>// Iterate through each element of the array</code><br/>
<code>// If a 0 (water) is found, increment a <b>counter</b></code><br/>
<code>  // Call a recursive function on the current spot</code><br/>
<code>    // Recursive function should flip the current spot to a 1, and then check all adjacent spots for 0s</code><br/>
<code>    // Call recursive function on adjacent 0s that are found</code><br/>
<code>// Return the counter</code>
<p>This approach to the solution makes it so that as we find contiguous blocks of water, we only count the block once
so that when we encounter the same spot in the iteration, we don't count it again.</p>

<h1>The Code</h1>
<pre>
</pre>








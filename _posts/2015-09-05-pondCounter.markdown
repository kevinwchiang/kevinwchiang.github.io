---
layout:     post
title:      "Whiteboard Pond Counter"
subtitle:   "Step by step solution to Pond Counter"
date:       2015-09-05 1:30:00
author:     "Kevin Chiang"
header-img: "img/pondCounter.jpg"
---

<h1>The Problem</h1>
<p>Given an N X M matrix, create a program that can compute how many
ponds there are. Ponds can be a single or contiguous block of water.</p>
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
<p>Let's break this down using some pseudocode:</p>
<code>// Iterate through each array of the matrix</code><br/>
<code>// Iterate through each element of the array</code><br/>
<code>// If a 0 (water) is found, increment a <b>counter</b></code><br/>
<code>  // Call a recursive function on the current spot</code><br/>
<code>    // Recursive function should flip the current spot to a 1, and then check all adjacent spots for 0s</code><br/>
<code>    // Call recursive function on adjacent 0s that are found</code><br/>
<code>// Return the <b>counter</b></code>
<p>This approach to the solution makes it so that as we find contiguous blocks of water, we only count the block once
so that when we encounter the same spot in the iteration, we don't count it again.</p>

<h1>The Code</h1>
<pre>
var pondCounter = function(matrix){
  var counter = 0;
  var recursive = function(i, x){
    matrix[i][x] = 1;
    // Right
    if (matrix[i][x + 1] === 0){
      recursive(i, x + 1);
    }
    // Left
    if (matrix[i][x - 1] === 0){
      recursive(i, x - 1);
    }
    // Check if Top exists first, then check value
    if (matrix[i-1] && matrix[i - 1][x] === 0){
      recursive(i - 1, x);
    }
    // Check if Bottom exists first, then check value
    if (matrix[i+1] && matrix[i + 1][x] === 0){
      recursive(i + 1, x);
    }
  }
  for (var i = 0; i < matrix.length; i++){
    for (var x = 0; x < matrix[i].length; x++){
      if (matrix[i][x] === 0){
        counter++;
        recursive(i, x);
      }
    }
  }
  // If there are no 0s (water), return 0
  if (counter === 0){
    return 0; 
  } else {
    return counter;
  }
}
</pre>

<p>Something to watch out for is checking the top and bottom adjacent spots in the recursive function.
If <code>matrix[i-1]</code> or <code>matrix[i+1]</code> are undefined,
attempting to access a property on them will return undefined. This will cause the
program to throw an error. A solution to that is to check if they exist before trying to
access a property on them.
</p>








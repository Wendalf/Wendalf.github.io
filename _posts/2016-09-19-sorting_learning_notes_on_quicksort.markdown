---
layout: post
title:  "Sorting: learning notes on quicksort"
date:   2016-09-19 19:52:00 +0000
---


The first time I came across with sorting was doing the sorting lab in learn.co's web pre work. I was fascinated by one of the resources' video in which it did a visualization and comparison of Sorting Algorithms.

https://youtu.be/ZZuD6iUe3Pc

We learned about bubble sort and merge sort during the CS Fundamentals talk. Bubble sort is a simple sorting algorithm that repeatedly steps through the list to be sorted, compares each pair of adjacent items and swaps them if they are in the wrong order. Merge sort is a divide and conquer algorithm that will first divide the unsorted list into n sublists, each containing 1 element, and then repeatedly merge sublists to produce new sorted sublists until there is only 1 sublist remaining.

[caption id="attachment_9" align="aligncenter" width="300"]<img class="wp-image-9 size-full" src="https://wendalfspells.files.wordpress.com/2016/08/merge-sort-example-300px.gif" alt="Merge-sort-example-300px" width="300" height="180" /> An example of merge sort.[/caption]

Bubble sort seems not too hard to code. Here's the Ruby implementation for bubble sort:
https://gist.github.com/b6000d3d6288bf8dbafc0447e8be0941
<blockquote><img class="aligncenter wp-image-24" src="https://wendalfspells.files.wordpress.com/2016/08/screen-shot-2016-08-11-at-8-18-49-pm.gif" alt="Screen-Shot-2016-08-11-at-8.18.49-PM" width="1000" height="157" /></blockquote>
We tried to code our own merge sort solution in Ruby last Friday. I couldn't come up with my own solution. Here's the Ruby implementation for merge sort I found from wikipedia:
https://gist.github.com/e302dad707e3ffc48f792b344cdc1e40

Merge sort seems to be a really efficient sorting algorithm. However, as you can see from the video above, there are even more efficient sorting algorithms. One of them is called quick sort.
<blockquote><b>Quicksort</b> (sometimes called <b>partition-exchange sort</b>) is an <a class="mw-redirect" title="Algorithm efficiency" href="https://en.wikipedia.org/wiki/Algorithm_efficiency">efficient</a> <a title="Sorting algorithm" href="https://en.wikipedia.org/wiki/Sorting_algorithm">sorting algorithm</a>, serving as a systematic method for placing the elements of an array in order. Developed by <a title="Tony Hoare" href="https://en.wikipedia.org/wiki/Tony_Hoare">Tony Hoare</a> in 1959, with his work published in 1961, it is still a commonly used algorithm for sorting. When implemented well, it can be about two or three times faster than its main competitors, <a title="Merge sort" href="https://en.wikipedia.org/wiki/Merge_sort">merge sort</a> and <a title="Heapsort" href="https://en.wikipedia.org/wiki/Heapsort">heapsort</a>.</blockquote>
Quicksort is a <strong>divide and conquer</strong> algorithm. Quicksort first divides a large array into two smaller sub-arrays: the low elements and the high elements. Quicksort can then recursively sort the sub-arrays.

<strong>The steps are:</strong>
1. Pick an element, called a pivot, from the array.
2. Partitioning: reorder the array so that all elements with values less than the pivot come before the pivot, while all elements with values greater than the pivot come after it (equal values can go either way). After this partitioning, the pivot is in its final position. This is called the partition operation.
3. Recursively apply the above steps to the sub-array of elements with smaller values and separately to the sub-array of elements with greater values.

The pivot selection and partitioning steps can be done in several different ways. One partition way that I found to be the most understandable is called Lomuto's partition scheme.

<img class="aligncenter wp-image-23 size-large" src="https://wendalfspells.files.wordpress.com/2016/08/lomuto_1.jpg?w=840" alt="lomuto_1" width="840" height="630" />
<img class="aligncenter wp-image-22 size-large" src="https://wendalfspells.files.wordpress.com/2016/08/lomuto_2.jpg?w=840" alt="lomuto_2" width="840" height="630" />
<img class="aligncenter wp-image-21 size-large" src="https://wendalfspells.files.wordpress.com/2016/08/lomuto_3.jpg?w=840" alt="lomuto_3" width="840" height="630" />

[caption id="attachment_25" align="aligncenter" width="300"]<img class="wp-image-25 size-medium" src="https://whatitalkaboutwhenitalkaboutcoding.files.wordpress.com/2016/08/tumblr_inline_oahccv9m121tz669h_500.gif?w=300" alt="what was that again?" width="300" height="142" /> what was that again?[/caption]

Here's the pseudocode for Lomuto's algorithm:
<pre>Lomuto-Partition(A, p, r)
x = A[r]
i = p - 1
for j = p to r - 1
    if A[j] &lt;= x
        i = i + 1
        swap( A[i], A[j] )
swap( A[i +1], A[r] )
return i + 1
</pre>

[caption id="attachment_24" align="aligncenter" width="300"]<img class="wp-image-24 size-medium" src="https://whatitalkaboutwhenitalkaboutcoding.files.wordpress.com/2016/08/802.gif?w=300" alt="hmmm..." width="300" height="169" /> hmmm...[/caption]

Can you write your own Ruby implementation for quicksort using the above partition algorithm?

<strong>References:</strong>

https://en.wikipedia.org/wiki/Quicksort

http://www.cs.bilkent.edu.tr/~atat/473/lecture05.pdf

http://cs.stackexchange.com/questions/11458/quicksort-partitioning-hoare-vs-lomuto

https://www.toptal.com/developers/sorting-algorithms/``

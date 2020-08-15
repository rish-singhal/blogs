---
title: "Codechef May Lunchtime - 2020"
mathjax: true
layout: post
comments: true
---

[ABSNX - Absolute Min Max](https://www.codechef.com/LTIME84A/problems/ABSNX)                      
Got the idea while solving, but the core technique used was to find - "Number of elements greater than some number $$k$$ in a given range $$[l,r]$$". For this, merge-sort tree can be used getting $$[l,r]$$ range in sorted order and doing binary search $$O(n\log^2{}n)$$ which apparently won't pass Time Limit. Hence another (new) idea was to use [Fenwick Tree (with offline queries)](https://www.geeksforgeeks.org/number-of-elements-greater-than-k-in-the-range-l-to-r-using-fenwick-tree-offline-queries/) with $$O(n\log{}n)$$ complexity. Main idea: consider the numbers in increasing order. All zeroes initially, and one by one raise the cutoff " while updating value in segtree ".						

* Similar concept: [SPOJ-KQUERY](https://www.spoj.com/problems/KQUERY/)

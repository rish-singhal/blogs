---
title: "Kőnig’s line coloring theorem"
mathjax: true
layout: post
comments: false
---

### Maximum Independent Set in Bipartite Graphs

**Kőnig’s line coloring theorem**: In any bipartite graph, the number of edges in a Maximum matching equals the number of vertices in a minimum vertex cover.							

The complement of a minimum vertex cover in any graph is the maximum independent set.

* Related Problem: [F. Bicolored Segments](https://codeforces.com/contest/1389/problem/F)
  * New Technique : **Flow over segment** -  instead of connecting all the nodes in a contiguous segment, a segment tree can be employed to connect $$O(\log{}n)$$ nodes (of a segment) rather than $$O(n)$$ nodes.			


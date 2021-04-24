---
title: "Multisource Bellman Ford"
mathjax: true
layout: post
comments: false
---

## Introduction

Consider a situation in which we want to calculate the minimum distance we can
move in pre-determined amount of steps, let's say $$k$$ for all the nodes in a
graph. 

How can we go around with solving this efficiently?

## Bellman Ford

Considering the point of $$k$$ steps, one can think of bellman ford which have
an outer-most loop for iterations. And in each iteration - each edge is
considered. Thus moving step by step with each iteration.

[Bellman-Ford](https:
//cp-algorithms.com/graph/bellman_ford.html) can be utilised for finding
negative cycles (while using single-source) and can perform
single-source-shortest-path algorithm in $$O(NE)$$ for a graph with $$N$$ nodes
and $$E$$ edges.

## Multi-source Bellman Ford

Consider the given problem in the introduction section, it comes easily that one
can utilise bellman ford algorithm with $$k$$ iterations initialising $$dp[node]
= 0$$ for all nodes.

```cpp
vector<LL> dp(n);
forn(d, k/2){
    vector<LL> newdp(n, INF);
    for(e: edges){
      // update new DP here 
    }
    swap(dp, newdp);
 }
```

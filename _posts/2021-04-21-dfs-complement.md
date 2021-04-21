---
title: "DFS over Complement Graph"
mathjax: true
layout: post
comments: false
---

## Motivation

Consider a given situation in which the number of edges in a given graph is greater than $$n^2$$ and hence it's not viable to iterate over all these edges for dfs for $$n > 10^5$$. And we somehow want to deal with the connected components of this graph.

Assume we are given the edges which are not present in the graph and they are of the order of $$n$$, i.e. $$O(n)$$. What can we do to instantiate a Depth-First-Search over such graph?

----

## Solution

We can maintain a set of unvisited vertices and iterate over this set for each vertex. While being at some vertex $$u$$ (during DFS) we can remove this vertex from the set. And then iterate over the unvisited set, skipping those vertices for which there does not exist an edge (**NOTE:** such skips will be $$O(m)$$).

Hence, in total while doing this modified DFS we will iterate over all the vertices once (and remove those from the set) and skip the vertices $$O(m)$$. Hence total complexity will be $$O(m + n)$$ for the number of vertices visited.

Although, to implement this we will require to take the **sorted** adjacency list (for complement graph) to quickly binary search to find out the missing edge.

---

## Implementation

```cpp
void dfs(int u){
  s.erase(u);
  sort(all(v[u]));
  for(int i=1;;){
    auto it = s.lower_bound(i);
    if(it == s.end())
      return;
    i = *it;
    if(!binary_search(all(v[u]), i)){
      dfs(i);
    }
    i++;
  }
}
 
int main(){
  fio();
  int n, m;
  cin >> n >> m;
  forn(i, m){
    int u, vv;
    cin >> u >> vv;
    v[u].push_back(vv);
    v[vv].push_back(u);
  }
  for1(i,n) s.insert(i);
  for1(i,n) {
    if(s.count(i))
    	dfs(i);
  }
  return 0;
}
```

----

## Practice Problems
- [ED E-Connected Component?](https://codeforces.com/contest/920/problem/E)
- [Div1 C-Complete the MST](https://codeforces.com/contest/1508/problem/C)

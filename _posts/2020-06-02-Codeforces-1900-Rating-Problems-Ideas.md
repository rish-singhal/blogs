---
title: "Policy Based Data Structures and more"
mathjax: true
layout: post
comments: false
---

[61E-Enemy is weak](https://codeforces.com/contest/61/problem/E)    
Instead of BIT + Co-ordinate Compression, policy based data structure can be used to find number of inversions (of order 3). 

**My approach:** to form $$ dp[2][n] $$ where $$ dp[1][i] $$ represents number of inversions including $$ i^{th} $$ element, of order 2, and $$ dp[2][i] $$ is further constructed from $$ dp[1][i] $$ for order 3. This can be done using BIT + Co-ordinate Compression 

**Alternate Solution:** Find for every element $$A[i]$$, $$L[i]$$ i.e. number of elements left to it and less than $$A[i]$$ and $$R[i]$$ (right), and $$ Answer = \sum_{i=1}^n L[i]\cdot R[i] $$. This can be calcuated using policy based data structures.


```cpp
#include <ext/pb_ds/assoc_container.hpp> // Common file
#include <ext/pb_ds/tree_policy.hpp>     // Including tree_order_statistics_node_updat
 
using namespace __gnu_pbds;
typedef tree<ll, null_type, less<ll>, rb_tree_tag, tree_order_statistics_node_update> ordered_set;

/*

functions: 
1. find_by_order(x) : The value at xth index
2. order_of_key(x)  : The index of number x
				if x is not present it will show key as if it was present in
				sorted array.
*/
```
* [Link to Submission](https://codeforces.com/contest/61/submission/40569977)

---

[1285D-Dr. Evil Underscores](https://codeforces.com/contest/1285/problem/D)    
Got the idea while solving, but was thinking to implement using TRIE. Instead in tutorial found an easy alternative to implement (according to the logic asked) which can be useful to solve dfs on trie kind of problems.

```cpp
int solve(vector<int>& a, int bit = 30){
	if(bit<0) return 0;
	vector<int> l, r;
	for(auto i:a){
		if(i&(1<<bit)) l.pb(i^(1<<bit));
		else r.pb(i);
	}
	if(l.size()==0) return solve(r, bit-1);
	if(r.size()==0) return solve(l, bit-1);
	return min(solve(l,bit-1), solve(r,bit-1)) + (1<<bit);
}
```
* [Link to Submission](https://codeforces.com/contest/1285/submission/82372023)			
* [Link to TRIE-Solution](https://codeforces.com/contest/1285/submission/68656872)

---


[1205B-Shortest Cycle](https://codeforces.com/contest/1205/problem/B)    
For finding the length of shortest cycle using bfs, maintain $$parent[i]$$ array and check for condition:

```cpp
parent[child] != x && parent[x] != child
```
* [Link to Submission](https://codeforces.com/contest/1205/submission/82392117)

---

[1036C-Classy Numbers](https://codeforces.com/contest/1036/problem/C)    
Instead of Digit DP, there was a new combinatorial approach (in editorial) which counted the number of possible numbers by fixing some prefix of $$X+1$$ and then taking less than "next digit", using $$\binom{N}{R}$$.

**NOTE:** One thing to note is, in Digit DP there is no need to make second dimension for $$flag$$ in dp state, instead just maintain dp state for $$flag = 1$$. 

* [Link to DP solution](https://codeforces.com/contest/1036/submission/82726317)



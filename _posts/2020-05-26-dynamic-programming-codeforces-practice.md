---
title: "Dynamic Programming Practice Codeforces"
mathjax: true
layout: post
comments: true
---

[466C-Number Of Ways](https://codeforces.com/problemset/problem/466/C)    
Instead of binary search, a suffix sum array of count can be created for quering for each $$l[i]$$.   Reducing complexity from $$ O(n\log{}n) $$ to $$ O(n) $$.

---

[1114D-Flood Fill](https://codeforces.com/problemset/problem/1114/D)    
One interesting idea to note was, the answer can be calculated using longest palindromic subsequence. Which inturn can be calculated by find LCS between array and it's reverse. 

* [Proof](https://stackoverflow.com/questions/54347339/longest-palindromic-subsequence-dp-solution)
* [Link to Submission](https://codeforces.com/contest/1114/submission/83169697)


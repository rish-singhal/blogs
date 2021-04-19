---
title: "Iterating over Floors"
mathjax: true
layout: post
comments: false
---

[830C-Bamboo Partition](https://codeforces.com/contest/830/problem/C)                      
It turns out the possible values of $$answer$$ is of the type $$\lfloor\frac{x}{y}\rfloor$$, and we need some way to iterate through these values which are $$O(\sqrt{n})$$. This can be done with some neat trick.

```cpp
for(LL i = 1; i <= K; i++){
	LL possible = (K/i);
	i = K/possible; 
}
```

* [Link to Proof](https://codeforces.com/blog/entry/53302?#comment-373555)
* [Link to Code](https://codeforces.com/contest/830/submission/28524841)





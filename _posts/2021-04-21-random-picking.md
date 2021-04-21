---
title: "Randomized Solution"
mathjax: true
layout: post
comments: false
---

This post is regarding a recent problem from [Codeforces Round 716 Div2](https:
//codeforces.com/contest/1514) which can be solved using a randomized approach. 

This is the first problem I solved using randomization approach, so
it's special.

----
## Problem

- Problem: [Cut and Stick](https://codeforces.com/contest/1514/problem/D)

This problem requires to find out the existence of the **super-most frequent**
element in a given range $$[l, r]$$ of an array. 

**Definition:** Super-most frequent element in a range $$[l,r]$$ is the element
with frequency greater than $$\lceil \frac{r-l+1}{2} \rceil$$.

To find such an array element (let's say it exists), it can be seen that the
probability of any array element between $$[l, r]$$ to be super-most freuqent
(SMF) is
$$1/2$$ as the number of SMF is greater than half of the total.

Therefore, we can utilize a random algorithmic approach, where we will choose an
element randomly from the range $$[l,r]$$ \~$$40$$ times and check it's frequency
in $$O(\log n)$$ using binary search over the indices it occur. $$40$$ times
because then the probability of all of the selected random element not to be SMF
will be $$2^{-40}$$ which is really less.

To generate the random number in c++ following code can be used:

```cpp
// initializing random_number_generator - rng
mt19937 rng(chrono::steady_clock::now().time_since_epoch().count());

// to generate a number in the range [l, r]
int random_number = uniform_int_distribution<int>(l,r)(rng)
```

## Solution Link

- [Submission Link](https://codeforces.com/contest/1514/submission/113695906)

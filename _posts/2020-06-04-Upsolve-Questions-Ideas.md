---
title: "Upsolve Tracker - June '20"
mathjax: true
layout: post
comments: true
---

[1043F-Make It One](https://codeforces.com/contest/1043/problem/F)                      
Solved it using binary search over $$1$$ to $$N$$. But it wasnt necessary as it can be seen that if the gcd of some subset is $$1$$ where $$ A_i \leq 300,000 $$, then the size of that subset can be maximum $$7$$ (so bruteforce over $$1$$ to $$7$$ would have worked). 					

**Proof:** It's $$7$$ because if we take small primes greedily and making their gcd not equal to $$1$$, then after $$8^{th}$$ element, it would exceed $$300,000$$.


---

[1271E-Common Number](https://codeforces.com/contest/1043/problem/F)                      
Required $$2$$ different binary searches for odd and even number, but found out that.. it's not necessary to do $$2$$ seperate searches. As, we can simply to do binary search for even numbers and check if $$2\cdot k+1$$ satifies or not.

```cpp
for(int bits = 60; bits>=0; bits--)
	if(func(answer + (1LL<<bits)) >= K)
		answer += 1LL<<bits;

// always use 1LL << bits " for integers not fitting in int (32 bits)"
```
This way of binary search first goes on with even number and at the end checks if we can add $$1$$ or not. So, it was ideal for this question.


* [Link to Submission](https://codeforces.com/contest/1271/submission/82781250) 

---

[BANQUNT-Banned Quotient](https://www.codechef.com/COOK119A/problems/BANQUNT)            
Got the main idea during contest, but didn't knew how to count the number of groups (of size $$p$$), for this the whole segement $$[1, N]$$ can be divided into segments $$[L_i, R_i]$$ where every group starting from a number in these segments ( will have some particular size $$p$$), and hence we can calculate the number of numbers which aren't divisible by $$K$$.

* [Link to Editorial](https://discuss.codechef.com/t/banqunt-editorial/69452) 			

---

[EZRMQ-Carry Bed](https://www.codechef.com/COOK119A/problems/EZRMQ)                      
Some new ideas used in this problem -> Barricade DP and converting the given array into binary tree such that $$LCA(u, v)$$ would be the index of element which holds the maxmimum value in range $$[u, v]$$. And then doing barricade kinda DP on the given binary tree. 			
Also, the main thing for complexity is it's $$O(N^2)$$, as each pair of nodes is evaluted just once while considering their $$LCA$$.

```cpp
int construct_tree(int l, int r){
	if(r<l){
		return -1;
	}
	int in = l;
	for(int i=l;i<=r;i++)
		if(v[i]>v[in]) in = i;
	int vs[2] = {construct_tree(l, in-1),construct_tree(in+1,r)};
	forn(i,2) if(vs[i]!=-1) adj[in].pb(vs[i]);
	return in;
}
```

* [Link to Submission](https://www.codechef.com/viewsolution/34639859)					
* [Link to Editorial](https://discuss.codechef.com/t/ezrmq-editorial/69458)

---

[HXR-Xor Jar Muluk Tar](https://www.codechef.com/LTIME83A/problems/HXR)                      
Simple Problem related to Matrix Exponentiation with XOR " rather than addition ", to solve it efficiently, we can maintain bitsets (both Rows and Columns) and calculate Matrix multiplication.

```cpp
bitset<N> row[MAXN], col[MAXN];
bitset<N> mrow[MAXN], mcol[MAXN];

void mul_mat(bitset<N> *r, bitset<N> *c, bitset<N> *c2){
	bitset<N> rx[MAXN], cx[MAXN];
	forn(i,n)
		forn(j,n){
			rx[i][j] = cx[j][i] = (r[i]&c2[j]).count()&1;
		}
	forn(i,n) r[i] = rx[i], c[i] = cx[i];
}

void expo(int k){
	forn(i,n) mrow[i][i] = mcol[i][i] = 1;
	while(k){
		if(k&1) mul_mat(mrow,mcol,col);
		mul_mat(row,col,col);
		k>>=1;
	}
}
```

* [Link to Submission](https://www.codechef.com/viewsolution/34648600)					
* [Link to Editorial](https://discuss.codechef.com/t/hxr-editorial/63715)

---


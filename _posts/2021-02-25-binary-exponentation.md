---
title: "Binary Exponentiation"
mathjax: true
layout: post
comments: true
---

Let's say you are given two numbers $$a$$, $$n$$ and you have to compute $$a^n$$.

# Algorithm

### Naive Approach: $$O(n)$$
The easiest approach to do this, if one knows how to use "for" loops or implement it (if it is not implemented already) in any given programming language is just a single $$O(n)$$ iteration. Below is a sample implementation in C++.

```cpp
int a, n;
// a, n can be initialized either by taking input or
// by assigning hardcoded values a = 3, n = 4 let's say

// expo initialized to 1 as it is the multiplicative identity
int expo = 1;

for (int i = 0; i < n; ++i) {
    expo = expo * a;
}

// now expo == a^n : true
```
<b>Note</b> 
Here, the data type is "int", assuming the value of $$expo = a^n$$ comes under the constraint of "int". So, any other data type can be used as per requirements.

<b>Caveats</b> 
1. It can be seen that this approach would time out if $$n > 10^8$$.
2. If the value of $$a^n$$ is very large i.e. it can not be stored in "int" or any other provided data type, it will overflow.

<b>Possible Solutions</b>
1. Algorithm of lesser complexity can be utilized in this case -- we will see $$O(\log n)$$ algorithm next.
2. This is the reason why most of the time $$(a^n)%(some\ number)$$ is to be calculated. Most of the time that "some number" is $$10^9 + 7$$ (which is a prime) in competitive programming problems.

-----
### Binary Exponentiation Approach: $$O(log n)$$
For achieving $$O(\log n)$$ complexity, the mathematical fact that any number (in decimal) can be represented uniquely in binary can be utilized.

For example,
$$12 = 1 \times 8 + 1 \times 4 + 0 \times 2 + 0 \times 1 = 1100_{2}$$
$$15 = 1 \times 8 + 1 \times 4 + 1 \times 2 + 1 \times 1 = 1111_{2}$$

Now, also using the fact that $a^{m + n} = a^m \times a^n, we can calculate the values of $a^1, a^2, a^4,$ and so on ...

```cpp
int expo = a;
for (int i = 0; i < n; ++i) {
    expo = (expo*expo);
}
// it's like
// expo: a -> a^2 -> a^4 -> a^8 -> a^16 ...
// i.e. with ith step the value will be a^(2*i)
```

Now, let's say we need to calculate $a^n$, then there will exist a unique representation of "$n$" in binary, whose $i_{th}$ bit can be checked if it is set or not by using a simple boolean expression involving bitwise operator

```cpp
// (n >> i) & 1 == ith bit of n
```
for the proof for this refer to [Link](https://codeforwin.org/2016/01/c-program-to-get-value-of-nth-bit-of-number.html)

now, it can be seen that $$a^n = a^{1 \times b_1} \times a^{2 \times b_2} \times a^{4 \times b_3} \times ...$$ and we can find if the $$a^{2 \times i}$$ have to multiply or not by using the fact we saw above. So, by a simple modification to the previous code we can calculate a^n.

```cpp
//init a, n
int expo = a;

// answer initialized to 1 as it is multiplicative identity
int answer = 1;
for (int i = 0; i < NUMBER_OF_BITS_IN_N; ++i) {
    if((n >> i) & 1) {
        // we check if the ith bit is set or not
        // if it is set then, we multiply expo = a^(2*i)
        answer = answer*expo;
    }  
    expo = (expo*expo);
}

// answer now have the value a^n
```

See, there is only one "O(NUMBER_OF_BITS_IN_N)" for loop, and it is easy to see that the number of bits in $$n = \log_{2}(n)$$.

Hence, the overall complexity = $$O(\log{n})$$

If you are not sure of the number of bits in n, then just simply take MAXIMUM_POSSIBLE_NUMBER_OF_BITS instead which can be \~32 for the int datatype.

### Modular Binary Exponentiation
Considering the second caveat described above, there can be cases where we need to find (a^n)%(some value) -- note that % is the remainder operator (as used in C++).

For this, just an easy modification of the code will work,
```cpp
//init a, n, modvalue
long long expo = a;

// answer initialized to 1 as it is multiplicative identity
long long answer = 1;
for (int i = 0; i < NUMBER_OF_BITS_IN_N; ++i) {
    if((n >> i) & 1) {
        // we check if the ith bit is set or not
        // if it is set then, we multiply expo = a^(2*i)
        answer = (answer*expo) % modvalue;
    }  
    expo = (expo*expo) % modvalue;
}

// answer now have the value (a^n)% modevalue
```

### Conclusion
So, as we saw the binary exponentiation algorithm, it can be used for exponentiating a matrix too, just by changing "\*" operator with implemented matrix multiplication and taking remainder with each number in the matrix.

### Further Directions
For reading more about binary exponentiation and solving some related problems to get a grasp refer to [CP-Algorithms Binary-Exp](https://cp-algorithms.com/algebra/binary-exp.html)

-----------------

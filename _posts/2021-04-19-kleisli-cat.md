---
title: "Kleisli Category: A category for programmers"
mathjax: true
layout: post
comments: false
---

## What is a category?

Category is simply some objects, with some morphisms arising from one object
and pointing to another (this can be same object too). Such that, 

1. There exists an indentity morphism for all objects.
2. For every two morphisms of the type $$m_1: A \mapsto B$$ and $$m_2: B \mapsto
   C$$ there exists a morphism $$m: A \mapsto C$$ which is called composition of
   $$m_1$$ and $$m_2$$. And this composition is **associative.**

---

## Kleisli Category

Now, consider a type of functions which logs "whatever happens in the function".

```cpp
pair <bool, string> negate(bool x) {
    return make_pair(!x, "not ");
    }
```
If we think closely, a composition of such functions exist, and which is

```cpp
pair <function <c(a)>, string> compose(function <b(a)> f, function <c(b)> g) {
    return [f, g](a x){ 
        auto p1 = f(x);
        auto p2 = g(p1.first);
        return make_pair(p2.first, p1.second + p2.second);
        }
    }
```
and identity also exists, which is trivially

```cpp
pair <a, string> id(a x) {
    return make_pair(x, "");
    }
```

---

Viewing this from categoric point of view, it can be seen that these functions
are nothing but morphisms with the two objects (which can be same too) as the
type of input and output.

```
  (a) ---- f -----> (b) ---- g ---->  (c)
   \                                  /
    \------------- f o g ----------->/
```
With each object having it's own identiy morphism.

So, it is a category with types as objects and functions (special - log) as
morphisms. This category is known as **Kleisli Category**.

---

## Reference 

- [Category Theory 3.2 - Bartosz Milewski](https://www.youtube.com/watch?v=i9CU4CuHADQ&list=PLbgaMIhjbmEnaH_LTkxLI7FMa2HsnawM_&index=6)


---
title: "Piano's Axiom"
mathjax: true
layout: post
comments: true
---

### Piano's Fifth Axiom

This blog covers the proof of Piano's Fifth Axiom using set theoretic definitions which are being used to develop Piano's Axioms.

**Axiom:** If $$n$$ and $$w$$ are in $$\omega$$, and if $$n^{+} = m^{+}$$ then $$n = m$$.

To prove the given axiom, we need to first go through two propositions, 

**Proposition 1.** No natural number is a subset of any of it's elements.                            
**Proof 1:** Consider the set $$S$$ with the given properties, now as $$0 = \emptyset$$, therefore no elements in $$0$$ exists hence $$0$$ is not a subset of any of it's elements or $$0 \in S$$.

**Induction Step:** Consider $$n \in S$$, now as $$n = n$$ therefore $$n \subset n$$ hence $$n$$ can not be an element of $$n$$ i.e. $$n \notin n$$ as otherwise $$n \notin S$$. Considering, $$n^{+} = n \cup \{n\}$$, as $$n \notin n$$ therefore $$n^{+} \not\subset n$$ --- (1).

Now let $$n^{+} \subset x$$ therefore $n \subset x$, which gives $$x \notin n$$, therefore $$n^{+}$$ is not a subset of any $$x \in n$$. Hence, $$n^{+}$$ is not a subset of any element of $$n^{+}$$ showing that $$n^{+} \in S$$.\\
Now by mathematical induction, $S = \omega$ (the set of natural numbers).


**Reference:** Naive Set Theory, Paul Halmos
 

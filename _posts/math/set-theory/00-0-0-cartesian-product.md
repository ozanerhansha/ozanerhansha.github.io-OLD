---
layout: post
title: Cartesian Product
date: 2018-12-7
tags: math set-theory
---
<!-- Heavily Reformatted 11/30/18 -->
## Definition
The Cartesian product $\times$ is an operation on two sets, call them $A$ and $B$, that returns the set of all [ordered pairs](/n-tuples) with their first element from $A$ and their second from $B$. Formally, we can think of it as shorthand for the following:

$$A\times B=\{(a,b)\mid a\in A \land b\in B\}$$

#### Existence in ZFC
Utilizing the [Kuratowski definition](/n-tuples#definition) of ordered pairs, we can show that the Cartesian product of two sets can be constructed from the axioms of ZFC. In particular, it is a subset of the following easily constructed set:

$$A\times B \subseteq \mathcal{P}\left(\mathcal{P}\left(A\cup B\right)\right)$$

<details><summary><strong>Proof</strong></summary>
First, note that $A\cup B$ is guaranteed by the axiom of union and that its power set is guaranteed by the axiom of power set.

Next notice that, among many other elements, the power set of $A\cup B$ contains:
<!-- \left(\forall a\in A,\forall b\in B\right) -->
$$\{a\},\{a,b\}\in\mathcal{P}\left(A\cup B\right)$$

where $a$ and $b$ are elements in $A$ and $B$ respectively. Now if we take the power set again we'll see that the result contains, among other things, the elements:

$$\{\{a\},\{a,b\}\}\in\mathcal{P}\left(\mathcal{P}\left(A\cup B\right)\right)$$

for all $a$ and $b$ in $A$ and $B$. Now invoke the axiom of subset to choose only those elements that fit the description and we are done!
</details>
<p></p>

<!-- $A\cup B$ is guaranteed by the axiom of union, and its repeated power sets are guaranteed by the axiom of power set. This coupled with the fact that the Cartesian product is only a subset of the above expression implies that it must exist. -->

<!--more-->

## $n$-ary Cartesian Product
It is easy to see how one might generalize this notion to $n$ sets. For example, by chaining the Cartesian product twice we are left with a set of $3$-tuples:

$$\begin{align*}(S_1\times S_2)\times S_3&=\{(\left(s_1,s_2),s_3\right)\mid\forall i\in[1..3],\ s_i\in S_i)\}\\
&=\{\left(s_1,s_2,s_3\right)\mid\forall i\in[1..3],\ s_i\in S_i)\}
\end{align*}$$

Repeating this $n$ times, we are left with the following for any $n$ sets:

$$S_1\times S_2\times \cdots \times S_n=\{\left(s_1,s_2,\cdots,s_n\right)\mid\forall i\in[1..n],\ s_i\in S_i)\}$$

The resulting product has an **arity** of $n$ and is dubbed an **$n$-ary Cartesian product**. We can denote product of multiple sets more concisely via the following notation:

$$\prod_{i=1}^nS_i=S_1\times S_2\times \cdots \times S_n$$

*Notice that the parenthesis are omitted. This is because the cartesian product is left-associative, a property that is expounded upon further below.*

<!-- Letting $S_i$ be a family of sets indexed by $n$, we can write this in the more concise big pi notation:
$$\prod_{i=1}^nS_i=S_1\times S_2\times \cdots \times S_n$$

*Note that the notion of indexed families comes from functions which depend on the definition of $n$-ary cartesian products. So it should only be taken as a useful shorthand.* -->

<details>
<summary><h4 class="inline" id="simultaneity-of-arity">Simultaneity of Arity</h4></summary>
Recall that any $n$-tuple can be <a href="\n-tuples#simultaneous-interpretation">simultaneously interpreted</a> as a $k$-tuple where $1\le k\le n$. Likewise, this means that an $n$-ary Cartesian product:

$$\prod_{i=1}^nS_i=S_1\times S_2\times \cdots \times S_n$$

can also be interpreted as having arity $k$. We can show this by first defining a new indexed set:

$$U_i =
  \begin{cases}
  \displaystyle  \prod^{n-k+1}_{i=1}S_i & i=1 \\
  \displaystyle  S_{n-k+i} & i>1
  \end{cases}$$

And now we can phrase the original $n$-ary product as a product of $k$ sets:

$$\prod_{i=1}^kU_i=\left(\prod^{n-k+1}_{i=1}S_i\right)\times S_{n-k+2}\times \cdots \times S_n$$
<p></p></details>

### Indexed & Infinitary Products
It is possible to extend the notion of the Cartesian product to allow for the product of any indexed family of sets:

$$\prod_{i\in I}S_i=\{f:I\to\bigcup_{i\in I}S_i\mid \forall i,f(i)\in S_i\}$$

In words, this Cartesian product returns every function that takes an element $i\in I$ and maps it to an element $f(i)\in S_i$. Note that this allows for index sets with an infinite cardinality, leading to **infinitary** Cartesian products:

$$\underbrace{\text{binary},\text{trinary},\cdots,n\text{-ary}}_{\text{finitary}},\cdots;\underbrace{\aleph_0\text{-ary},\aleph_1\text{-ary},\cdots}_{\text{infinitary}}$$

Note that this generalizes the first definition because $n$ can be thought of as a set with $n$ elements as per its construction in the [natural numbers](\natural-numbers), and so we can take it to be our index set $I$. As a result, these two definitions are isomorphic for finitary products.

#### Useful Shorthand
Note that the normal finitary product produces a set of tuples while this indexed product produces a set of functions. This distinction is important because the definition of a function depends on that finitary product.

Think of the indexed product as just a useful shorthand for defining a the set of all functions from some $I$ to some set of domains $S_i$, and not a replacement for the finitary product.

<details>
<summary><h4 class="inline">Cartesian Powers</h4></summary>
When dealing with the repeated Cartesian product of a single set $S$, we call it the <b>$n$th Cartesian power</b> and use the following notation:

$$S^n=\prod_{i=1}^nS=\underbrace{S\times S \times \cdots \times S}_{n\text{ sets}}$$

Even more generally, using the indexed definition of Cartesian product, we can denote the set of all functions from a set $I$ to $S$ like so:

$$S^I=\prod_{i\in I}S=\{f\mid f:I\to S\}$$

<!-- $$S^I=\prod_{i\in I}S=\{G\mid (\exists f)\ f=(I,S,G)\wedge \operatorname{isFunction}(f)\}$$

*Note that, because many naïve definitions of function identify them solely via their graphs, the definition of $S^I$ above may not look the same as usual.* -->

<!-- Note that this meshes with the simpler definition of $S^n$ since $n$ can be thought of as a set with $n$ elements as per its construction in the <a href="\natural-numbers">natural numbers</a>
<!-- [natural numbers](\natural-numbers). -->
<p></p></details>

<details>
<summary><h4 class="inline" id="empty-set">Empty Set</h4></summary>
A special case of the Cartesian product is when one of the sets $S_i=\emptyset$. When this happens the entire product collapses into the empty set. This is because there are simply no elements in $\emptyset$ to be mapped to by $f(i)$. We can state this as the following for any indexed family of sets $\{S_i\}_{i\in I}$:

$$(\exists i\in I)\ S_i=\emptyset\implies \prod_{i\in I}S_i=\emptyset$$

Indeed this absorbing property of the empty set is the only case in which a Cartesian product could result in the empty set.
<br><br>
<i>Interestingly, if we don't assume the axiom of choice, it is possible that an infinite Cartesian product of nonempty sets will still produce the empty set.</i><p></p>
</details>

<details>
<summary><h4 class="inline" id="unary-product">Unary Product</h4></summary>
Because our product notation allows us to denote the cartesian product of <i>any</i> indexed family of sets, it is natural for us to ask what is returned when the family consists of a single set. The answer is just that set itself:

$$\prod_{i=1}^1S=S$$

We define the unary product in this way to make our product notation more convenient (e.g. recursive definition of product has a base case of 1 set). It also allows us to avoid adding $1$-tuples, and even further $0$-tuples, along with the unnecessary complexity they add to our definition of $n$-tuples.

Note that this definition implies that a "$1$-tuple" can be intuitively thought of as just an element of a set.<p></p>
</details>

<details>
<summary><h4 class="inline">Nullary Product</h4></summary>
Another special case is when the index set $I=\emptyset$. This is called an empty or <b>nullary Cartesian product</b>. The index set being empty means that there can only be one function (the empty function) in the product:

$$\prod_\emptyset=\{f_\emptyset:\emptyset\to\emptyset\}=\{(\emptyset,\emptyset)\}$$

Going back to Cartesian powers, this implies that $S^0=S^\emptyset=\{f_\emptyset\}$ for any set $S$.

<i>If we were to identify functions as just their graphs, then the nullary product would just be $\{\emptyset\}$.</i>
</details>

## Properties
Note that the following properties refer to the standard binary Cartesian product and not its indexed variant.
### Positional Properties
<details open>
<summary><h4 class="inline">Left-Associative</h4></summary>
When faced with an $n$-ary Cartesian product without parenthesis, it is conventionally evaluated from left to right. That is to say the Cartesian product is left-associative:

$$A\times B \times C=(A \times B)\times C$$

This convention intuitively meshes with the definition of $n$-ary Cartesian products and $n$-tuples, i.e. $((a,b),c)=(a,b,c)$.
<p></p>
</details>

<details>
<summary><h4 class="inline">Non-Commutative</h4></summary>
The Cartesian product is a non-commutative operator:

$$A\times B \not= B \times A$$

This should be obvious as the ordered tuples $(a,b)\not=(b,a)$ where $a\in A$ and $b\in B$ via the definition of <a href="/n-tuples#equality">tuple equality</a>.
<p></p>
</details>

<details>
<summary><h4 class="inline">Non-Associative</h4></summary>
The Cartesian product is a non-associative operator:

$$\left(A\times B\right) \times C \not= A\times \left(B \times C\right)$$

Similar to its non-commutativity, we can illustrate this by noting that $((a,b),c)\not= (a,(b,c))$ where $a\in A$, $b\in B$, and $c\in C$.
</details>

### Distributive Properties
$$\begin{align*}
A\times\left(B\cup C\right)&=\left(A\times B\right)\cup \left(A\times C\right)\tag{Union}\\
A\times\left(B\cap C\right)&=\left(A\times B\right)\cap \left(A\times C\right)\tag{Intersection 1}\\
\left(A\times B\right)\cap \left(C\times D\right)&=\left(A\cap B\right)\times \left(C\cap D\right)\tag{Intersection 2}\\
A\times\left(B\setminus C\right)&=\left(A\times B\right)\setminus \left(A\times C\right)\tag{Set Difference}\\
B\subseteq C&\leftrightarrow\left(A\times B\right)\subseteq \left(A\times C\right)\tag{Subset 1}\\
\left(A\times B\right)\subseteq \left(C\times D\right)&\leftrightarrow\left(A\subseteq B\right)\land \left(C\subseteq D\right)\tag{Subset 2}\\
\end{align*}
$$

<!-- <h4>Union</h4>
$$A\times\left(B\cup C\right)=\left(A\times B\right)\cup \left(A\times C\right)$$

<h4>Intersection</h4>
$$A\times\left(B\cap C\right)=\left(A\times B\right)\cap \left(A\times C\right)$$

$$\left(A\times B\right)\cap \left(C\times D\right)=\left(A\cap B\right)\times \left(C\cap D\right)$$

<h4>Set Difference</h4>
$$A\times\left(B\setminus C\right)=\left(A\times B\right)\setminus \left(A\times C\right)$$

<h4>Subsets</h4>
$$B\subseteq C\iff\left(A\times B\right)\subseteq \left(A\times C\right)$$

$$\left(A\times B\right)\subseteq \left(C\times D\right)\iff\left(A\subseteq B\right)\land \left(C\subseteq D\right)$$

<h4>Complements</h4> -->
If $A$ and $B$ are members of some universal set $U$, then their absolute complement is denoted $A^C$ and $B^C$ respectively.

$$\left(A\times B\right)^C=\left(A^C\times B^C\right)\cup\left(A^C\times B\right)\cup\left(A\times B^C\right)\tag{Complement}$$

## Cartesian Factorization
The Cartesian product is analogous to the integer product we are familiar with in the following way: a Cartesian product can be 'factored' into its component sets. Even further, there exists a unique prime factorization of any Cartesian product that recovers its original sets.

#### Finitary Product
<!-- Before we can factor finite Cartesian products we have to remember their simultaneity of arity, i.e. that they can be interpreted in multiple ways. To avoid this, and arrive at a unique prime factorization, we have to extract the factors right to left, since the **rightmost factor** (RMF) of any Cartesian product $P$ is the same for all its possible factorizations. -->
To find the $i$th **Cartesian Factor (CF)** of an $n$-ary Cartesian product $P$ we simply have to find the union of the $i$th index of all tuples in $P$:

$$\operatorname{CF}_i^n(P)=\bigcup_{p\in P} \pi^n_i(p)=S_i$$

*Where $\pi^n_i(p)$ is the [tuple extraction function](\n-tuples#extraction).*

#### Indexed Product
In the more general case where our Cartesian product $P$ is of an indexed family $\\{S_i\\} _{i\in I}$ then we can find the $i$th factor in the following way:

$$\operatorname{CF}_i(P)=\bigcup_{p\in P} p(i)=S_i$$

Note that we can recover the index set $I$ from the product $P$ by simply choosing any one of its element (a function) and looking at its first element. It will end up being the Cartesian product of its domain $I$ and codomain which is a binary product, so we can extract the first set as described in the finitary case.

*Also note that, unlike the finitary case, indexed products can only be interpreted one way and so only have one factorization.*

#### Prime Factorization
The **Cartesian prime factorization (CPF)** is simply the indexed set of all the Cartesian factors. Note that the indexing is important because, unlike integer factors, the order matters. And so for an $n$-ary Cartesian product $\prod_{i=1}^nS_i=P$ we can say:

$$\operatorname{CPF}^n(P)=(\operatorname{CF}_i^n(P))_{i=0}^n=(S_i)_{i=1}^n$$

Note that due to the simultaneity of arity, the factorization of a finite product depends on what arity we consider to it be. We can resolve this if we specify that the *unique* prime factorization of a finitary product requires it be considered the maximum arity possible.

For an indexed Cartesian product $\prod_{i\in I}S_i=P$ we can say:

$$\operatorname{CPF}(P)=(\operatorname{CF}_i(P))_{i\in I}=(S_i)_{i\in I}$$

#### Factorization of the Empty Set
Analogous to the number zero, the empty set $\emptyset$ does not have a unique prime factorization. That is because if one of the factors of a Cartesian product happens to be the empty set, then the result too will be empty and thus there is no way to recover the original factors from it. In other words, any family of sets can serve as a factorization of $\emptyset$ so long as one of them is $\emptyset$ itself.

## Examples & Uses
#### Relations
An $n$-ary [relation](\relations) is defined as an $n$-tuple with the first element being an $n$-ary Cartesian product and the last element a subset of that product. For example, $\le$ is a binary relation on the set $\mathbb R$:

$$\begin{gather}
\le\equiv(\mathbb R\times\mathbb R,G)\\
G\subseteq\mathbb R\times\mathbb R
\end{gather}$$

This allows us to formalize statements like $4\le7$ which really means $(4,7)\in G$.

#### Cardinal Multiplication
Cartesian products are used to define the product of two cardinal numbers:

$$\left|X\times Y\right|=\left|X\right|\left|Y\right|$$

And in general for any indexed family of cardinal numbers:

$$\left|\prod_{i\in I}X_i\right|=\prod_{i\in I}\left|X_i\right|$$

*Note the left product denotes the Cartesian product while the right denotes the cardinal product.*

#### Cartesian Coordinates
Every point in $2$-space represents an element of the Cartesian product of the Reals with themselves (i.e $\mathbb{R}^2$). This can be generalized to $n$-space with every point being an element of $\mathbb{R}^n$:

$$\mathbb{R}^n=\{(x_1,x_2,\cdots,x_n)\mid \forall i\in [1..n]:   x_i\in\mathbb{R}\}$$

![plane](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Cartesian-coordinate-system.svg/354px-Cartesian-coordinate-system.svg.png?style=centerme)

*Indeed, the graphical representation above was dubbed the Cartesian plane after the same [Descartes](https://en.wikipedia.org/wiki/René_Descartes) that used it to represent the Cartesian product $\mathbb{R}\times\mathbb{R}$.*

Points in $3$-space are necessary in describing the [position](/position) of objects and particles in space and thus set up the study of [motion](\kinematics), the causes of that motion and, ultimately, the rest of physics.

Moreover, $2$-space (and less frequently $3$-space) is used in plotting and making inferences from data as well as visualizing functions over an interval of numbers. We can even consider an infinite dimensional real space $\mathbb R^\mathbb \omega$, aka the set of all real sequences.

---
layout: post
title: "Update on the FCA Problem"
date: 2025-07-17
readingtime: 15
tags: [math, 2025]
excerpt: Counterexamples to the FCA problem
---

Some time last year I wrote about the [<u>finite consensus algorithm problem</u>]({{ "/old-site/2024/misc.html" | relative_url }}){: .page-link target="_blank"}. The problem asks: if we have a graph which admits random values to be defined at each vertex, and we can take a number of moves to replace the value at an individual vertex with the average of its neighbors' values, how can we determine for a given graph $G$ whether a finite sequence of moves exists such that no matter what values we set at the start, all vertices will have the same value after this sequence of moves is applied?

This question was inspired by Q4 of APMO 2019 (see original document). As far as I am aware nobody has researched it before, which suggests that it may be a trivial type of question because it is not immediately obvious whether it has any real world analogs. However there are variants where a broader class of functions (including averaging) is considered in an asymptotic context and where multiple vertices can update their values in the same timestep. In this question we can't do that if two vertices are neighbors, since the value of one of them would have changed if it was chosen first.

My original conclusion was also that this was a trivial sort of mathematical curiosity and so after I couldn't get a full rigorous proof, but had a heuristic argument that I was 99% sure was correct, I just gave up on the thing and put together a hypothesis that basically relied on the heuristic argument being true.

The hypothesis I originally had was that $\exists$ some process that is finite for all input vectors $\vec{g}$ iff $G$ is a complete bipartite graph. If you look at a few test examples it becomes immediately clear that this is the most natural class of solutions to this problem. The issue was that I couldn't definitively prove that no other classes of solutions existed.

The heuristic guess I had was that there would never be a multiple moves on a single node in a minimal sequence of moves. This turned out to be wrong. So far, all the counterexamples I have found have required at least one node to make a "move" multiple times.

Let's take a look at the first one:

<div align="center">
    <img src="/assets/images/pcaupdate/graph1.png" style="width: 40%">
</div>

Note that the numbers are the indices of the vertices, not the values assigned to them (which are random). There is in fact a finite consensus sequence for this, which is: $2\rightarrow3\rightarrow0\rightarrow1\rightarrow3$. You can try it yourself to prove that it works.

In contrast to the original hypothesis, in this case there is a vertex (0), which required some other vertex (3) to reach some value <i>that was not the final consensus value</i> first, before it could reach the final consensus value.

An interesting thing about this graph is that $v_2$ reaches $\mu$ in the first move, whereas $v_3$ requires an additional move since it's used as an "intermediate step". This means that if we attach another vertex with the same neighbors as $v_2$ we can use an analogous process to reach consensus, but it won't work in the same way for $v_3$:

<div align="center">
    <img src="/assets/images/pcaupdate/graph2.png" style="width: 40%">
</div>

The consensus sequence here is $3\rightarrow1\rightarrow4\rightarrow0\rightarrow2\rightarrow4$. In effect this is the exact same process as the first graph but with an extra vertex at the start. If we instead added another vertex to the first graph which was only connected to $v_0$, then the move at $v_0$ would not make it equal to the value at the original $v_2$ (try it yourself).

I'll call the first graph and its extensions "branch and leaf / leaves". As you can see you can add as many "leaves" as you want:

<div align="center">
    <img src="/assets/images/pcaupdate/graph3.png" style="width: 40%">
</div>

The next two graphs, which I found after running a brute force search (details later), are:

<div align="center">
    <img src="/assets/images/pcaupdate/graph4.png" style="width: 40%">
    <img src="/assets/images/pcaupdate/graph5.png" style="width: 40%;">
</div>

You can try finding the answers yourself. The answers are below:

<span class='spoiler'>3, 2, 1, 3, 0, 3, 2</span> and <span class='spoiler'>1, 3, 4, 0, 5, 2, 3, 4</span>

These two counterexamples were found using a brute force “pruned tree” search on all relevant permutations of matrices up to length 8 (ie. 8 moves) over <b>every unique connected graph</b> with 6 or less vertices (up to isomorphism). This is an unfortunate issue because if I have $v$ vertices and want to do a brute force search of move sequences up to a maximum length of $n$, then even if we use the fastest known matrix multiplication algorithm we need to do at most $v(v-1)^{n-1}$ computations of complexity $O((n-1)v^{2.37})$ in the worst case. For up to 8 moves, the 5 graphs presented above are the only graphs that are not complete bipartite but have a finitely converging sequence of moves, but it doesn't exclude there being more complicated sequences that haven't been found yet.

So given that counterexamples to the original hypothesis exist, we need to come up with some alternative hypothesis. Unfortunately I don't have an answer for this, but to give an idea of what <i>doesn't</i> work:

First let's rewrite this problem in the matrix language originally defined in the document linked at the start of the article. Let $P_{i}$ be the projection matrix encoding a "move" on vertex $i$, which is equal to $I_{j*}$ for rows $j \neq i$ and $D^{-1}A$ for row $i$, where $D$ and $A$ are the degree and adjacency matrices respectively. A converging sequence of moves exists if for some finite arrangement of $P_{i}$ we get a rank 1 matrix.

This is effectively computing a membership problem for the multiplicative semigroup generated by $\left<P_1, P_2, … P_n\right> \subseteq M_n(\mathbb{R})$, which we know to be undecidable in the general case for $n \geq 3$ (see [<u>here</u>]({{ "https://bazhenov.droppages.com/wdcm-2020/Slides/Semukhin.pdf" }}){: .page-link target="_blank"}). Of course, this is not any random semigroup but a very specifically chosen generating set, but it means that in general it would be hard to come up with a satisfactory way to solve this by only using computational methods.

It is possible to get a necessary but not sufficient condition for a finite consensus sequence using a transformation of the problem. First, notice that we can choose the inputs to be integers. This allows us to consider the problem of averaging, which is division by the degree of a vertex, as a problem of multiplying by the inverse of the degree over a prime field.

Let $p$ be any prime that is coprime to all the degrees of the vertices. Then in row $i$, $D^{-1}A$ becomes $d^{-1}A_{i*}$ in $\mathbb{Z}_p$. For example in the first graph from above, the branch with one leaf, the original matrix $P_0$ was
$$\begin{pmatrix}
0 & \frac{1}{3} & \frac{1}{3} & \frac{1}{3} \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}$$,
whereas under $Z_5$ this matrix would be
$$\begin{pmatrix}
0 & 2 & 2 & 2 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}$$.

For all matrices, there will only ever be two eigenvalues, 0 and 1 (each $P_i$ is right stochastic and also “eliminates” the value at $v_i$), and the eigenspace associated to 1 has dimension $n-1$. Additionally, the all ones vector $[1, 1, … 1]^{T}$ will always be in the span of the eigenspace of 1.

The necessary condition is then simply: if the intersection of all the eigenspaces associated to 1 for every $P_i$ has dimension greater than 1, ie. there are vectors left unchanged by <b>all</b> the matrices aside from $(1, 1, … 1)^{T}$, then the graph can’t have a finite consensus sequence, since back in the $\mathbb{R}$ world repeated moves on such a vector would not bring all the values to be equal.

Let’s try this on a few examples:

For the branch with one leaf graph, the intersection of all $\lambda = 1$ eigenspaces mod 5 is indeed generated by $[1, 1, 1, 1]^T$. For a triangle, the intersection mod 3 is generated by $[2, 1, 0]^T$ AND $[2, 0, 1]^T$. Notice that adding those two gives $[1, 1, 1]^T$ mod 3, but there are still other starting vectors that don’t end up converging! For a disconnected graph, which is useful as a test, we get that the intersection mod 2 is $[1, 1, 0, 0]^T$ and $[0, 0, 1, 1]^T$. As expected, the triangle and the disconnected graph can't reach consensus.

However this is not a sufficient condition. Consider the graph on 4 vertices which are connected in a line ($\cdot - \cdot - \cdot - \cdot$). For any input, we can use the moves $0 \rightarrow 3$ to get to the position where $v_0 = v_1$ and $v_2 = v_3$. Representing this in mod 3 we get:
$[a, a, b, b] \rightarrow [a, 2a+2b, b, b] \rightarrow [a, 2a+2b, a, b] \rightarrow [a, a, a, a]$ from the sequence $(0 \rightarrow 3) \rightarrow 1 \rightarrow 2 \rightarrow 0 \rightarrow 3$. But if you try this on an actual sequence over this graph in $\mathbb{R}$ you will realize that this doesn’t work at all. Indeed, the intersection mod 3 for this graph is spanned by $[1, 1, 1, 1]^T$, and yet there is clearly no finite consensus sequence for this graph.

So this doesn’t work either. What next?

I think there’s some sort of pattern with the average degree not being too low in comparison to the number of vertices and also not being too high. It is possible that for large $n$, there could be some kind of probabilistic proof based on this and the rough idea that every value should have a clean way to “flow” to another vertex, and this gets impeded if there are too few edges (path between vertices is too long) or too many edges (value gets diluted by lots of other values along the way). For now I don’t have any hypotheses that I can formalize. Hopefully in the future I can pick this up again with a newer set of tools and figure out a full solution.

&nbsp;&nbsp;

[<u>Back to top</u>](#){: .page-link}
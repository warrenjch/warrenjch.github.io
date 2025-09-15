---
layout: post
title: "Variance Drain under Ito and Stratonovich Integrals"
date: 2025-09-15
readingtime: 6
tags: [finance, math, 2025]
excerpt: Why does it seem to exist under one and not the other?
---

# Deriving Variance Drain

When I ended my internship back in July I set myself the very unrealistic goal of finishing &Oslash;ksendal's <i>Stochastic Differential Equations</i> before university started and unfortunately, I massively overestimated my comprehension speed and underestimated the amount of Rudin I had to brush up on. With 75% of my 2 month break gone I have only finished 4 out of the 12 chapters, though some chapters near the end are less conceptual and more application based, which would hopefully prove to be less dense than the first few chapters.

On the upside, with what little I have already learned, I have finally come around to proving one of the things I've always quoted to others but never knew how to prove:

$$\begin{align*}
\text{Geometric Mean Return} = \mu - \frac{1}{2}\sigma^2
\end{align*}$$

This comes up in basically any argument you have about leveraged ETFs, but there's really no way to answer "why is there a $-\frac{1}{2}\sigma^2$ there" without using some stochastic calculus. Below I'll derive this, following &Oslash;ksendal's notation.

First we quote It&ocirc;'s formula:

$$\begin{align*}
\text{Let } & X_t = udt + vdB_t\\
& g(t,x) \in C^2([0,\infty) \times \mathbb{R})\\
& Y_t  = g(t, X_t)
\end{align*}$$

$$\text{Then } dY_t = \frac{\partial g}{\partial t}(t, X_t)dt + \frac{\partial g}{\partial x}(t, X_t)dX_t + \frac{1}{2}\frac{\partial^2 g}{\partial x^2}(t, X_t) \cdot (dX_t)^2$$

From here we can easily apply it to the stock price $S_t$, which we model as a geometric Brownian motion by:

$$dS_t = S_t(\mu dt + \sigma dB_t)$$

We know this means that the log of the prices follows a normal Brownian motion with drift, so we apply It&ocirc;'s formula:

$$\begin{align*}
\text{Let } g(S_t) &= \ln S_t\\
d(g(S_t)) &= \frac{1}{S_t}dS_t - \frac{1}{2S_t^2} S_t^2 (\mu dt + \sigma dB_t)^2 \\
&= \frac{1}{S_t} S_t(\mu dt + \sigma dB_t) - \frac{1}{2}\sigma^2 dt\\
&= (\mu - \frac{1}{2}\sigma^2)dt + \sigma dB_t\\
\ln S_t &= \ln S_0 + (\mu - \frac{1}{2}\sigma^2)t + \sigma B_t\\
S_t &= S_0\exp((\mu - \frac{1}{2}\sigma^2)t + \sigma B_t)
\end{align*}$$

From here we can read off that $\mathbb{E}\left[\frac{S_t}{S_0}\right] = (\mu - \frac{1}{2}\sigma^2)t$, meaning that the geometric mean or the expected increment to the log return <i>per unit time</i> is going to be $\mu - \frac{1}{2}\sigma^2$.

# It&ocirc; vs Stratonovich integrals

A more interesting question is why, despite there being multiple "valid" interpretations of what "$\int f\,dB_s$" is supposed to mean, we mostly only use the It&ocirc; integral in financial contexts. Consider if we formulate $S_t$ with the Stratonovich definition instead:

$$dS_t = S_t(\mu dt + \sigma \circ dB_t)$$

Since $S_t$ does not vary "smoothly" with $t$, we should expect this to be different from the It&ocirc; integral. We can convert between the Stratonovich and It&ocirc; integrals by adding the term $\frac{1}{2} \frac{\partial v}{\partial x} \frac{\partial^2 v}{\partial x^2}dt$, where $X_t = u(t,x)dt + v(t,x) \circ dB_t$. Hence:

$$\begin{align*}
S_t(\mu dt + \sigma \circ dB_t) &= \left(\mu S + \frac{1}{2}(\sigma S)\sigma\right)dt + \sigma S_t dB_t\\
\end{align*}$$

From the first section we can substitute $\mu$ with $\mu + \frac{1}{2}\sigma^2$ to see that the expected geometric return is $\mu$, and the variance drain term has disappeared. So which method is correct here?

It turns out that the trick that creates this "contradiction" lies in a small abuse of notation. Since we can use the chain rule for Stratonovich integrals, we can simply write:

$$\begin{align*}
d(\ln(S_t)) &= \frac{1}{S_t}dS_t\\
&= \mu dt + \sigma dB_t\\
\mathbb{E}[d(\ln(S_t))] &= \mu
\end{align*}$$

Therefore, $\mu$ here is actually the <b>expected geometric return</b>, which we can call $\mu_s$ for clarity, whereas in the It&ocirc; formulation, $\mu_i$ is the <b>expected arithmetic return</b>.

If we are talking about leveraged ETFs, then it's much harder to see how the expected geometric return changes, whereas the expected arithmetic return can just be scaled by the leverage factor. I suspect that arithmetic returns are used for this neat fact that they are conceptually much simpler and also conveniently happen to mask variance drain!

From this example it would seem that it's fair to use either interpretation of the integral, because after applying a change of measure they should both give the same result. Aside from the useful fact that It&ocirc; integrals are martingales<sup>1</sup> wrt  $$\mathcal{F}_{t}$$, I would posit that a more important fact is that in actual applications we know that datapoints of prices are discrete in time. Until we reach the limit of $\Delta_{t} \rightarrow 0$, the midpoint between $t_{k}$ and $t_{k+1}$ is not measurable wrt $$\mathcal{F}_{t}$$. In order to not introduce lookahead bias, it only makes sense that we stick to choosing $S_{t_{k}}$ under the It&ocirc; interpretation, which is the only measurable point between $[t_{k}, t_{k+1})$.

<small><sup>1</sup> &Oslash;ksendal, Corollary 3.2.6</small>

&nbsp;&nbsp;

[<u>Back to top</u>](#){: .page-link}
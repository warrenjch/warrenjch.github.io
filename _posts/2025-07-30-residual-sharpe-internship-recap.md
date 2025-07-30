---
layout: post
title: "Residual Sharpe - Internship Recap"
date: 2025-07-30
readingtime: 10
tags: [finance, math, 2025]
excerpt: Derivations of useful properties involving t-stats
---

I ended my internship last week after 5 months. It was a lot more flexible than my previous two internships, since I was given the freedom to choose the duration of my internship and most of what I wanted to work on with minimal supervision. I think there's pros and cons to this style of unstructured internship, but I like working in environments where I can focus on researching whatever interests me. For me having someone experienced critique my work while I iterate through different ideas to "fit" my research to a proper rigorous output is better than being told what to do directly.

In total I think I looked at 7 strategies, some seriously, and others as a mere curiosity. Out of the 6 serious strategies, one did not work due to a combination of trading limitations (I didn't know different commodities had such wildly varying settlement dates and rules) and what I suspect were data issues, two were replicable for the period during which prior papers talked about the strategy but immediately fell off after that<sup>1</sup>, one couldn't be replicated for whatever reason, and two successfully made it past the testing stage to formalization (and hopefully can go into production in the future).

<small><sup>1</sup> One strategy was taken from a paper that was published in 2020 and used data up until the end of 2017, which was a gap of 2+ years. We contacted their data vendor and were able to get data up to the end of last year. Coincidentally, their strategy worked very well until the start of 2018, when the returns went off a cliff:</small>

<div align="center">
    <img src="/assets/images/residualsharpeinternship/strat.jpg" style="width: 60%">
</div>

<small>Not alleging anything here, but I think there's also something to be learned: if it's too good to be true, it's either (most likely unintentional) p-hacking, it's luck, or you're getting paid for some kind of toxic risk. In this case, I think it's a combination of the former two.</small>

I can't say much about what I did during these few months, but I learned a few interesting properties about t-stats along the way that I will prove below. T-stats are useful when you are trying to figure out how much alpha a strategy has over some other strategy or a benchmark. In the Sharpe world that's important because you can derive many things about how two return series relate to each other from the t-stats of a regression.

# Residual Sharpe

The first relation:
$$S_{r} = \frac{t_{\alpha}}{\sqrt{T}}$$
where the residual sharpe of one strategy over another is the t-stat of the constant term in the regression divided by the root of the number of years in the data.

If we have two strategies $A$ and $B$, then after regressing we get $A = \alpha + \beta B + \epsilon$. The residual strategy is $A$ after hedging out its beta to $B$, which is $A - \beta B = \alpha + \epsilon$. Since we are looking for an annualized Sharpe, we need to normalize the $N$ datapoints: $S_r = \sqrt{\frac{N}{T}}\times\frac{E[A - \beta B]}{\text{std}(A- \beta B)} = \sqrt{\frac{N}{T}}\times\frac{\alpha}{\sigma_{\epsilon}}$.

Since $t_{\alpha} = \frac{\alpha}{\frac{\sigma_{\epsilon}}{\sqrt{N}}}$ we have that $S_r = \frac{t_{\alpha}}{\sqrt{T}}$.

The other relation, if you only know the correlation between $A$ and $B$, is:

$$S_r = \frac{A - \rho B}{\sqrt{1 - \rho^2}}$$

The interpretation of this is that you are breaking $\beta$ into its components, $\rho \frac{\sigma_{A}}{\sigma_{B}}$, in order to use the correlation. We can rearrange the original regression and take an expectation to get

$$\begin{align*}
\alpha &= \mu_{A} - \beta \mu_{B} \\
&= \mu_{A} - \rho \frac{\sigma_{A}}{\sigma_{B}} \mu_{B} \\
&= \sigma_{A} \left(S_A - \rho S_B \right)
\end{align*}$$

That's $\alpha$, which is the expectation, and now we find the stdev.

$$\begin{align*}
\text{Var}(A - \beta B) &= \sigma_{A}^2 + \beta^2 \sigma_{B}^2 - 2 \beta \text{Cov}(A, B) \\
&= \sigma_{A}^2 + \rho^2 \frac{\sigma_{A}^2}{\sigma_{B}^2} \sigma_{B}^2 - 2 \rho \frac{\sigma_{A}}{\sigma_{B}} \rho \sigma_{A} \sigma_{B} \\
&= \sigma_{A}^2 \left(1 - \rho^2 \right)
\end{align*}$$

Combining the two, we get $S_r = \frac{S_A - \rho S_B}{\sqrt{1 - \rho^2}}$.

The second formula, translated into English, is essentially saying that the residual sharpe is given by hedging away as much $B$ as is required to make $A$ uncorrelated to it, and then using the part of the regression that can't be explained by $B$ to determine how volatile this hedged asset is; which quite neatly lines up with our idea of what "residual sharpe" should intuitively mean.

# Correlation from t-stats

We have formulas linking the t-stats and residual sharpe, as well as correlation and residual sharpe. The next equation will link t-stats to correlation. A crucial difference, however, is that previously we were looking at $t_\alpha$ whereas now we will use $t_\beta$. If we have $N$ datapoints in our dataset, then:

$$t_{\beta} = \frac{r\sqrt{n-2}}{\sqrt{1-r^2}}, \, r = \frac{t_{\beta}}{\sqrt{t^2 + n-2}}$$

The latter is just the former but rearranged, so I will only prove the former. Earlier we assumed that we were working with the population level statistics for calculating Sharpe, but here I'll use sample statistics since actually our calculations are drawn from our dataset, which is a sample.

First, the standard error of $t_{\beta}$ is $\frac{\hat{\sigma}_{\epsilon}}{\sqrt{(n-1)s_B^2}}$. Our goal is to first represent $\hat{\sigma}_{\epsilon}$ in terms of $r$ and find a way to get rid of $s_B$. From here I'll simplify $t_{\beta}$ to $t$.

From the regression we have that

$$\begin{align*}
\hat{\epsilon}_{i} &= A_i - \hat{\alpha} - \hat{\beta}B_i \\
0 &= \sum_{i} A_i - \hat{\alpha} - \hat{\beta}B_i \\
\hat{\alpha} &= \bar{A} - \hat{\beta}\bar{B}
\end{align*}$$

We know $\hat{\beta} = \frac{s_{AB}}{s_B^2}$ where $s_{AB}$ denotes the sample covariance, so
$$\begin{align*}
\sum \hat{\epsilon}_{i}^2 &= \sum \left(A_i - \bar{A} - \frac{s_{AB}}{s_B^2}\left(B_i - \bar{B}\right)\right)^2 \\
&= \left(n-1\right)s_A^2 + \frac{s_{AB}^2}{s_B^4}\left(n-1\right)s_B^2 - 2\frac{s_{AB}}{s_B^2}\left(n-1\right)s_{AB} \\
&= \left(n-1\right)s_A^2\left(1-r^2\right) \\
\hat{\sigma}_{\epsilon}^2 &= \frac{\left(n-1\right)s_A^2\left(1-r^2\right)}{n-2}
\end{align*}$$
since we fitted two parameters $\alpha$ and $\beta$, leaving us with $n-2$ degrees of freedom.

Now putting it back into the expression of $t$:
$$\begin{align*}
t = \frac{\hat{\beta}}{\frac{\hat{\sigma}_{\epsilon}}{\sqrt{(n-1)s_B^2}}} &= \frac{\frac{s_{AB}}{s_B^2}\sqrt{(n-1)s_B^2}}{\sqrt{\frac{\left(n-1\right)s_A^2\left(1-r^2\right)}{n-2}}} \\
&= \frac{s_{AB}}{s_A s_B} \sqrt{\frac{n-2}{1-r^2}} \\
&= r\sqrt{\frac{n-2}{1-r^2}}
\end{align*}$$

The formula for $r$ in terms of $t$ is trivial to derive so I will exclude it, but in practice I've found it more useful than the version above. If some research paper produces a strategy against a benchmark or set of benchmarks, they will usually regress the returns and provide the t-stats, but there was a case I had where the researchers didn't include the correlations, so finding $r$ from $t$ actually proved to be useful.

&nbsp;&nbsp;

[<u>Back to top</u>](#){: .page-link}
---
layout: post
title: "Jun 25 Quarterly Opex"
date: 2025-06-21
tags: [quarterly-opex, 2025]
excerpt: Apr-Jun 25 wrap
---

# Introduction

This is the first of what I hope to be many posts, because I have a tendency to start doing things and stop doing them after a month or so when I get tired of it. I plan to do this every 3 months, and in between I also hope to post things if I find them particularly interesting (interesting enough to spend time writing about). Refer to the about page for why I started writing this stuff.

The joke for those who don't know is that every quarter a big batch of options expire and people call it the quarterly opex. I thought about how long it would take for my thoughts to form enough sediment to be worth digging up and putting into a long written ramble, and it's around 3 months. Since this is the first time I am writing this, and I started writing this because I realized I had too many pent up ideas that had to be written down, it means this quarterly opex post will probably be longer than the next few. It will also include things I have thought about in the distant past, and not necessarily just the past 3 months.

I plan to structure most of my quarterly opex posts in the following fashion: some interesting math topics I came across over the past period, followed by some random topics I've thought about (will probably always include a section on music), followed by a section on finance. The reason why it is ordered this way is that there are a lot of things in finance that are basically some idea from the random thoughts section but expressed in a finance way. And math is the first section because math comes first.

## Content links
- [Math](#math){: .page-link}
- [Random thoughts](#random-thoughts){: .page-link}
    - [Gambling society I](#gambling-society-i){: .page-link}
    - [AI and the "smell"](#ai-and-the-smell){: .page-link}
    - [Signaling](#signaling){: .page-link}
    - [Music](#music){: .page-link}
- [Finance](#finance){: .page-link}
    - [Gambling society II](#gambling-society-ii){: .page-link}
    - [Ipad kids](#ipad-kids){: .page-link}
    - [Unreasonably good backtests](#unreasonably-good-backtests){: .page-link}
    - [Price sensitive](#price-sensitive){: .page-link}
    - [Polymarket Jesus](#polymarket-jesus){: .page-link}
    - [Things I've been working on](#things-ive-been-working-on){: .page-link}


## Math

### The centrifuge problem

[<u>Here's the link to a write-up on it.</u>](https://mattbaker.blog/2018/06/25/the-balanced-centrifuge-problem/){: .page-link} This is just a cool problem. I thought at first that it had to do with some properties of the cosets of finite rings but it turned out to be something else entirely.

### Graph colorability

If you want to figure out whether a graph is k-colorable, you can just encode it using its graph polynomial, $\prod_{\lbrace u,v \rbrace \in E}\,(u-v)$, and calculate the Gr&ouml;bner basis of this and $v^k - 1$ for $v \in V$. Clearly if 1 is in the basis then you know it's k-colorable, else there would be some pair of adjacent vertices with the same color (represented by a k-th root of unity). This isn't so much of a big complicated fact as it is something to make computation easier.

### Shapley-Folkman

Speaking of Gr&ouml;bner bases, there are lots of mathematical objects that admit some form of deconstruction into "bases" or smaller generating elements that serve a similar role. There's bases for vector spaces and topologies (sometimes the properties of local bases are not satisfied by the bases for the whole space). You can generate $(\mathbb{Z}, +)$ with {1}, and $(\mathbb{Z}, \times)$ is not a group but you can kind of see it being "generated" with 1 and the primes.

Anyways, Shapley-Folkman is a nice result that says: if you have a convex hull in $\mathbb{R}^m$ generated from the Minkowski addition of $n$ sets $S_i$, you can find some representation of ANY point in the convex hull as the sum of only $m$ points in the convex hulls of some $S_i$, and the rest of the $n-m$ points can just be in $S_i$ directly. Here's a pic I stole from Wikipedia to illustrate:

<div align="center">
    <img src="/assets/images/Shapley_Folkman_lemma.svg.png" alt="Shapley-Folkman in 2d">
</div>

There's 4 points in 2 dimensions. The lemma states that to get to point +, you just need to adjust the "inputs" in two of the sets within their convex hull, and the other sets can just "freeload" there.

The proof of this is a nice pigeonhole argument. Say we have point $x \in conv(S)$ that we want to represent ($S$ is the Minkowski sum of the $S_i$). We know we can just take some $y_i \in conv(S_i)$ such that they sum to $x$. Then, we represent each of these $y_i$ as a convex sum of $z_{i,j} \in S_i$. Essentially, we represent $x$ as the sum of points in all the convex hulls (none of the "inputs" are "freeloading") and represent those inputs as a convex sum.

Next, we attach $n$ more 1's to $x$, and for each $z_{i,j}$ we append $(0,...,1,...,0)$ where the 1 comes at the i-th position. Since for each $i$, $y_i = \sum a_{i,j}z_{i,j}$ for $\sum a_{i,j} = 1$, after we add the $n$ new dimensions at the end we get the same relation. Therefore, $x' = \sum_{i} \sum_{j} a_{i,j}z'_{i,j}$.

The point of doing this was to make all the $z_{i,j}$ turn into unique points in $\mathbb{R}^{m+n}$. Now we can just use Carath&eacute;odory's theorem and say $x'$ is the sum of $m+n$ of the $z'$ and that the rest can have $a_{i,j} = 0$.

We can now remove all the extra 1's we added to go back to $\mathbb{R}^{m}$. Remember that $y_i = \sum a_{i,j}z_{i,j}$. We know there are $m+n$ nonzero values of $a_{i,j}z_{i,j}$ and $n$ of $y_{i}$ in total. Therefore by the pigeonhole principle, only $m$ of them have multiple nonzero values of $a_{i,j}z_{i,j}$, and the rest only have 1 value and thus satisfy $y_{i} \in S_{i}$ (freeloaders).

I think of this as a kind of "basis" representation of that point in the convex hull. You can specify points in large complicated sets with just a small number of values, bounded by the dimension of the set.

### Tutte polynomials

There are two characterizations of Tutte polynomials. One is the intuitive recursive version that quite literally counts bridges and loops. The other is $T_{G}(x,y) = \sum_{A \subseteq E}\,(x-1)^{k(A)-k(E)}(y-1)^{k(A)+\|A\|-\|V\|}$ where $k(A)$ is the number of connected components of the subgraph $A$. It is easy to prove that the summation version satisfies the properties of the recursive equation but not so easy to prove the other direction (that it is the only formula to satisfy this). That is probably something I will only figure out in university.

The reason I came across this was because apparently, $T(1,1)$ satisfies the same function as Kirchhoff's theorem, that the number of spanning trees of a graph is equal to the determinant of any cofactor of the graph Laplacian.

On the topic of graph Laplacians, something else I've been putting off for a while now is reading an article about chip-firing games. This is why I have 100 tabs open at any time because I keep saving things to read later but never actually read them.

## Random thoughts

### Gambling society I

One thing I have been thinking about a lot is the "gambling society" idea. I suppose it could be considered a "hypothesis" because it is actually testable. There are two parts to this. This one is about some overall observations, and there's another part that goes under the finance section because I talk about options and risk neutrality. But because the topic is gambling, it's inevitable that there will be some finance related stuff in this section.

The idea is that society as a whole has accelerated towards the normalization (or, as I talk about in the second section, a reconsideration of the discount factor) associated with gambling. We will talk about normalization first through the na&iuml;ve lens.

A few observations first:
1. People use their phones more. It's easier to gamble on your phone. Everything I talk about below can be done on your phone or some other electronic device.
2. Sports betting is a 100B industry growing at an average estimate of 6-10% CAGR. I think that's conservative.
3. Polymarket daily volume is in the 8 digits. It's big enough that there's actual institutional market makers in it (SIG).
4. Kalshi is, at the time of writing, regulated not by local authorities that are supposed to enforce rules on betting, but by the CFTC, whose job is not to enforce rules on betting. This is due to the current political situation. [<u>Matt Levine writes about this.</u>](https://www.bloomberg.com/opinion/newsletters/2025-06-17/it-s-not-gambling-it-s-predicting){: .page-link}
5. A lot of things that are not gambling are becoming gambling. It started with WSB. Some more examples related to this are the rise of 0dtes, crypto scams, and generally the nonstop pumping of highly speculative retail stocks.
6. There is celebrity endorsement (Drake) of gambling and this links to the use of social media. I'm sure Stake spends lots of money to increase the reach of their gambling posts. Of course there are also politicians that endorse similar things (point 5).

Instead of making a value judgment about this I think it's more important to explore why it's happening and what we should do about it. I mean the latter in the sense of "as an individual human, given that this is happening, what is the best conditional action I should take to maximize my own benefit" and not "what should society do".

Why it's happening is quite obvious but also not quite obvious (explained in part 2). The obvious part is that phones and social media made gambling more accessible and more desirable. People have a natural tendency to gamble. You make it easier for everyone and obviously there will be more gambling.

There is also the issue of a gambling culture. This is harder to quantify, but I think it's happening. A culture that legitimizes instead of shames gambling has a reinforcing feedback loop and you don't instantly see the impacts of it, because most modern gambling is noisy enough so that luck can be misconstrued or misrepresented as skill.

People gamble on negative EV outcomes for two reasons. The one we are talking about now is that they don't have perfect information and think that the EV is actually positive. If you think you have skill at picking the next crypto 10000x-er, or highly shorted stock poised for a GME style squeeze, or in putting on sports parlays, the only feedback you get from this process is the outcome (+/-PNL). If your prior distribution of your own skill is extremely skewed to "I am highly skilled at this", then you are not going to stop betting because you lost a few times in a row. You probably also don't give a shit about Bayes' theorem and overweight positive evidence in favor of you having "skill". In short, if you model gambling as a random walk with drift for most people, the reason most people start (under our current assumptions) is that they think their drift is positive, and once they start they don't stop because they don't know how to / don't care to evaluate whether their random walk has positive or negative drift.

This is simplistic too because there are other motivations for gambling. Peer pressure is one of them. You get peer pressured by people you see online who struck it big. We didn't have this problem before social media.

The funny thing is that we have a risk-averse culture in most parts of the world, and yet this is the one thing everyone seems to be risk-taking on. Because most actions with convex, risky payouts require work, and gambling is easy. Of course there are people taking the convex risky bets (like making a startup). I'll talk about them in the next section.

The last bit of the "why", I think, has to deal with existential dread. Everything feels out of reach, and more so with AI. What's the point if actually trying to work towards something offers little upside? This is a doomer viewpoint, but I think a sufficient number of people are starting to buy into this idea, and a good number of them are by no means "stupid".

And thus we come to the topic of <i>scam theory</i>. It's just a dumb name for the fact that the worst, scammiest, dumbest sounding names in the equity space have all seemed to outperform spectacularly over the past months to a year. It was especially apparent during the post-liberation day rally. While funds were net short and every macro person was calling for risk-off, retail names like PLTR, CRWV, and CRCL just kept going up. RGC makes quack traditional Chinese medicine, has never turned a profit in its history, and its stock went up 600x in a year. I think if we are to believe that the endgame for the dollar based world is to inflate their way out of their mess, then there is merit to buying the most fundamentally unsound companies that have captured retail interest and pump the hell out of them.

Everyone looks at historical bubbles and comes to the conclusion that you should not be investing in a speculative bubble. I think that the opposite is true. Obviously this is not financial advice, but you should absolutely be investing during a speculative bubble, and in the most leveraged retail-heavy names, because that's upside convexity. The worst thing that can happen is that everything crashes all at once, but the default assumption is that stocks keep going up and in the case of these stocks, you have a very long right tail. It's free convexity for delta-1 investors. When everyone wants tulips, and the left tail is priced richly since people know what happened to bubbles in the past, you can buy tulips and put spreads.

One last thing I heard about recently was that Labubus were becoming ridiculously popular again in China. I thought this trend died last year, but apparently it is alive and well. When there is money sloshing around everywhere with no feasible outlets, these kinds of stupid things become the release valve.

### AI and the "smell"
Terence tao, bluffing into success (AI hacking social methods), NGMIism and SF tech broism

[<u>Terence Tao went on Lex Fridman's podcast recently.</u>](https://www.youtube.com/watch?v=HUkBz-cdB-k){: .page-link} I don't know how Lex convinced him to do a 3 hour podcast but it's quite interesting (I skimmed through most of it). Terence puts complicated things in an accessible way.

One of things they talked about (I think around the 2 hour mark) was how AI could "hijack" our human sense of smell for the quality of something, such as a mathematical proof or a piece of code. That's what most people have observed after using AI for a while: it bullshits very confidently. It's ok in qualitative disciplines to an extent, but its horrible in math because it would make a nice-looking proof that looks completely correct but the error would be some absolutely asinine mistake that no real human would make. I get his frustration because I've seen it before too.



### Signaling
NS, AI and schools as signaling, slatestarcodex school piece

### Music
the types of music listeners, non english music, why i cant work with music that has lyrics, listening to "mid" music

## Finance

### Gambling society II
friedman-savage utility, risk neutral pricing, why gambling society only works with capitalism

### Ipad kids
risk reversals

### Unreasonably good backtests
VX model, peso problem, toxic risk

### Price sensitive
how to get the fair price if the market is "fair" under risk neutrality

### Polymarket Jesus

### Things I've been working on
CRWV chart, problem with BS pricing
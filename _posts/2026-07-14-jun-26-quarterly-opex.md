---
layout: post
title: "Confidence Intervals - Jun 26 Quarterly Opex"
date: 2026-07-14
tags: [quarterly-opex, 2026]
excerpt: Apr-Jun 26 wrap
---

## Introduction

The first year of university is over, and it went by much faster than I had expected. The last time I seriously thought about my subjective experience of time was when I was in the army, in the earlier days of the 2 years when the concept of being taxed some of the best years of your life still stung acutely. During the first two months when I was on Tekong there were frequently planes flying overhead and I would cope during the physical trainings by imagining what it would be like once it was all over and I was flying on one of those planes to somewhere far away. I remember frequently conjuring the image of a long straight tunnel where far off at the projective infinity there was a speck of light, so far off that there was never any change in its distance from me. When the first rush of novelty wore off after basic training and we were threw into the mundanity of unit life I experienced the additional terror of having to imagine myself wading through the swamp of monotonous mind-numbing work for another 1.5 years.[1](#fn-1){: #ref-1 .page-link .footnote} It doesn't feel as long in retrospect, and was made a lot more bearable by the people who were in it together with me. But how odd it is that I can look back upon it now and feel nearly no compassion for the person who I was just 3.5 years ago, the stranger who shared my body spacially but had such a different subjective experience of life as I do now.

I used to think that I found army life to be much shorter in my memory because there was a lack of memorable events to benchmark my experience to; every day was roughly the same, save for some occasional distractions and high intensity conducts, and even though I could roughly map out what I was doing during each of the few months in my own time,[2](#fn-2){: #ref-2 .page-link .footnote} there was nothing particularly different about the general structure of how my days went and so it all ended up feeling like the same day over and over for 1.5 years (it's not much different for my experience of school life). But the weird thing is that even though in university there was a great amount of variability to how my days went, and absolutely no shortage of memorable events, it still feels like the first year went by before I was ready to let it pass. One possible explanation for this is that it has actually not been that long since I first left for university, because there have only been 3 2-month stretches at a time when I was actually in Oxford and 2 more 1.5-month stretches when I was either traveling or staying at home. Usually events in life seem long during observation and short in retrospect; here I would hazard a guess that term time seemed short because much of it was spent on problem sheets (and later revision for prelims) which have the magical time-warping property of always taking twice as long as expected.

From April to June, a sizable chunk of my time was taken up by exam revision. It was quite difficult to simultaneously keep so many months' worth of knowledge in the mind for the entire period up until the week of exams, and unlike almost every other subject, the prelims math exams consisted of five papers one after the other in the span of a week. Therefore, the process of revision was a race to remember as much as you could before it all dissipated by the next time you had scheduled to look at that particular topic. Consequently the mental load of content to remember was the highest before the first paper, and things got much better as the exam week progressed. Unfortunately that week was that a record heatwave had been sweeping across the whole of Europe, building up to its climax during the exact week I had all my exams, and easing to a denouement right after I flew back to Singapore. For a whole week Oxford was hotter than Singapore and there was no AC anywhere. My room there also had the frankly inexplicable property of being colder than the outside in the winter, and hotter than the outside in the summer; not even a giant standing fan pointed outwards to suck the hot air out was of relief for a sufficient amount of time. In the end I concluded that it was futile to reduce the temperature in my room, and it was easier to increase the outward heat flux from the surface of my skin by taking my shirt off and pointing the fan right at myself, which is what I did (it didn't really help either).

To my own surprise, I have had a fair bit to think about outside of revision over the past quarter. I anticipated this edition of the quarterly post to be much shorter than usual, but instead I've had such an excess of material to cover that I omitted some things. Additionally, a nice property of this post is that I had a revelation and came up with a topic where all of the major sections have some overlap, which is the topic of confidence intervals. In the math section I will first discuss some different interpretations of confidence intervals, and later on we will see how the accurate estimation of such intervals is of practical interest in general life situations outside of statistical measurement.

## Content links
- [Math](#math){: .page-link}
    - [Confidence intervals](#confidence-intervals){: .page-link}
    - [Yet another matrix problem](#yet-another-matrix-problem){: .page-link}
    - [Unit distance problem](#unit-distance-problem){: .page-link}
    - [Khinchin's constant](#khinchins-constant){: .page-link}
    - [A card game](#a-card-game){: .page-link}
- [Random thoughts](#random-thoughts){: .page-link}
    - [Miscalibration I](#miscalibration-i){: .page-link}
    - [Miscalibration II](#miscalibration-ii){: .page-link}
    - [Buttons](#buttons){: .page-link}
    - [Other interesting things](#other-interesting-things){: .page-link}
    - [Music](#music){: .page-link}
- [Finance](#finance){: .page-link}
    - [QVR](#qvr){: .page-link}
    - [SK Hynix](#sk-hynix){: .page-link}
    - [Who defines fairness on Polymarket](#who-defines-fairness-on-polymarket){: .page-link}
    - [Safe Haven: a book review](#safe-haven-a-book-review){: .page-link}
    - [Other finbro things](#other-finbro-things){: .page-link}
- [Final thoughts](#final-thoughts){: .page-link}

## Math

### Confidence intervals

Last term we finally started on statistics and data analysis which was the same length as the other standard 8-week courses but was crammed into 4 weeks because of the revision schedule for prelims. During one of our tutorials my tutor had the following remark about confidence intervals: "If we have a confidence interval for a parameter of an observed random variable, it is incorrect to say that the parameter has a $1-\alpha$ chance of being in the interval, but rather we should say that with probability $1-\alpha$ the interval we give contains the parameter, as the parameter itself is fixed but the interval is not." This statement is in fact only partially true. For the purposes of our course, where our treatment of probability views random events as being modeled using repeatable experiments under a fixed distribution, we must define confidence intervals as my tutor did above in accordance to the interpretation given by frequentism.

However, consider what happens when we do not assume that the parameters are objective and deterministic. Then the parameter we are estimating carries a distribution according to the data, and therefore it is correct to define the probability of the parameter being within an interval. This perspective is the definition under Bayesian statistics of a confidence interval.

This is not a trivial difference, because using the different methods built up from frequentist and Bayesian interpretations can give us different confidence intervals, even under uninformative priors. Let us choose $n$ large so that we can apply CLT, and consider the following problem:

Suppose we have an experiment with a weighted coin. Say we flip it 40 times and it comes up heads 6 times. Under the frequentist interpretation we were taught, it is very easy to quote off a confidence interval for this; $n = 40$, the MLE of $p$ is $\hat{p} = 0.15$, we assume that we can use the MLE of $p$ in its variance, so that the 95% confidence interval is $\left[\hat{p} \pm 1.96\sqrt{\hat{p}(1-\hat{p})/n}\right]$ or about [0.04, 0.26]. Under a Bayesian interpretation, we choose the uninformative prior of Beta(1,1), and since we observe 6 heads and 34 tails we get the posterior Beta(7,35). The 95% credible interval we get from this is [0.07, 0.29]. The intervals are not the same because the CLT version is symmetric around 0.15, whereas the Bayesian version is skewed upwards because we started with the assumption of having one "fake head" and one "fake tail" under the uniform density prior.

### Yet another matrix problem

In the previous post I went through a matrix problem that my friend introduced me to. This quarter I came across another interesting problem involving matrices. Some time in Michaelmas I entered into a math competition hosted by QRT; this was a team competition and I went with a friend who did math and to fill the team of 4 we brought along two other friends who didn't do math. Against our own expectations we beat a whole bunch of other teams to place second in the university and got invited to the national finals against the top few teams from Cambridge, Imperial, and UCL. After a few months they finally got around to hosting the finals, and the moment we walked into the reception area before the competition we saw 3 different people with IMO merch and we knew we were going to get cooked. Surprisingly, again, we managed to get 4th, and we were extremely close to getting a full solution one of the questions which would have gotten us to 3rd.

The competition included a few answer-only questions (one of our teammates who did not do math spent the whole competition bruteforcing an answer-only optimization question and managed to get the highest score on that question), and a few proof-based questions which were marked very similarly to IMO questions but on a scale of 0 for wrong solutions, 0.5 for partial solutions in the right direction, 0.9 for nearly correct proofs, and 1 for full proofs. Similar to the original university-level competition, there was a live leaderboard showing whether a team got a question correct or not, and we had a fixed number of solutions with a maximum number of tries allowed per question. So part of the strategy was deciding whether to attempt questions you know everybody else is getting wrong, because on one hand it means that the question is probably harder than the others, but on the other hand their scoring metric meant that questions with more wrong submissions were worth more marks.

There was one infamous question P3 that nobody got a full solution for. The question read: Let $M$ be a $n \times n$ matrix where the element in the $i$-th row and the $j$-th column is $\cos (i-j)$. What is the rank of $M$? Upon a cursory inspection of this question most people would have guessed that this was a rank $n$ matrix, or that at the very least the rank was $O(n)$, and so I'm guessing a bunch of the other teams sent in some guesses to scope the question. (There was also a mechanism where you got extra marks for submitting correct answers to proof questions early.) I don't think this was a good strategy from them, unless they were confident in their ability to solve it after knowing one wrong solution, but as the wrong answers piled up it became obvious free information to the other teams that this was not a rank $n$ matrix, and it also probably was not a rank $n-1$ matrix, because one team sent in two answers and both were wrong. After a while teams seemed to have given up on this question. Since we weren't sure of what the actual answer was, we similarly decided to skip this question for most of the competition.

In the final five minutes, however, it appeared that there was not much else that we could do regarding the other questions and so I turned my attention to this problem, which had the highest potential value to us as the question with the most fails and not even a single partial solution. After some expansions on small values of $n$ a sudden inspiration hit me and I realized that I had been blindsided by the spectral theorem stuff I was revising for the linalg paper at the time and that there was a very simple recursive property in the rows of $M$: for $n > 2, i > 2$, the $i$-th row $M_i$ satisfied $M_i = 2 \cos(1) M_{i-1} - M_{i-2}$. I basically had 30 seconds left at this point and scribbled this as fast as I could on the submission sheet that for $n \ge 2$, the rank of $M = 2$. I'm sure if I had more time I could have spun up some proof by induction of this fact, but simply for noting this (which was the correct answer) we managed to get 0.5 marks for this question, the only partial solution of this question by any team.

Afterwards I realized that all my work could actually be expressed in a far simpler form, given that I already had the expansions down:

$$M = \begin{pmatrix}
\cos 1 & \sin 1 \\
\vdots & \vdots \\
\cos n & \sin n
\end{pmatrix}
\begin{pmatrix}
\cos 1 & \cdots & \cos n \\
\sin 1 & \cdots & \sin n
\end{pmatrix}$$

And we immediately arrive at the required solution.

### Unit distance problem

Recently OpenAI published a result related to an open problem in geometry, known as the planar unit distance problem, where they claimed their internal models have found an improved solution to a longstanding conjectured solution. The impressive thing about the proof seems to be that the AI was able to 1) intuit that the given conjecture was likely wrong and spend most of its time trying to construct a counterexample, as shown from the CoT, and 2) it managed to use techniques from a very different field of mathematics to solve this problem, showing that "that there is a lot more that number theoretic constructions have to say about these sorts of questions than [human mathematicians] suspected ... no doubt many algebraic number theorists will be taking a close look at other open problems in discrete geometry in the coming months."

To provide my own very unqualified opinion on the subject, I think it's quite reasonable to expect that AI would be able to spot links between disparate fields of math much more easily than humans could, and that specialized models built for math could perhaps be even more capable of spotting the structures that exist across different domains. Like the Chinese idiom of blind people trying to describe what an elephant is like by feeling only a small part of it, many individual human mathematicians are only able to understand increasingly small and niche areas of mathematics; we have progressed far from the days when individual polymaths like Gauss and Euler were able to simultaneously make contributions to a vast number of fields in math due to the primitive understanding we had of each field. Now if AI is able to behave as if it was many thousands or millions of mathematicians describing the elephant at once, it would naturally have a better idea of some subtle links that humans would not be able to find, and this would only become more true as math becomes more advanced and getting to the frontier of research requires more knowledge and effort to catch up with all the important research that has happened up to this point. I suspect that in the near future we could see AI come up with some more crazy conjectures like monstrous moonshine that can only come from a deep understanding of many fields simultaneously.

I recently got to try out Fable 5, which was lauded as "basically AGI" or too dangerous to be released to the public, and my first impressions are that it is extremely impressive at doing anything related to coding, but still struggled to reason deeply about complicated math problems. I threw the research problem I was working on at it, and as I had predicted it was good at drawing links to other concepts in the field that I had no idea existed, but aside from throwing up a scattershot attempt at linking existing ideas to the problem, it wasn't able to make any concrete theoretical advancements beyond what I had already provided it (some of which it ended up getting wrong even after being given existing results). I wouldn't say with any certainty when publicly available models become advanced enough to oneshot any questions I could have at my level, but I am quite certain that it will happen at some point.

Another observation by Yuan Qiaochu: [<u>AI is good at doing high level math and not so good at doing high level writing</u>](https://x.com/qiaochuyuan/status/2055404224457163132?s=46){: .page-link target="_blank"}. If you were active on the math stackexchange, which was essentially last relevant before 2022, you would surely have seen this guy in the answers of some question (aside from being a prolific answer writer on stackexchange he's also a prolific writer in general). As I will go into more detail about later, right now a majority of people would prefer AI writing over human writing, but a decent minority can still tell when things are clearly written by AI, and to people who actually care about this stuff the AI generated output is very obviously worse. It's debatable whether the content and style of writing is worse (I think it is, and it is horribly unnatural) but a major gripe I have is with the lack of actual substantive information being intentionally passed from author to reader in non-descriptive or non-informative contexts. In contrast to the watertight rigor of mathematics and coding, human language is lossy and unstructured and takes on so much more meaning than its functional purpose of "informing"; recall [<u>this quote</u>]({{ "/2026/01/17/dec-25-quarterly-opex.html#other-interesting-things" | relative_url }}){: .page-link target="_blank"}:

> We can still use language to access objective reality, as long as we’re prepared to let it take a more active role than straightforward description. Language, and especially philosophical language, changes how the world discloses itself to us.

How can a machine that reasons in its own invented machine-speak because it is far more efficient than reasoning in any of our human language come up with words that capture the same lossiness, the imperfection and ambiguity and smallness of human experience? Sam Kriss writes in a [<u>separate piece</u>](https://samkriss.substack.com/p/if-you-let-ai-do-your-writing-i-will){: .page-link target="_blank"}:

> "I’m literally the size of a dry martini — shaken, stirred, and nursing the burn of every sip." ... In the same way that no human mathematician would have thought to use Golod-Shafarevich class field towers to generate point sets [note: this is referring to the unit distance problem], no human writer would ever write that sentence.

With how convincing AI generated text is already, I doubt there is much incentive for further improvements in this direction, but if one day AI could mimic the blind ramblings of humans trying to figure out what the elephant of our existence looks like, I fear there would be no purpose left for us at all.

### Khinchin's constant

I saw this very interesting result recently, stating that:

If $x = \lfloor x \rfloor + \frac{1}{a_1 + \frac{1}{a_2 + \frac{1}{\ddots}}}$, meaning that $(a_i)_{i \geq 1}$ is the continued fraction expansion of a real number, then for almost all real numbers, $\lim\limits_{n \to \infty} (a_1 a_2 a_3 \dots)^{\frac{1}{n}} = 2.6854520010 \dots$ where the right hand number is known as *Khinchin's constant*. My first reaction on seeing this result was bewilderment, but then I was reminded of something very similar I had seen about Benford's law, which gives a distribution of leading digits of (what can be taken to be) random draws of numbers under a specific form of uniformity. If this limit holds for almost all reals, then certainly it is proven by some result of a form like Benford's law, which gives a distribution of random draws of digits.

Indeed Claude told me that it was so: Benford's law comes from the same family of distributions as the Gauss-Kuzmin distribution, which gives us the distribution of continued fraction quotients $a_k$, which are not necessarily only from 1-9 as leading digits are. In both cases, we are interested in a measure that stays invariant after some map. In the first case it is the map $x \mapsto cx$ because Benford's law is observed for scale invariant constants, and so the measure we want is $\frac{dx}{x}$. In the second case, it is the map $x \mapsto \lfloor \frac{1}{x} \rfloor$ because that essentially "pops" the leftmost partial quotient out of the continued fraction, and the invariant measure here is $\frac{dx}{1+x}$. We skip a bunch of ergodic theory and assume that these distributions (after multiplying by a suitable constant to make them probability distributions on their domain) are how we find $P(a_i = k)$ (regardless of whether $a_i$ here refers to the leading digit or the digits in a continued fraction). Thus we find:

$$P(\text{leading digit} = d) = \frac{1}{\ln 10} \int_{d}^{d+1} \frac{dx}{x} = \log_{10} \left(1+\frac{1}{d}\right), d = 1, 2, \dots , 9$$

$$\begin{align*}
P(\text{quotient } a_i = k) = P\left(x \in \left(\frac{1}{k+1}, \frac{1}{k}\right]\right) &= \frac{1}{\ln 2} \int_{1/(k+1)}^{1/k} \frac{dx}{1+x} \\
&= \log_{2}\left(1+\frac{1}{k}\right) - \log_{2}\left(1+\frac{1}{k+1}\right) \\
&= \log_{2}\left(\frac{(k+1)^2}{k(k+2)}\right)
\end{align*}$$

Notice that if we are taking the limit of the geometric mean of values randomly drawn from these distributions, we can simply calculate the products of each value to the power of its probability of appearing in the limiting distribution. Thus for Benford's we get:

$$\prod_{d=1}^{9} d^{\log_{10}(1+1/d)} \approx 2.6138$$

And for Khinchin's constant, we get:

$$\prod_{k=1}^{\infty} k^{\log_{2}\small(\frac{(k+1)^2}{k(k+2)}\small)} \approx 2.6855$$

### A card game

[<u>One last interesting problem</u>](https://math.stackexchange.com/questions/2771661/say-red-with-playing-cards){: .page-link target="_blank"}: consider a game where you have a standard deck of 52 cards, and you draw them one by one. Before each card is drawn you have the opportunity to say "red", and if the card drawn is red you win, otherwise you lose. It is not stated
in the question here, but it is implied that if you do not say red at all then you will lose. The question asks: is it possible to do any better than 50/50?

Intuitively, the setup is symmetric in red and black cards, and it is probably not possible to do better than 50/50, which indeed is the answer. It's a bit harder to prove that no strategy does better than 50/50, but to start, it is sufficient to notice that in order for a strategy to consistently beat 50/50 then by assigning a payout to winning, your EV (of winning) from saying "red" at a specific card should be higher than 50%, and thus the only thing we need to consider is whether this can possibly hold over many iterated runs of the game. The accepted answer on the post provides a very neat inductive argument for why the probability of winning (ie, the EV of the indicator variable of winning) is always 50% in this case.

## Random thoughts

### Miscalibration I

If you have been on Metaculus, you would notice that the way many of their questions are set up allows people to predict based on a distribution of likely outcomes instead of quoting a single value. When you ask people in real life for the likelihood of something, most people only give you one value ("yo how long are you gonna take to get here" "around like 10 minutes" (it's never around 10 minutes)), and this value is often worse than when you force them to frame their thinking from upper and lower bounds, and what the various percentiles of results would look like, because most likely you aren't thinking about the distribution at all when you lazily give an estimate of the mean (which would make it way off). A slightly better compromise is to consider *two* central moments / statistics instead of one, which forces you to think distributionally without going through all the nerd stuff people get up to on Metaculus. 

You would think that AI would be much better than people at doing things like this. It has access to more information, is able to reason more clearly than not just the average human but most humans, and it also pays an inhuman amount of attention to every single detail that could be relevant to the question. In fact, depending on who you ask, the AIs are [<u>already beating</u>](https://www.astralcodexten.com/p/the-ai-superforecasters-are-here){: .page-link target="_blank"} all but the best human superforecasters at prediction, which isn't surprising because there's a lot of money to be made in this. It's interesting to consider to what extent forecasting can improve based on only macroscopic observations, and whether some day AI would be able to simulate even the microscopic conditions of the human brain so well that it could predict the exact next state of the world through evolving the little dynamical systems in our heads.

Right now at least, it's odd that AI is simultaneously extremely capable of forecasting and yet still so maddeningly overconfident in its own judgments. Perhaps it is an issue of scaffolding and proper prompting, but as the ACX article reports, the current frontier models are only 9 months behind the best purpose-built forecasting AIs. Therefore, the best public models right now can't possibly be that bad at estimation either. So why can't they accurately assess how correct they themselves are? You can see Campbell complain about his overconfident AI assistants [<u>here</u>](https://www.campbellramble.ai/p/systems-101-overconfidence){: .page-link target="_blank"}. He's using the best models that the leading labs have to offer. Now spare a thought for the people who are themselves unable to accurately judge the credence of things on their own, who don't have access to the best models or let their own biases enter their questions, and treat whatever AI says as the truth. The same overconfident AI, with its authoritative and overzealous tone, is now giving gullible and uncritical people an immense amount of confidence to do things that may turn out to be ill-advised.

Aside from overconfidence, there's also a small subset of cases where AI is underconfident in value-destroying ways, which I surmise to be a reflection of guardrails built into the AI during training. An example of this is in this [<u>trading game</u>](https://crystal-ball.elmwealth.com/){: .page-link target="_blank"} where you're given a newspaper front page from the day after an important event or data release, and with all information related to the market's reaction blacked out, you're supposed to make a trade from the previous day. It's not very hard to beat the AI if you spend some time looking at the news, and Claude's performance on this was quite impressive compared to the other models but still nowhere close to what a focused human could achieve. You can observe the reasoning that each model gives for their trades, with most of the models observing that there are times where they are more confident in their guesses and times where it's hard to tell, but none of them seem to be able to size down or size up properly. They never used 50x leverage, even when they claimed to be nearly certain, and their inability to use the easy rounds to make up for difficult rounds ultimately cost them heavily in terms of performance.

![My results vs AI results](/assets/images/jun26opex/crystalball.jpg){: .flex-img style="--img-width: 280px;"}

Perhaps the models were biased by the given persona of a "typical middle-aged, wealthy investor" to be more conservative with their bets, but ultimately their inflexibility in choosing bet sizes went both ways and it's quite clear that they were unwilling to take too little or too much risk. If we are content to hand off most of our thinking and decision making to AI already, I don't see why we wouldn't be OK with training them to be less hesitant to do risky things (when it is aware that what it is doing is risky). Surely the machine god has a better idea of what's dangerous and what's not than ourselves?

### Miscalibration II

To continue the thought from above: humans are ridiculously bad at assigning an estimate to things. We are all the worst parts of AI: overconfident and blustery when we have very little information, and underconfident and indecisive when we face complicated decisions where we have more information. I think the latter is a far larger failure, because it tends to occur when we have to make important choices, but I want to focus on one very funny subset of humans being bad at estimation, which is when it comes to detecting whether something is AI or not.

[<u>Here's</u>](https://x.com/Jediwolf/status/2054776716770320631?s=20){: .page-link target="_blank"} an experiment where someone posted a picture of a real Monet painting, claimed that it was AI, and asked people to describe why they thought it was worse than a real Monet. And you can see all the commenters coming up with all sorts of detailed analysis (or not, some of them had no arguments other than "it's garbage") to justify why they found the picture to be worse than the other Monet paintings they have supposedly seen. (This perhaps makes for interesting commentary on the value we ascribe to works of art by famous artists, if having the framing of "this thing is potentially AI-generated" takes away the subconscious overfitting to other peoples' views on the artwork.)

We've all been cautioned against trusting what we see to be real, but sometimes this overly cautious priming works against us. We don't want to become the "boy who cried AI", but neither do we want to let liars and cheaters get their way by giving them too much benefit of doubt. The solution, as before, is in being more aware of what confidence interval we would assign to our guesses. If after comparison with other Monet paintings (which I don't think any of the commenters bothered to do) the image was indeed difficult to fairly rate against the rest of his work, then the correct response is just no response.

In general it's been shown pretty convincingly that the vast majority of people are now no longer able to detect a significant difference in frontier AI writing and human writing, and many even prefer the AI generated versions. In a [<u>side-by-side quiz (paywalled)</u>](https://www.nytimes.com/interactive/2026/03/09/business/ai-writing-quiz.html){: .page-link target="_blank"} of AI-generated text vs works from the same genre, people on average preferred the AI version in 4/5 categories:

![Quotes covered in case you want to try it](/assets/images/jun26opex/nytquiz.jpg){: .flex-img style="--img-width: 300px;"}

I suspect that many of the same people who showed a preference for the AI-generated text here would be [<u>far less inclined</u>](https://link.springer.com/article/10.1186/s41235-023-00499-6){: .page-link target="_blank"} to vote for it if it was clearly labeled which excerpt was written by AI and which was written by a human.

You would think that people who spend more time reading, especially writers themselves, would find it easier to detect the sickening gloopiness in AI-generated text. Yet there are some times when the clearly AI-generated content is still bafflingly considered better by no less than those who claim to be our eminent vanguards of art. This year's Commonwealth Essay prize winner, for example, was entirely AI-generated. Two other of the five finalists were also entirely AI-generated. Even the judge's opinion on the text was AI-generated. As Sam Kriss [<u>said</u>](https://samkriss.substack.com/p/if-you-let-ai-do-your-writing-i-will){: .page-link target="_blank"}:

> One prize-winning AI-generated short story is bad news. Three prize-winning AI-generated short stories are extremely bad news. If the judge’s commentary on the prize-winning AI-generated short story is also AI-generated, maybe we should pack it up and digest ourselves into grey goo ahead of schedule.

What's worse than using AI to write self-exoticizing postcolonial slop is that the author of the piece doubled down after being caught on the extremely obvious use of AI to claim that "AI was trained on human writing" and therefore it was possible that he had written it himself, as if AI detectors like Pangram (or the common sense of readers) weren't able to tell that no human would ever in a million years write the vapid dreck he claimed to be his own. In an interview with the Times of India he uses his position as a supposedly marginalized writer from the global south to justify this:

> Q: The judges said writers from the Global South are increasingly being asked to prove their humanity alongside their talent. Did you feel that happened to you?
>
> A: I think so. The literary establishment didn’t know me, and there’s a literary elite in Trinidad that I wasn’t part of. I also believe that because my biography described me as an Indian living in the Caribbean, that became another factor. At times I was angry when they asked me to submit drafts and other material, but my wife kept saying, ‘Just do it.’ The Commonwealth also told me these weren’t part of the competition rules and I wasn’t obliged to comply. But I chose to because I didn’t want to jeopardise my place in the final judging. What I don’t understand is why people continue to question the judges’ decision.
>
> Q: Many acclaimed writers like Ursula K Le Guin, Mary Shelley, and JRR Tolkien have also been falsely flagged by AI detectors. Where does this leave writers?
>
> A: What these AI detectors are saying is that if a piece of writing is too polished, it must have been written by AI. I refuse to accept that. AI was trained on human writing. Large language models, to me, are tools, much like a word processor. They don’t replace the human spirit behind creative writing. Ask an AI to write a prize-winning story on its own and see what it produces. You still need human imagination and judgment to create literature.

What facetious nonsense. In a separate [<u>interview with the Atlantic (paywalled)</u>](https://www.theatlantic.com/technology/2026/07/commonwealth-prize-ai-writing-jamir-nazir/687806/){: .page-link target="_blank"} he says:

> Nazir: The first one whose poetry I fell in love with was a guy known as Pablo Neruda from Chile. And his teacher or mentor was a lady known as Gabriela Mistral. Both of them had a profound impact on me. Then there is Derek Walcott, a Caribbean poet who, like Pablo Neruda, is a Nobel Prize winner. The thing that got me attracted to Walcott was his complete disregard for the traditional Western sentence structure, which people cite as one of the things that proves my writing was AI. But Walcott created his own style.
> I looked at how they all write, and I write poetry in their style too. AI must have been fed all their work. And another thing to that: I have significant poems that I’ve posted in several poetry groups on Facebook. Once it’s on Facebook, AI companies will have data-mined that, right? So they have all of that as a reflection of my style as well, right? I wonder if they can attempt to claim it as their own, as AI-generated. Do you think that’s possible?
>
> Oremus: So you mean that AI gets trained on human writing, and then it generates similar writing?
>
> Nazir: Okay, say AI has been trained with the writing of Will. So it understands what Will does, right? Now, when it sees Will’s writing again—if somebody puts Will’s article through an AI detector—because it’s familiar with that style and construct, it tells itself, This must be generated by an AI system. I’m wondering if it is possible.
>
> Oremus: I don’t know. That’s not how a tool like Pangram works. It’s looking for statistical patterns in the language that are more commonly produced by AI systems than by human writers.
>
> Nazir: But is that true? Why, then, has no court of law in any country, even the tiniest country in the world, accepted as admissible any AI-detector system? Not one country. So that shows you, in terms of the reliability—I’m not saying it’s not helpful, but I think there’s still a lot of refining.
>
> Oremus: You had mentioned some of your inspirations earlier, including Walcott and Neruda. What’s your favorite Walcott work?
>
> Nazir: Walcott has a lot of Caribbean poems, right? And I cannot—there are several, and they talk about the destruction of a village because of the sea. And I wrote something like that. It’s quite a change. And I am advertising a little bit, but I have a collection that I have written, my Caribbean collection, sort of Walcott-style. I tried to edit it as much myself as I could, and it’s ready for publication. So hopefully this award will give me the platform to publish this.
>
> Oremus: But do you have a favorite of Walcott’s poems?
>
> Nazir: A story of Walcott’s?
>
> Oremus: Yeah.
>
> Nazir: To be honest with you, I can’t think of a specific favorite right now.

You get the idea. Not only do these people have no shame, they are perfectly happy to lie and try to argue their way out after being caught cheating. At some point you see these tumorous Cluelyisms pop up in every field and wonder whether other people even care about material truth any more, or if personalized vibe-based nonsense will replace all our sources of empirical knowledge. I am talking about the people at the Commonwealth foundation who had to vet this story, and all the other AI-generated slop stories that were crowned regional finalists: surely there had to be humans in there somewhere. Somebody, perhaps MANY judges, had to read his story, see the backlash it generated on social media, and decide that instead of trusting industry experts and the general public, they would collectively remove their frontal lobes and trust the excuses of "creative process" given to them by the author (an individual who most certainly has no conflict of interest in the matter!) and then decide to NOT disqualify him but rather give him the overall prize.

The council of judges not being able to flag this out might point towards a larger trend of [<u>pseudo-illiteracy</u>](https://samkriss.substack.com/p/reading-is-magic){: .page-link target="_blank"} among the "educated" populace:

> [P]rofessors at elite universities increasingly report that their students are no longer capable of reading an entire novel, or even a thirty-page extract; some of them have difficulty making it through a single sentence. Instead of reading and understanding anything, they’re willing to pay \$300,000 for the privilege of dumping an entire text into ChatGPT and submitting its response as an essay.
>
> Probably the most alarming index of this was a study in which a group of **English majors** at two well-regarded public universities in Kansas were asked to read the first seven paragraphs of Bleak House by Charles Dickens, and explain after every sentence what they thought was happening. Only 5% of the students could produce a ‘detailed, literal understanding’ of the text. The rest were either patching together vague impressions from a bunch of half-understood phrases, or could not comprehend anything at all.
>
> One particular stumbling block was the novel’s third sentence, which describes London in December: ‘As much mud in the streets, as if the waters had but newly retired from the face of the earth, and it would not be wonderful to meet a Megalosaurus, forty feet long or so, waddling like an elephantine lizard up Holborn Hill.’ The students found this figurative language impossible; they could only read the sentence with the assumption that Dickens was describing the presence of an actual prehistoric reptile in Victorian London. One respondent glossed it like this: ‘It’s probably some kind of an animal or something or another. So, yup, I think we’ve encountered some kind of an animal these characters have met in the street.’ The study assessed this person as a ‘competent’ rather than a ‘problematic’ reader, because they’d at least managed to form an idea of what the text meant, even if it was wrong.
>
> Bleak House is not an elitist text; not so long ago, it was mass entertainment. When Dickens visited America in 1867, over 100,000 people paid to see him speak. Delighted crowds mobbed him in the streets. ...

... but I digress.[3](#fn-3){: #ref-3 .page-link .footnote}

I fear that our reasoning instruments have been blunted to such an extent, or perhaps were always just as malformed, to the point that a frightening number of people are unable to even begin considering whether they should be confident or unsure at the appropriate times. Sometimes it is highly apposite to assign a lower credence to your own beliefs, which is determined by the very obvious factors of how much you personally know about the subject, how certain you are of your facts, and so on. Other times it is silly to trust yourself so little that you grant the benefit of doubt to charlatans who are very clearly abusing your goodwill. If there's one thing the trading AIs taught us, it's that miscalibrating your confidence intervals can be very costly.

### Buttons

A contentious [<u>thought experiment</u>](https://x.com/waitbutwhy/status/2047710215265730755){: .page-link target="_blank"} on Twitter from a few months back:

> Everyone in the world has to take a private vote by pressing a red or blue button. If more than 50% of people press the blue button, everyone survives. If less than 50% of people press the blue button, only people who pressed the red button survive. Which button would you press?

Every time this poll is run there's always a great deal of bickering between blue pressers and red pressers, usually along ideological lines, and usually blue wins in this version of the problem. The general line of argument among people who haven't failed to understand the question is this:

Red: The rational choice is for everybody to press red, therefore if everyone is rational, everyone should press red.

Blue: There are people who are not rational or could have misread / misunderstood the question and pressed blue, and therefore as many people as possible should press blue because there is a possibility that a loved one might have pressed blue.

Red: Your individual choice contributes a negligible amount to the ultimate balance of things and you should therefore press red as the most rational choice. By pressing blue you are putting your hopes in other peoples' hands.

Some obvious variants include adjusting the threshold for blue to survive, clearly, most blue-pressers will have a cutoff at which they would swap to red. Alternatively, if the vote was not private, then there would perhaps be more impetus to push blue over the threshold in a marginal case.

It's also important to consider the way in which this problem is framed. Some variants of this question include [<u>if we replaced the button with a blender that 50% of people had to willingly step into</u>](https://x.com/rokomijic/status/2047748428235686295?s=46){: .page-link target="_blank"}, [<u>if we knew for a fact that our friends or loved ones had already pressed blue</u>](https://x.com/prerat/status/2047814071903260703?s=46){: .page-link target="_blank"}, [<u>if we were in a drowning tank with two buttons to open the door, one of which only worked if 4.2 billion other people also pressed it</u>](https://x.com/thechaosledger/status/2047958366194930084?s=46){: .page-link target="_blank"}, or [<u>if we knew for a fact that a certain number of people were in a cage and would die unless blue won</u>](https://x.com/tracewoodgrains/status/2049503551286649247?s=46){: .page-link target="_blank"}. The framing of this question matters greatly because we must operate under the assumption that a certain subset of people is picking based off of [<u>vibes</u>](https://x.com/choffstein/status/2048219243418997208?s=46){: .page-link target="_blank"}. Under each case, the "vibe" changes considerably and the logically identical questions are no longer practically identical.

Anyways because all of this discourse happened on twitter you could be sure that the grimiest and most insufferable individuals were compelled to crawl out and provide some indescribably asinine takes. Among the common ones are the smugly-stated claim that red is a "Nash equilibrium" ([<u>it is not</u>](https://x.com/bobmurphyecon/status/2048508388502385049?s=46){: .page-link target="_blank"}, unless other people dying is of no consequence to the individual). Or the invariable allusions back to IQ and natural selection, with seemingly no concern for the fact that children would be subject to the choice as well; not only that, but people who selected blue scored higher than people who selected red on an [<u>IQ test</u>](https://x.com/cremieuxrecueil/status/2050335311624913349?s=46){: .page-link target="_blank"} on average, and were far better at identifying which button required fewer people to save everyone.

Two other interesting spins on the original question: [<u>given that blue is going to fail, would you choose to flip the results if given the choice</u>](https://x.com/flaminhottweets/status/2048572845572145347?s=46){: .page-link target="_blank"}, and [<u>the outcome of your choice now applies to a random person, and a random person's choice applies to you</u>](https://x.com/gfodor/status/2050245431976964158){: .page-link target="_blank"}. The latter should, if people acted rationally, change the answer for a significant number of people, since the people who picked red to maximize their chances of self-preservation at first should swap to blue, and people who voted blue due to not wanting to be morally responsible for causing another's death should now swap to red.

### Other interesting things

In chronological order...

[<u>Related to</u>](https://x.com/buccocapital/status/2055713977884135871?s=46){: .page-link target="_blank"} what I said two opexes ago about [<u>luck being far more important than we realize</u>]({{ "/2026/01/17/dec-25-quarterly-opex.html#chaotic-outcomes" | relative_url }}){: .page-link target="_blank"}:

> I get why the tech outcomes drive some people insane. I’ve joined companies 12 months “too late”, and merely made a good amount of money instead of generational wealth
>
> The people who joined before me weren’t any better or smarter. They just got lucky. Just like someone looks at me and thinks I got lucky
>
> The pure randomness of it all can either drive you crazy or give you an appreciation for the role of luck.

Again, [<u>related to (paywalled)</u>](https://www.nytimes.com/2026/05/17/opinion/chatgpt-ai-college-school-graduation.html){: .page-link target="_blank"} what I said three opexes ago about [<u>the prevalence of cheating</u>]({{ "/2025/09/25/sep-25-quarterly-opex.html#cheaters-cheat" | relative_url }}){: .page-link target="_blank"}:

> In our tech-enabled, newly A.I.-powered world, students were increasingly fudging just about everything. They would embezzle dorm funds to spend on their friends and lie about having Covid to get the UberEats credits that the school offered to those in quarantine. ...
>
> One could get ahead, quickly, by cutting corners, by focusing on self-presentation. ...
>
> Why put all your energy into being a student when it seems like everyone around you is getting rich? One time during sophomore year, I was working on homework in my dorm common room with an acquaintance when she offhandedly remarked, “I bought a house in Las Vegas last week.” She continued, “It’s good for taxes.” It’s hard to put your earbuds in and get right back to your problem set when someone says something like that.

Firstly, notice how this is being blamed on AI, which I think is a misattribution since the urges were always there, and even the examples given were pre-AI. AI just happens to be the biggest cash vortex in an accelerationist world flush with cash. Secondly, I think that anxiety about this is pointless; I am strictly of the view that 1) if AI takes off before strong alignment then we are cooked anyways, 2) if AI takes off after strong alignment then we are likely in a world that is not technofeudalist (this will be covered more in the next opex post), and 3) if AI never fully takes off then we will forever be in a world filled with cash and grift, and in such a world there is no shortage of opportunity.

Lastly, there could be plenty of misalignment just from [<u>choosing the wrong things to align to</u>](https://backofmind.substack.com/p/everything-is-a-nail-or-at-least){: .page-link target="_blank"}. In fact, whether or not there is a right way to optimize for things in general is debatable: "just good enough" is often a useful heuristic in human decision-making for tradeoffs, and if we boil everything down to data we could <i>possibly</i> have an answer wrt a context-amenable metric like maximin utility (assuming the agent performing the optimization is able to come up with such a metric), but how are we going to boil everything down to data without an aligned AGI, which we would have made after having solved this alignment problem in the first place?

### Music

> If you wanted to really find the good stuff you had to either be an insufferable RYM user or have some kind of really complicated AI recommendation system.

Last time I made the whole music bot thing to figure out some good recs for myself and promptly stopped using it after I finally wrangled it into a working build. Well this time I decided to one-up myself and starting using RYM to be even more insufferable. After a month or two on the platform:

1. I've come across more music than I would have otherwise, but ...
2. The effect is quite marginal because their recommendation system is honestly not that great.
3. There are some absolute banger reviews on RYM. I mean just look at [<u>this review of Zimerman playing Chopin</u>](https://rateyourmusic.com/release/album/krystian-zimerman/4-balladen-barcarolle-fantasie/){: .page-link target="_blank"}:

> this is <i>the</i> recording of chopin's ballades. one so utterly exceptional it makes all others seem downright ordinary. i say this especially about the last three; i have heard some other recordings of the first which manage to carve their own path in a way that actually sometimes eclipses this recording, but this is not even near to the case with the other three.
>
> the first ballade, which imo is clearly the weakest of the four, seems to just fly from the first moment of the performance. the steady build from the introduction to the first climax in g minor is effectively perfect, the reentry of the first theme in the tonic is haunting, and even the third theme is breathed so much life and energy into, but of course it is impossible to mention the first ballade without speaking of the entry of the second theme in A major, which of course is as brilliant as ever in this recording. this is also one of the recordings where i've felt the energy of the coda in a way where it lives up to the codas of the other ballades, which is a pretty amazing feat given how weak this one is in comparison. ...
>
> this is the first, and so far the only, recording of the fourth ballade where the coda is both understood and played so well that chopin's intentions shine through. this is the single recording that is responsible for the fourth ballade being my favorite piece of all time. and upon listening to the coda, it's immediately apparent why. i can't do justice to this thing in words, partially because there is simply so much going musically, so i will not, but it's something that's impossible to miss. there is the fourth ballade, and then there is the fourth ballade played by zimerman, and it is a world of difference.
>
> i cannot give this anything other than five stars. this recording itself is a miracle of human accomplishment.

And then this other review of the same recording:

> chopin wrote the barcarolle three years before he died. and it would be easy for me to tell you that "it's like he knew he was going to die" given the wistful feeling of the piece. but chopin's always wistful. it's what we know him for. and i can't talk about this piece and chopin, i won't be able to talk about it properly since i'm not chopin. even if i were chopin, why would i try to explain it with my words if i feel as if the piece i wrote fully explains what i was going through? i think that's where i fall. why write about something you're deeply connected to only to write about the dude you made it. who cares how and why he made it, he made the thing, he's already showing you how he feels. tell me about how it makes you feel. you're the one writing. you're the one reacting to the thing. don't tell me anything about the guy unless you relate the guy to yourself.
>
> now i'll do just that; i'll tell you how chopin's barcarolle came in at a very appropriate and proper time. i could argue that i'm doing it right now. i could say that i'm writing about how it made me think about these things. and i want to tell myself that it's proper and valid, but i can't say that without coming across as self-worshipping. but alas.
>
> chopin and i go way back. when i started figuring out what yearning was, he was there. when i cried to music for the first time, he was there. when i think about details i take for granted but are really significant in the grand scheme of things, he would be there in the background. when i think about words i choose in regards to how i come across, he would be there. chopin, though indirectly most of the time, would be the guy that rows the boat. he's one of the reasons why i tend to favor dissonance with lush qualities. he's one of the reasons i like the piano's sound more than the guitar, even though the guitar's my primary instrument of choice. he's one of the reasons i grew my hair out. he's one of the reasons i wanted to play piano in the first place. he's one of the guys that fortified my love for classical music through exposure to one of his nocturnes. he's one of the reasons why i tend to like nights more than mornings, though i've learned to appreciate mornings with his accompaniment. he's one of the reasons i wanted to write music of my own, making me download musescore, but not knowing enough about composition to actually write something properly. i wish i could afford myself music theory lessons, there was absolutely something there. imagine where i could be right now. chopin had these tendencies as well, but ever he knew that they weren't good for anyone.

It's very eye opening to read how other people connect to music! Here's a third review on the exact same recording:

> This is my first time attempting to review classical music.
I'm so not good at this that I don't even know if that's the right word for this.
>
> Every song started off like "eh this isn't that special" but evolved into "damn this is some fuckin piano"
>
> I'm seriously struggling to write things here. I mean, Barcarolle in F Sharp Major Op 60 fucking slaps. But I know that's not how people talk about this kind of music. And I don't know what a Baracarolle is. Or why it's Op 60.
>
> Anyway, this was nice. I liked the bits where the piano was going fast. :)

Guys, this is the point of music.

After I made an account on RYM I was forced to rate some albums in order to seed its recommendation system. In the process of doing so, I tried to be as accurate as I could, and so I ended up rating a whole lot of albums all at once, and because of that I realized that a bunch of albums I wanted to rate weren't actually in my frequent rotation and so I had to listen to every single album I wanted to rate again from start to finish. This then made me think about making a list of all the songs that I really liked, because I was trying to properly normalize what justified an album being 5/5, and that came down to two criteria: the average score I'd give to each track had to be at least 4.5, and there has to be at least one standout track that I'd give higher than 5/5. This means that even some of my favorite albums of all time wouldn't fall under this category, for example <i>Depression Cherry</i>, just because I don't like one of the tracks. Consequently I ended up thinking of all the tracks I'd ever give a 5.5/5 or more, and that turned out to be another fairly complicated exercise, but in the end I concluded that Radiohead's <i>Black Star</i> was my #1 track of all time, followed by <i>Superstar</i> (Beach House) and <i>大石碎胸口</i> (万能青年旅店).

For all I complain about RYM users hating music, on average my ratings are actually lower than consensus, and there are some albums where I'm wildly off consensus (mostly to the downside), eg. <i>In The Aeroplane Over the Sea</i>, <i>Revengeseekerz</i>, <i>Left Hand Path</i>, <i>Getting Killed</i> (I think these suck) and <i>Camp</i> (I think this is super unfairly underrated). In general, the demographic of RYM users favors some genres and styles more than others and I don't take the ratings into account seriously, but this perhaps has a negative impact on the quality of recommendations that their system outputs, and that is a very grave offense in my eyes.

A few other unrelated thoughts:

1. I don't understand the hype around Jane Remover, and I don't even think it's because it's not my cup of tea, it's more like the quality of their work is highly questionable. Without knowing that it was a serious attempt at artistic expression, I would have thought someone was just randomly mashing sounds and samples together then adding a bunch of distortion on top (I have very similar problems with supposed "underground rap", like osamason and nettspend). I was always a bit skeptical of hyperpop and internet dancepop as a genre, but I've come to discover some very good albums like <i>I Love My Computer</i> and <i>WOR\$T GIRL IN AMERICA</i> that to me are clearly on a different level of artistry than whatever else I've heard from soundcloud-adjacent artists; most of what comes out of this space sounds like shit.
2. I also don't understand RYM's obsession with Cameron Winter and Geese, I think the music is absurdly mediocre at best, and the lyrics are nowhere as good as people make them out to be. I don't wanna hear anybody compare him to Geordie Greep. One commonality I notice between bands / artists I strongly dislike is that on top of everything else they do, they tend to have a vocalist with an unbearable voice. Example: BCNR (there are some tracks where it works superbly, but entire albums of whining and moaning are unenjoyable), NMH, and Geese.
3. King Crimson has a formula to their albums and once you hear it, you can't unhear it because they use it in every single album. It's always: some rock thing, quiet ballad, wheedly guitar post-rock thing, then an assortment of random noises and bullshit, with some freedom to choose in the next few tracks, and it's ALWAYS in this exact order.

Let's look at my favorite tracks and albums from this quarter:

Songs / Pieces:

- Cadence and Cascade, Starless, Epitaph by King Crimson
- Piano Sonata No. 32 in C Minor, Op. 111: I. Maestoso Allegro con brio ed appassionato by Beethoven
- ฟังดูง่ายง่าย by Silly Fools
- Falling from Cloud 9 by Lift to Experience
- BEAT UP CHANEL\$ by Slayyyter
- Good Morning, Captain by Slint
- Spieluhr by Rammstein
- Sleep by GY!BE
- Man Next Door by Massive Attack
- Ipod Touch and Delete by Ninajirachi
- Breathe by The Prodigy
- Wisteria by Tokyo Shoegazer
- I Know It's Over by Jeff Buckley (cover of The Smiths)
- Luv(sic) by Nujabes
- Heathen by Deafheaven
- Gilded Runner by HOYO-MiX

I included the last one, which I didn't actually listen to that much, because I got nerdsniped by the fact that its main motif is grouped by Fibonacci sequence size.

Albums:

- Remains by Tokyo Shoegazer (new album, solid but not as good as their past few imo)
- Spiderland by Slint
- I Love My Computer by Ninajirachi
- Caminhos de &Aacute;gua by Kaatayra
- Heaven or Las Vegas by Cocteau Twins (relistened to this a lot because I found a website that had some surprisingly good guesses of the "actual" lyrics)
- D&uuml;nya Yalan S&ouml;yl&uuml;yor by mor ve &ouml;tesi
- WOR\$T GIRL IN AMERICA by Slayyyter
- Let My Children Hear Music by Charles Mingus (very un-Minguslike record)
- For&ccedil;a Bruta by Jorge Ben Jor
- The Texas-Jerusalem Crossroads by Lift to Experience
- Red and In The Court Of The Crimson King by King Crimson

For&ccedil;a Bruta was very good, but I also listened to the other supposed standard-bearer of MPB, <i>Clube da esquina</i>, and didn't find it nearly as memorable.

I also listened to Glenn Gould playing the Well-Tempered Clavier during my exam season, and instead of getting calmed down I couldn't stop noticing how he would randomly start vocally stimming during the performance. But it was a brilliantly flexible yet composed rendition of a brilliant suite of compositions, a key to interpreting Bach that I never managed when I was learning the piano.

The Big Beautiful Playlist is now 211 tracks long compared to 204 last quarter, but still no V, X, or Z!

## Finance

### QVR

This came as a big shock to me, but QVR Advisors closed / "blew up" in May after losing 30% from January to April from bad bets and redemptions. Benn Eifert is one of the biggest vol manager accounts on twitter and he was always willing to share his knowledge with people, so it was very unprecedented that someone who ran his book with this level of sophistication would one day blow up in the most ignominious manner: as a long volatility shop during one of the highest realized vol runs on record.

Some information from the grapevine:

> "Wow, some real die the hero or live long enough to become the villain stuff. There was some conf in Oct where I asked Benn what he thought about how crowded dispersion was getting and he said they had flipped to buying corr, which was probably painful into Jan and Feb..."

> "[I]f you were in a 5-10% drawdown and as a result 80% of your investors asked for their money back right away within a single month and you had modeled 50% redeeming in a month as a 3SD event or whatever given history…and then you are having to try and get out of positions with counterparties that know you are bleeding out…Is it clear that your risk process was bad?  Obviously the outcome of the bet went against you. A lot of the negativity from the cheap seats seems to be focused on him having totally screwed it up."

I believe I saw this on an episode of Odds on Open: someone had opined that it's never a bad strategy that kills a PM, but rather bad portfolio construction. It seems here that overly optimistic risk estimates [<u>ultimately did them in</u>](https://x.com/bennpeifert/status/2058214546905674170){: .page-link target="_blank"}:

> Nearly all of these sub-strategies and positions are ones where, if you experience losses, typically the positions are getting more attractive, and from a portfolio management perspective you want to (cautiously, prudently) add more risk. Which we did.
>
> The idea of mechanical stop-losses and cutting risk during drawdowns is sensible in some strategies; it is applied heavily by pod shops for this reason; but is generally inappropriate in a diversified, risk-managed derivatives strategy based on dislocations.
>
> No one month was that bad, no one trade experienced some major blowup, but four months of down 7-9% in a row, even in an 18-vol target strategy, is too much for investors to reasonably handle. Our investors were great through this process. ...
>
> ... I'd say the most important one is simple and obvious... I should have taken more seriously the shift in realized correlation across our strategies. I of course saw this was happening, and attributed it to the correct factors, but saw the rising expected return from dislocations and actively chose to hold and increase positions that we believed in, waiting for the reversion that would take us from down 15-20% on the year to up 20% and make us look like geniuses.... obviously did not turn out to be the right thing. So this was a risk management failing, but a much more nuanced one than just having a stupidly risky trade on and blowing up -- it was about how to manage a long difficult path of losses where those losses make your positions look more attractive.

I wonder how many people in his position would have made the choice to cut positions. It's easy to conclude ex post that the right move was to lower conviction, but in the midst of the action, with no indication of whether the observed dislocations were likely to persist, and with positions that looked like they had fair justification with enough convexity to ensure they wouldn't be completely blown up, it would be an extremely difficult call to cut sizing. If the strats indeed rebounded to new highs there would have been no shortage of grumbling from the allocators as well.

The big takeaway from this incident, I think, is to be aware of the size of a combined set of strategies designed to negatively correlate; even if they realize returns contrary to what is implied by the models and the data, I don't think that they should be drawing down nearly 10% month after month.

### SK Hynix

Long ago when I first heard about "dealer gamma", it felt like some voodoo art that had suddenly unlocked an inside view of market mechanics (dealers having to forcibly rebalance their delta exposures due to gamma, vanna, charm, etc). I was very into this stuff for a while until gradually I came around to understanding that public dealer profiles weren't indicative of overall dealer greeks exposure, and moreso that dealers could lean their deltas, or hedge against other option holdings, so on. The people pushing GEX and 0dte dealer hedging flow maps had good explanations of market behavior, but more often than not the impact of such hedging was greatly overexaggerated because they wanted to sell their product.

This didn't mean that the underlying principles of options-based hedging flows weren't present, and in some cases the combined effect of leverage and options greeks created destabilizing setups that had very visible market footprints.

The perfect example of this is SK Hynix. I hardly have to describe how desperate the scramble for memory exposure is, both among pods and among retail gamblers. Just a few examples of the money-warping capabilities of the SK Hynix black hole:

1. It made up [<u>25% of KOSPI</u>](https://x.com/GlobalMktObserv/status/2060325845898530921){: .page-link target="_blank"}, with Samsung taking another 27%
2. People are [<u>surrendering life insurance policies</u>](https://x.com/normal_2610/status/2056423418824929761?s=46){: .page-link target="_blank"} to buy SK Hynix on leverage, and many of them are from older generations and [<u>have never owned brokerage accounts before</u>](https://www.koreatimes.co.kr/amp/economy/20260517/brokerages-hit-jackpot-as-retail-investors-borrow-more-to-chase-koreas-stock-rally){: .page-link target="_blank"}
3. (Sneak peek forward to July) Not only are the Korean and Hong Kong markets wrapped up in this frenzy, Americans trying to get exposure to it have [<u>driven the price of the ADR</u>](https://x.com/degentradingLSD/status/2075659099338076413){: .page-link target="_blank"} way above its price in the Korean market due to the difficulty of exchanging the shares on the Korean exchange for ADRs in the American market to arb this premium

Yes there might be perfectly good engineering reasons for why SK Hynix should be worth even more multiples of its current valuation, but whether those are the primary drivers of this massive parabolic run is debatable. Here's an alternative perspective: a large part of the daily volume of underlyings with large leveraged ETFs benchmarked to them is currently driven by rebalancing requirements. For example, a 5% move in SOXX would require [<u>SOXL to buy or sell \$10B in exposure</u>](https://x.com/Alpha_Ex_LLC/status/2067656852637106385){: .page-link target="_blank"} through various swaps and derivatives. In comparison, the average daily volume of SOXX is in the order of \$5B. This setup is mechanically the same as stuffing dealers with short gamma, because they need to add deltas as the underlying moves up and vice versa.[4](#fn-4){: #ref-4 .page-link .footnote}

Similar leveraged stories are playing out across the chip and memory complex, but the SK Hynix story is unique in just exactly how much leverage is being demanded by traders. The leveraged fund at the center of it all is 7709.HK, whose their AUM has grown to the extent that the original counterparties to their leveraged swaps had to [<u>stop extending them more leverage</u>](https://x.com/Alpha_Ex_LLC/status/2060735674811121720){: .page-link target="_blank"}. Therefore, in order to maintain the same exposure in the face of the ballooning AUM triggered by the wealth effect of chip stocks melting up, the ETF issuer had to start buying exposure through the options market. 7709 is run by a joint venture under China Southern Asset Management, and they are decidedly [<u>not the most sophisticated player in the options market here</u>](https://x.com/Alpha_Ex_LLC/status/2072652611971346524){: .page-link target="_blank"}, but with their mandate and the unfathomably large demand for access to SK Hynix they didn't have much choice.

<div align="center">
    <img src="/assets/images/jun26opex/skhynix.png" style="height: auto;">
</div>

With how many 90 delta calls the ETF issuer has had to buy, two observations become clear: firstly, that the issuer is bleeding out massively in terms of spreads, especially since now their counterparties are aware that they have this massive forced flow at defined times, and secondly, this creates a potential downside accelerant and also very odd requirements to rebalance based on higher order greeks (for CSOP), because their option trades are often only a week or so to expiry (so charm would mean dealers need to sell to delta hedge, but would also mean that CSOP needs to rebalance wrt their new delta each day).

It's hard to imagine that the unbridled exuberance that's rolled across multiple asset classes this year could have existed in a world without these large mechanical causes of localized dislocation, be it leveraged ETFs here, or passive allocators in other cases. You would think that this makes trading against these forced flows easier, but in almost all cases the option market is a step ahead; for example, if you wanted to bet on a sharp unwind in SK Hynix, you would either have to buy puts at a very high vol and eat a huge loss on vega once the underlying came back down, or short the calls (why would you ever want to do that in a meltup situation).

### Who defines fairness on Polymarket

[<u>I've talked before</u>]({{ "/2026/04/07/mar-26-quarterly-opex.html#other-finbro-things" | relative_url }}){: .page-link target="_blank"} about how Polymarket's business model is fundamentally broken, primarily because it attempts to exist in a superposition between an accurate representation of liquid, informed market consensus, while at the same time wants to increase volume on its own site, which surely can't happen if everyone is equally rational and informed because then the no-trade theorem would hold, and therefore it has to balance between allowing people to see themselves getting adverse-selected against HARD in real time in the former vs having less institutional adoption in the latter. [<u>From Onyx cofounder Greg Newman</u>](https://moontower.substack.com/p/slam-da-duh-duh){: .page-link target="_blank"}:

> To begin with, [Polymarket] was great. There really was nothing like it. ... Then what started happening, unfortunately, is it got more and more popular, and we started to realize the way it settles is just not ideal. Even with that Strait example, some people felt it had technically closed — ships slowed down for a time. How do you define “closed”? The settlement matters. It’s funny, because in our market in particular, with so many of these contracts, the big thing is to let contracts expire — which is actually quite unusual. A lot of us take these contracts to expiry. You might hold things against it, but expiry is incredibly important — how the contract expires and to what methodology. So we’re very used to studying these underlying methodologies, and that’s where relative-value opportunities — maybe not arbitrage, but relative value — can become very important. So when we studied that from a Polymarket perspective, we lost confidence very quickly in what the game was all about. You have to own the tokens — you have to own a big portion of it — to be able to decide. So who decides is as important as anything else. And then — I’m not even saying it’s rigged — it’s just inefficient. So to use it as a reliable source of information, it kind of lost its gravitas quite quickly. So then we stopped looking at it.

Now there is also another argument for why Polymarket is bad, because it is too easy to hijack the outcome of a vote (well it's not easy, but for the severity of the issue there have been far too many instances of this happening), and the company has shown its unwillingness to do anything about it (perhaps to preserve the pretense of decentralization, which allows them to deflect liability in contentious cases). But even then, sometimes their own resolution rules are purely nonsensical, as the debacle below would show. If they're trying to make their decentralized oracle the standard of contract resolution in prediction markets, it seems self-contradictory to then give themselves sweeping powers in defining outcomes.

Recently what happened was someone full ported YES contracts on "Will MSTR sell Bitcoin by May 31st", they do sell by 31st, but because the announcement only comes after May 31st, the contract ends up resolving to no. The contract itself did not resolve until after the release of Microstrategy's 8K filings, which only happened the day after the resolution of the contract, so at the point when the 8K was released, the YES contracts were trading at 80c. Thinking it was a free arbitrage, [<u>this guy</u>](https://x.com/willo2_poly/status/2061640812132516321?s=46){: .page-link target="_blank"} went all in and then lost it all when Polymarket ruled in favor of NO.

His explanation covers basically everything, but there is a strong argument against him: that [<u>by precedent</u>](https://x.com/rb_tweets/status/2061906811930935371?s=46){: .page-link target="_blank"}, information released after the cutoff time of the contract is not considered eligible to be factored into the consideration of the bet. This is why the contract was trading at 80c after the information was released, which some people claimed to be another argument against the YES holders, but that's obviously a stupid take (it should only make you rethink the assumptions of why the market hasn't converged to 1 yet, but it's not a reason to say YES itself is wrong!) Obviously this is a stupid precedent. More importantly, these kinds of "does it matter, does it not" situations with precedents are precisely why large institutions like Onyx find Polymarket to be a poor source of information and a poorly defined market in general. I don't think there exist incremental fixes that would smooth over the inherent contradiction between decentralization and reproducibility in the UMA settlement system. I suppose there's some validity to the name "optimistic oracle" when their reasoning for why their [<u>fallback dispute resolution</u>](https://docs.uma.xyz/protocol-overview/how-does-umas-oracle-work){: .page-link target="_blank"} system can't be hijacked is:

> Unstaking UMA requires waiting a one-week period before the tokens are released. If the DVM were successfully corrupted by 65% of stake voting against reality, the UMA token would depreciate significantly in the following week, resulting in a loss for the attackers. This creates a cost of corruption that disincentivizes corrupting the oracle.

Well-posedness of the resolution criteria is paramount to a well-defined universe of prediction contracts, and the primary difficulty in implementing this is just the sheer number of edge cases you would have to think through for every possible prediction you could make. If in the future Polymarket could reduce the reliance of their oracle on corruptible voting systems and also just commit to either centralized arbitration or decentralized settlement instead of trying to do both, it could perhaps find more widespread institutional adoption. As it stands, I do not believe that the current state of prediction markets is poised for it to be anything other than a niche alternative asset.

### Safe Haven: a book review

I read Mark Spitznagel's <i>Safe Haven</i> on the flight back from the UK after my prelims ended (and over the following day). Some thoughts:

1. Essentially the entire book is saying that big losses are disproportionately impactful on the compounding path of a person/strategy's realized wealth and thus should be avoided. There's a whole bunch of philosophical babbling that I would not recommend taking too seriously (more on this later) and then a later portion about how to calculate whether a hedge is cost-effective, which was the only somewhat useful part: take the past returns of something and its selected hedge, then randomly simulate different orderings of annualized returns (with replacement). I'm not sure how much more epistemically sound this is compared to the other bootstrap methods he claimed to involve too much backwards-looking bias. I'm also not sure how this can eliminate the problem of regime changes that he claimed to be a big issue for some hedges that worked in the past and have stopped  working, since the data from past regimes would still be in the randomizer. Overall I felt like the book was just a 200-page exposition of the AM-GM inequality - adequate for a layperson, but I would have liked a more in-depth exploration of the strategies he looked at and discarded in the final chapter, and an exploration of the history of these strategies, why some worked at some times, and so on. But of course he has to keep the Universa secret sauce well guarded, so I don't blame him for not explaining any of this.
2. My biggest gripe with the book is that it's overly tailored to laymen. There's a lot of pseudoscientific and philosophical filler in the book that I honestly could have skipped because it did not contribute anything to my understanding of tail hedges. Like what about amor fati and the history of the Bernoulli family is relevant to our understanding of tail hedges? I'm sure there are people who would benefit from a discussion about delayed gratification and it certainly is relevant to the PNL curve of a tail-hedging shop, but seriously I'm reading this book to learn about how to tail hedge not about psychology or a watered down version of Karl Popper.
3. Another issue I have with it is what I can only describe as carelessness in applying statistical ideas. In the final part I was very confused by how the arithmetic and geometric means could now somehow be additively combined to determine the cost-effectiveness of a strategy, before I realized that it wasn't actually that serious and he was just making a point about how cost $<$ gain $\to$ \$\$\$. Then there's this whole bit on P133 that was just a big mess of (perhaps purposely) incorrectly applied confidence intervals. Yes it works as a rhetorical device to "show" laypeople what he means, but it offers very little insight in the mathematical sense.

The conventional wisdom is that buying tail options cannot possibly be +EV. I have long since accepted that this is not true, at least not in the traditional "Sharpe world" sense, as the guys at Convex Strategies like to point out (they seem to have very similar ideas as Spitznagel, including their views on central bank intervention). But this book's purpose, if it was to provide a justification of his investment methodology and philosophy, has not succeeded in convincing the average person that tail hedges are mathematically sound in practice, because all the examples that he gives of them working are fictional, whereas in the last chapter he systematically discredits every single common anti-correlated strategy. So what exactly was he trying to accomplish with this book? I am not sure, but maybe some large allocator or another would read this book and think, maybe I should go and ring up Universa and see how they deal with this. If that's the only logical purpose for this book existing then I must say I'm quite disappointed in retrospect for having spent a whole day reading one long-winded advertisement. 

### Other finbro things

Here's a collection of other rarities.

Recall the gambling society thesis, laid out [<u>here</u>]({{ "/2025/06/23/jun-25-quarterly-opex.html#gambling-society-i" | relative_url }}){: .page-link target="_blank"}, [<u>here</u>]({{ "/2025/06/23/jun-25-quarterly-opex.html#gambling-society-ii" | relative_url }}){: .page-link target="_blank"}, [<u>here</u>]({{ "/2025/09/25/sep-25-quarterly-opex.html#gambling-society-iii" | relative_url }}){: .page-link target="_blank"}, and [<u>here</u>]({{ "/2026/01/17/dec-25-quarterly-opex.html#gambling-society-iv" | relative_url }}){: .page-link target="_blank"}. A related idea is how volatility, in both its explicit form in markets and in its implicit forms in other parts of life, would be heavily bid now and into the future. If you have negative edge, the only way to win money is to [<u>not bleed out</u>](https://moontower.substack.com/p/how-to-get-arbed-with-perfect-information){: .page-link target="_blank"} from the law of large numbers:

> Doug Costa actually showed that happen in the toy example above. The investor who bought the 110 calls based on the real-world probability but then hedged by shorting the mispriced security actually assured themselves of a loss. If you have no edge, **variance is your friend**.

A [<u>"closed" form</u>](https://x.com/tleilax___/status/2049207719056609596?s=46){: .page-link target="_blank"} of Black Scholes implied IV has supposedly <i>just</i> been found. It is not exactly closed in the sense that you can plug numbers in and it would give the answer, because the inverse Gaussian still has to be solved for numerically.

Here's some more from [<u>moontower</u>](https://moontower.substack.com/p/hard-earned-trading-wisdom){: .page-link target="_blank"}, which is about an interview with Euan Sinclair:

> There’s a lot of people who’d be like, “Well, that’s not quantitative. That’s not systematic.” Well, first of all, who gives a shit what they say? You don’t get a medal for being quantitative. You make money or you don’t. Being quantitative is seen as this kind of goal, and it’s not the goal. It’s a tool toward the goal. ...
>
> Every time you make a portfolio or sizing decision, you are at some point applying that kind of thing. If you’re going to go through all the math, eventually you’re going to have a utility function, and that utility function is going to have a risk aversion parameter. So you’re going to go through all this math, and then at the end it’s going to say, “Oh by the way, what’s your risk aversion parameter?” You have to make that decision somewhere. I’m just doing it at the start. It’s much more of an exogenous thing that’s obvious. ...
>
> ... It’s one of those things where retail look at institutional and go, “Well, it’s all systematized. I have to do that.” But they don’t think of the reason we systematize things. It’s not to make the strategy better. Honestly, it probably makes it worse, because you’ve locked it in. You’ve said, “This is it, I’m not going to be learning anything more about that now.” But it definitely removes operational risk. It makes it cheaper to run, because you can just let it run on its own. You don’t need a person doing it all the time.
>
> People on the outside are making a judgment of how the things on the inside work, and they’re missing the point. ... If you’re in a situation where you have to automate the trades, you’re probably playing in a game where you’re not going to win as a retail trader. You shouldn’t be trading, “Oh, I have to run this through the API so I can trade 15 times a day.” That’s one of those quant-envy things where you’re like, “I’m going to do this the way Citadel would do it.” Again, you’re playing basketball one-on-one with LeBron. Good luck. Don’t care how tall you are.

Lastly, some concerning signs are brewing in how volatility and returns are realizing cross-sectionally in equities: [<u>momentum dispersion is breaking down</u>](https://x.com/pinkhasov/status/2070196327481237619?s=46){: .page-link target="_blank"} and [<u>RV in semis is dominating realized returns</u>](https://x.com/alpha_ex_llc/status/2070860944138174766?s=46){: .page-link target="_blank"}.

## Final thoughts

What can we truly know about what we know? Thinking back to the whole QVR episode, and also to the fake real Monet painting, to the inherent untestability of tail events, the one thing in common is that what we know to be true is not always true, and what we don't know to be true sometimes can't be known at all. If life is the act of making decisions, we must be the most unfortunate creatures of all to be given such awareness of our agency and yet having so little at our disposal to make epistemically justified decisions other than the educated guess. Heuristics are macroscopic behaviors we generalize from deterministic systems, or are averages and summary statistics we use in place of data we don't have, or in other words the crutches we use to hobble down this one realization of all the possible paths we could have realized in this world. Maybe the one thing we will have left, after the machines ingest enough data to outperform us at everything else, is the ability to throw caution away, and let "variance be your friend". Until that day comes, the best we can do is to hedge away catastrophic failures, so that we can be confident in taking more risk.

&nbsp;

[<u>Back to top</u>](#){: .page-link}

&nbsp;

---

<div id="fn-1"></div>

<small><sup>1</sup> This piece is not meant to be a debate about the merits and issues of NS, but I wanted to bring up this anecdote from a friend: "in my office during NS there was a regular whose main job was to update course results from an excel sheet into the HR database. actually, there was a way to almost fully automate the process by uploading an entire CSV file to the database (2 min process), but short of that you could copy+paste the results into the system (10 min). this woman did neither. she did not know how to copy and paste. so she printed out the excel sheet with the course results, opened the site on her desktop, and MANUALLY keyed in the results cell by cell. the worst thing is that we tried to teach her how to ctrl+C ctrl+V multiple times and she would be like oh wow that's so useful, and 1 month later she would be back to printing out her fucking excel sheets. here's the kicker: because manual entry of results took so long, she would spend HOURS on a task that could take 2 minutes (and indeed there was a nsf in my team whose job was to do the same thing in 2 minutes). so she would always stay in the office late to finish uploading results. her boss, the branch head, saw her stay back late every day and lauded her for being so hardworking." Let us consider that, anecdotally, this is not an isolated instance of ineptitude but rather a recurring trait across a nontrivial subset of regulars that I have had the fortune of encountering in my time as an admin signaler, albeit taken to the extreme. Let us also generalize the fact that this is not an isolated instance in a single organization, but that surely there are similar cases in many large and bureaucratic institutions, perhaps to a smaller extent, but regardless pernicious in their uncanny ability to avoid the proper checks of organizational feedback. I would have liked to turn this into a whole section but it seems a bit out of my scope of ability to comment on, except to remark that incentives matter, and designing properly aligned incentives is in no way an easy task (nor is it impossible). [↩](#ref-1){: .page-link}</small>

<div id="fn-2"></div>

<small><sup>2</sup> I read an introductory book to linear algebra, and introductory book to abstract algebra, and an introductory group to topology, then promptly forgot all the useful details when I entered university and actually had to do the first two for my exams. Thinking back it was probably an issue with the amount of rigor I held myself to in going through exercises, but even then it is quite surprising that the amount of content we covered in 2 terms of linalg was a strict subset of what was covered in the book, and same for groups. I distinctly remember one day some time in early 2024 when it was raining so hard that the sky was black at 3pm, and I had to myself an entire empty unused bunk for the afternoon, because I didn't want to disturb my sleeping bunkmates, and I was listening to Glitter by pasteboard thinking that once I got to Oxford I'd forever be playing that album on rainy days when I wanted to study. It's a bit unfortunate that I no longer think it's one of the best albums I've ever heard. [↩](#ref-2){: .page-link}</small>

<div id="fn-3"></div>

<small><sup>3</sup> Another passage from the same piece, even more irrelevant to the point that I was making but interesting nonetheless:</small>

> <small>Our illiterate future is unlikely to be peaceful. But political and ideological conflict is already waning, being replaced with something much more intimate. In every developed country, the last few decades have seen a massive political polarization among gender lines. Young women are swinging hard to the left; young men are swinging even harder to the right. A lot of people still seem to think that this is because we disagree more about politics than ever before, but actually it’s the opposite. Politics is losing its content; being on the left has come to mean being a girl, and being on the right is just another way of saying being a boy. Teenage boys watch esoteric Nazi edits for the same reason they used to pull girls’ hair; as a way of working through the ambivalence of the heterosexual relation. Right-wing economic policy is now framed as a way of punishing women, reducing their social status until they’re willing to turn back the clock on liberation. In some parts of the left, anything can be justified as long as it seems to reduce the power of men. When we can no longer conceive of a political whole, this is what will be left: all struggles will be powered by outright sexual sadism.</small>

<small>[↩](#ref-3){: .page-link}</small>

<div id="fn-4"></div>

<small><sup>4</sup> The opposite is true for ETFs with less than 1x leverage. If you recall the volmageddon debacle from 2018, you would see that shortly (3 weeks) afterwards SVXY changed its leverage from -1x to -0.5x. [↩](#ref-4){: .page-link}</small>
---
layout: post
title: "99% Luck 1% Effort - Dec 25 Quarterly Opex"
date: 2026-01-17
tags: [quarterly-opex, 2025]
excerpt: Oct-Dec 25 wrap
---

# Introduction

This edition of the quarterly opex came a bit late, partly because I was traveling and wanted to include a full account of everything that happened during my travels, and also partly because I was revising for collections at the same time. I started writing this in Sofia, and finished writing this in Oxford after my collections; prior to this I had departed from Oxford for London, stayed in Paris for a few days, went skiing in the French Alps, crashed a friend's house in Menton for a week, then I flew to Bucharest on Christmas and trundled my way down south to Sofia and finally to Athens. I talk about my observations in detail below.

At the end of the [<u>previous post</u>]({{ "/2025/09/25/sep-25-quarterly-opex.html#final-thoughts" | relative_url }}){: .page-link target="_blank"} I wrote:
> "I hope that the next 3 months will not completely overwhelm me to the extent that I wouldn’t have time to write ..."

This basically turned out to be true. I have never had a time in my life (other than perhaps the first two months of army) where I could wake up and spell out exactly what I had to do at every minute during the day because there were so many things (compulsory or not) that I had gotten myself involved in, and because I believe that when you set yourself something to do like a problem sheet or some sort of recurring commitment like going to the gym, there is no such thing as "I am too busy with other things and therefore I can postpone this to the following week"; there is a divine unquestionable quota of everything to be done within a week, regardless of whether anyone is chasing you to do them, and this can outweigh other things that might be more important in reality because the disquietude that comes with not having completed the work assigned to you by the universe is far worse than not meeting man-made deadlines. All this is to say that I have managed my time somewhat suboptimally in Michaelmas, and that I plan to improve upon this failure by further eschewing a strict timetable (the worst form of masochism) and to embrace the formless freedom and the neuroticism of being led around by whatever seems the most urgent in the moment.

It reminds me of when I was in the robotics club back when I was in grade 7/8 and the teachers kept trying to teach us about some extremely complicated shit called PID when we didn't have the requisite understanding of the motivation or rationale behind the approach. I bring this up not because of their teaching methods, but because even though I slept through most of the lectures I still ended up roughly remembering what PID was because of how many times they had to repeat it ... in the same way that the PID algorithm can "anticipate" future corrective actions in the derivative term, I like to rationalize "unscheduled timetabling" as the reaction to the derivative of some function that weighs the importance of what I have to do in a particular instant, instead of a carefully hardcoded "best path" that would inevitably be derailed by successive self-amplifying unpredictabilities along the way. While I have the utmost respect for the people who adhere to this form of self-torture, such as some of my friends in E&M, I doubt if I would ever find myself in a situation that warrants making myself a strict timetable, much less apply this way of living to my daily business.

Another problem is that there is a time for working and there is a time for doing fun things with your friends, and scheduling squeezes out the latter from life because having fun is often spontaneous and unstructurable. At the end of my university years, and in fact even now, I will remember nothing from the days when my time was occupied from the moment I woke up to the moment I went back to sleep, but remember everything from the random gatherings and events with friends. I consider having these moments a necessary part of my divinely ordained schedule and therefore I have been, by my own definition, very busy during term time.

On an unrelated note, something I want to do in my opex notes from now on is to have a theme. The [<u>first opex post</u>]({{ "/2025/06/23/jun-25-quarterly-opex.html" | relative_url }}){: .page-link target="_blank"} had the theme of the <i>gambling society</i>, and the second did not have much of theme at all. As you can see from the title, this quarter's theme is going to be about assigning happenstance its fair share of credit in determining how events play out.

## Content links
- [Math](#math){: .page-link}
- [Random thoughts](#random-thoughts){: .page-link}
    - [On university life](#on-university-life){: .page-link}
    - [Chaotic outcomes](#chaotic-outcomes){: .page-link}
    - [Walking the world (winter 2025 edition)](#walking-the-world-winter-2025-edition){: .page-link}
    - [Other interesting things](#other-interesting-things){: .page-link}
    - [Music](#music){: .page-link}
- [Finance](#finance){: .page-link}
    - [Gambling society IV](#gambling-society-iv){: .page-link}
    - [Doing math does not excuse you from thinking](#doing-math-does-not-excuse-you-from-thinking){: .page-link}
    - [Polymarket Jesus II](#polymarket-jesus-ii){: .page-link}
    - [Other finbro things](#other-finbro-things){: .page-link}
- [Final thoughts](#final-thoughts){: .page-link}

## Math

In this quarter, I have essentially had no time to do any math that was outside of my university syllabus. During the first two weeks I still had a bit of free time on the weekends to read my stochastic calculus book, but soon it became apparent that with 5 problem sheets a week, one of which was essentially two problem sheets in one (analysis had as many optional questions as compulsory ones), I had very little time to do the mindless math-scrolling that I used to do. I also figured that instead of trying to look so far ahead on a shaky footing, I would go back to all the basic things that I had learned once upon a time and make sure that I was really comfortable with the fundamentals of linalg, analysis, and so on, before I went and explored more complex topics that I would otherwise have just glanced the surface of.

That isn't to say that there weren't mathematically "interesting" things that I did this quarter. It is just unfortunate that many of these happen to be from geometry, the one topic that at least 95% of the cohort (including me) hates, because it is extremely dense and calculation-heavy. Out of my 5 subjects, the average time it takes for me to complete a problem sheet ranges from a few (<5) hours for calculus and probability, to 5-6 for linalg, to a day or more for analysis (since I do all the extension questions), and finally to the extremely skewed distribution of geometry problem sheets, the worst one of which (sheet 3 conics) took me 3 whole days to finish. I remember finishing that problem sheet then doing calculus, linalg, and probability in one sitting the following day and I told my friends:
> "life is genuinely sunshine and rainbows when ur not fucking doing geometry"

And yet all the interesting math moments I remember this term came from geometry. For example:

### Sheet 5, Q5

Let $\mathbf{e}_r = (\sin{\theta}\cos{\phi}, \sin{\theta}\sin{\phi}, \cos{\theta})$. Show that $\mathbf{\dot{e}}_r = \dot{\theta}\mathbf{e}_{\theta} + \dot{\phi}\sin{\theta}\,\mathbf{e}_{\phi}$ for some unit vectors $\mathbf{e}_{\theta}$, $\mathbf{e}_{\phi}$ to be determined, and find the angular velocity $\omega$ in terms of $\mathbf{e}_{r}, \mathbf{e}_{\theta}, \mathbf{e}_{\phi}$ such that $\mathbf{\dot{r}} = \omega \wedge \mathbf{e}_{r}, \mathbf{\dot{\theta}} = \omega \wedge \mathbf{e}_{\theta}, \mathbf{\dot{\phi}} = \omega \wedge \mathbf{e}_{\phi}$.

The first part is fairly standard: we get that

$$\begin{pmatrix}
\mathbf{\dot{e}}_r & \mathbf{\dot{e}}_{\theta} & \mathbf{\dot{e}}_{\phi}
\end{pmatrix} =
\begin{pmatrix}
\mathbf{e}_{r} & \mathbf{e}_{\theta} & \mathbf{e}_{\phi}
\end{pmatrix}
\begin{pmatrix}
0 & -\dot{\theta} & -\dot{\phi}\sin{\theta} \\
\dot{\theta}& 0 & -\dot{\phi}\cos{\theta} \\
\dot{\phi}\sin{\theta} & \dot{\phi}\cos{\theta} & 0
\end{pmatrix}$$

The problem is how to transform that right matrix into the $\omega$ form, and I'm not proud to admit that this took me around 4 hours and lots of AI to figure out, because changing bases is quite possibly the worst and most brain-melting topic in all of linear algebra. I was tripped up on the fact that for an antisymmetric matrix $M$, $M\mathbf{v} = \omega \wedge \mathbf{v}$ for some $\omega$, but the form that we currently have it in, where the basis of $(\mathbf{e}_{r}, \mathbf{e}_{\theta}, \mathbf{e}_{\phi})$ consists of 3 column vectors, does not allow us to use transposition tricks or anything to get it into a form where we could reduce the matrix to the cross product representation. It was only during the tutorial afterwards when my tutor explained to me that there was no need to go into such rigorous detail and that it was perfectly fine to just take $\mathbf{e}_{r}, ...$ as a bunch of "labels" instead of vectors themselves, and then we could just simply write:

$$\begin{pmatrix}
\mathbf{\dot{e}}_r \\ \mathbf{\dot{e}}_{\theta} \\ \mathbf{\dot{e}}_{\phi}
\end{pmatrix} =
M\begin{pmatrix}
\mathbf{e}_{r} \\ \mathbf{e}_{\theta} \\ \mathbf{e}_{\phi}
\end{pmatrix} = 
\omega \wedge \begin{pmatrix}
\mathbf{e}_{r} \\ \mathbf{e}_{\theta} \\ \mathbf{e}_{\phi}
\end{pmatrix}$$

Anyways this was what ChatGPT and I came up with after 4 very frustrating hours (I remember this took me until 3 AM to figure out and I was genuinely crashing out because I was so tired and ChatGPT was going around in circles and confusing itself and me 95% of the time, and I really wanted to give up but I also believed that it was my god-given task to finish Sheet 5 before I went to bed):

The primary confusion in this question is "what basis are we considering something in", and we can see that if we think of $(\mathbf{e}_{r}, \mathbf{e}_{\theta}, \mathbf{e}_{\phi})$ as an orthonormal basis represented wrt the canonical basis, then

$$M_{e} = \begin{pmatrix}
0 & -\dot{\theta} & -\dot{\phi}\sin{\theta} \\
\dot{\theta}& 0 & -\dot{\phi}\cos{\theta} \\
\dot{\phi}\sin{\theta} & \dot{\phi}\cos{\theta} & 0
\end{pmatrix}$$

is $\frac{dA}{dt}A^{T}$ represented wrt the $(\mathbf{e}_{r}, \mathbf{e}_{\theta}, \mathbf{e}_{\phi})$ basis, where $A(t)$ is the basis of the rotating frame at time $t$. Therefore for any $\mathbf{x}$ represented wrt the canonical basis, let $E = (\mathbf{e}_{r}, \mathbf{e}_{\theta}, \mathbf{e}_{\phi})$, and let $\mathbf{x}_e = E\mathbf{x}$. We also know from earlier that $\dot{E} = EM_e$. Then:

$$\begin{align*}
\mathbf{\dot{x}}_e = \dot{E}\mathbf{x} = EM_{e}\mathbf{x} = EM_{e}E^{-1}E\mathbf{x} = EM_{e}E^{T}\mathbf{x}_e 
\end{align*}$$

If we let $M = EM_{e}E^{T} \therefore \exists \omega, \omega \wedge \mathbf{x}_e = M\mathbf{x}_e$.

I'll skip on the working for the rest because it was just an algebraic expansion of $M$ using to solve for $\omega$. The point is, we had the goal of moving $E$ to the right of $M_{e}$, and due to the antisymmetric property of $M_{e}$, $M$ could be expanded in a form that then lets us use the vector triple product of two basis vectors and $\mathbf{x}$, and since $E$ was an orthonormal basis the cross product of two basis vectors was the third.

The confusing but neat part of this is understanding that when we talk about angular velocity as $\omega \wedge \mathbf{x}$, we need both vectors to be represented wrt the same basis. Here in the question, we are asked to find $\omega$ wrt the basis represented by $E$, and therefore when we consider $\mathbf{\dot{x}}$ we are considering a fixed point wrt the canonical basis that looks like it's changing wrt the rotational basis because the rotational basis itself is changing over time. So what $\mathbf{\dot{x}}_e = EM_{e}E^{T}\mathbf{x}_e$ is actually saying is that in order to find how the representation of $\mathbf{x}$ in $E$ evolves as a transformation applied to itself, first you need to fix the vector by sending it back to the canonical basis, before applying the "moving" part that comes from $E$.

(If all this sounds more like linear algebra than geometry, that is because prelims Michaelmas geometry is not a very well designed topic, since it's basically calculus, linear algebra, and a bunch of 2d and 3d conics cobbled together.)

### Hexagon $\iff$ double torus

The second "interesting" moment occurred after a tutorial. Our tutor told us that you could make a genus $n$ (hollow) torus by gluing together the sides of a polygonal sheet with $2n+2$ edges. For example, you can make a standard torus (genus 1) using a square like this:

<div align="center">
    <img src="/assets/images/dec25opex/torus.png" alt="Making a torus from a square" style="height: auto;">
</div>

After the tutorial, my friend and I decided to try it for a genus 2 torus, which by our tutor's remark was constructible from a hexagon. We tried for 2 hours, coming up with more and more delusional and deranged constructions, some of which involved looping through, under, and around the holes in the torus, but none of which actually turned out to be a hexagon. We also cut up and stapled a bunch of rubber gloves he had lying around, and then we borrowed our friend's blu tack, both of which ended up achieving nothing.

We were about to miss dinner when we finally gave up, and I checked google just to make sure it was possible, but apparently our tutor had gotten it wrong and you needed a $4n$-gon not a $2n+2$-gon.

<div align="center">
    <img src="/assets/images/dec25opex/doubletorus.jpg" alt="Making a double torus from an octagon" style="height: auto;">
</div>

At least we figured out how to make a M&ouml;bius strip-like object with [<u>2 twists</u>](https://math.stackexchange.com/questions/3379866/a-double-m%C3%B6bius-strip){: .page-link target="_blank"}. (Note: this object is homeomorphic but not isomorphic to the cylinder, unless you allow self-intersection, and then you can do the [<u>Dirac belt trick</u>](https://en.wikipedia.org/wiki/Plate_trick){: .page-link target="_blank"}.)

All in all, geometry was interesting sometimes and a huge chore most of the time, and when it was interesting it was by virtue of something <i>else</i> hidden within geometric ideas that was interesting and not because the way it was structured as a course was particularly interesting.

In other news, some interesting math-related pictures from my travels:

I visited the Institut Henri Poincar&eacute; where there were shelves of geometrical constructions, mostly manifolds in 3D, but it was interesting to see how they were able to make these things before the invention of modern graphing technology.

<div align="center">
    <img src="/assets/images/dec25opex/ihp.jpeg" alt="Geometrical constructions in the Institut Henri Poincare" style="max-width: 70%; height: auto;">
</div>

In Bulgaria I found a Soviet-era textbook on introductory mathematics, where they were still using ancient Greek methods of constructing polygons with a compass and straightedge.

<div align="center">
    <img src="/assets/images/dec25opex/russianbook.jpeg" alt="Geometrical constructions in the Institut Henri Poincare" style="max-width: 70%; height: auto;">
</div>

In Athens I found a translation of Aristarchus of Samos' <i>On the Sizes and Distances of the Sun and Moon</i> by Sir Thomas Heath, where there were plenty of extremely clever constructions and geometrical diagrams.

<div align="center">
    <img src="/assets/images/dec25opex/aristarchus.jpeg" alt="Geometrical constructions in the Institut Henri Poincare" style="max-width: 70%; height: auto;">
</div>

## Random thoughts

### On university life

The first term was long while I was in it, but now that I'm looking back on it from the things I've written it actually feels a lot shorter: events that I thought had taken place later actually took place way earlier, and things I thought I did a long time ago turned out to have happened at the end of the term. My theory for why this happens is because the chaotic eventfulness of starting university life, and having to handle so many things about settling into a new place and forming new routines, pads the recent memory with too many reference points, whereas from the rearview mirror only the most important things remain visible and all the dull administrative chores fade away.

For example, at the start of the term I was still struggling to figure out how I could reasonably cook within my dorm room without triggering the smoke alarm and at the same time how I could effectively and thoroughly wash my things after cooking, given that neither my chopping board nor my cooker could fit in the sink; it took me at least 5 or more tries to settle on something that I could cook over and over and not get tired of. It remains to be seen how much settling into a routine helps with reducing "chore time", but I would probably guess a reduction of around 10-20% of the total time spent on doing necessary things to survive comfortably.

Culturally, the UK is really not as strange as one would expect; the strangest thing we had to do was to toast the king during our formals (since the reigning monarch is the visitor of Christ Church), and I only went to one formal dinner because by my record it took me 17 minutes to put on my shirt, suit, and the layer of heattech underneath which I had to cover with a long-sleeved white tee as the fourth layer. I got better at putting on this ridiculous fit as the term progressed since I had to go to a bunch of events that required formal wear, but in addition to wasting this much time to dress up, formals also took at least an hour or more to finish, and that was just way too much time being wasted for food that was exactly the same as what would be served during the informal dinner sitting.

But on the topic of culture, the strangest aspect of living in Oxford was not British culture, which one could opt out of, but rather the culture of being a British student. I didn't know if this was true of all Singaporean students, but the impression that I had of the people I knew who studied back there was that they were on average studious individuals who spent the better part of their day studying and grinding for jobs. This wasn't to say that a similar culture was not present in Oxford, because it is absolutely rampant amongst the Singaporeans here, but when you talk to the other students you sometimes get the feeling that you are living in a different world: approximately 15% of my non-Singaporean friends from every single mathematically inclined STEM degree (Math, Math+CS, Math+Phil, CS, CS+Phil, Physics, Engineering) knew what a quant was, and exactly 1 of them was interested in it at all. Contrast this with the Singaporean society, where every single person knew what a quant was and roughly 0% of the people who weren't on a government scholarship were not actively applying to finance or consulting clubs and internships. Even the future doctors were applying to quant roles...

The British student, or perhaps the Western student as I have come to understand it, often has the remarkable ability to bend time. I was talking to a British friend about this, when I calculated that in order to cope with their copious amounts of partying and drinking nearly every single night AND to finish all their assigned work before tutorials, which I know 99%+ actually do, the average party-going student (which I concede is not everyone, but it is quite a large majority of people) would be left with 3-4 hours of sleep per night, or maximally 5 if they skipped lectures. And he told me:
> "Theyre doing that lmao"

I am horribly envious of these people who are somehow able to get away with 3-4 hours of sleep a night and still have the energy to do everything else in the day, given that shorter nights also mean longer days. I personally cannot function with less than 7.5 hours of sleep a day, which I have figured out is my absolute minimum, and even when I get 7.5 hours a day I usually need a half-hour siesta to bump my sleeping hours up to 8. I know friends back from high school who actually did this, sleeping less than 4 hours a day and taking mini-naps when they had time during the day, but for me I never had the luxury of choosing because I would fall asleep during the first lesson if I ever got less than 8 hours, whereas they could just choose to keep their eyes open, despite complaining of being how tired they were. This, I think, is an enviable superpower and people who have this ability are truly blessed if they have the willpower to use this time for work. Unfortunately, it appears to me that most people I know who are doing this are not using it for work.

On the topic of partying and drinking, both of these were things I tried and they are enjoyable when done with friends and in moderation. It's interesting to think about how the difference in attitudes towards things like going to the club or getting drunk evolved in the West and in Asia, where after adjusting for economic background it seems that the only explanation left is social and cultural. This is an unsatisfying conclusion for several reasons: 1. I dislike conclusions that rely on arguments like "Asian culture is more conservative" because what culture typically refers to here is the culture of the OLD Asia, the prewar, preindustrialized, premodern Asia, and by comparison the culture of the old West is hardly any different, and the only real difference comes from being in a different stage of the modernization brought about by capital, and 2. Clubbing culture is actually quite prevalent in specific areas of Asia, and its extent is quite uneven across areas with similar economic and social background: just compare Tokyo and Singapore for example, both very Westernized culturally (arguably Tokyo less so), both relatively rich, and yet by the most recently available data clubbing and nightlife is alive and well amongst Gen-Z individuals in Tokyo whereas in Singapore you get news reports like [<u>this</u>](https://www.straitstimes.com/life/a-waste-of-money-and-time-gen-z-and-millennials-are-over-traditional-nightlife){: .page-link target="_blank"}. Anecdotally, the Singaporeans that I know are even more reluctant to go clubbing than average.

There is another possibility, which I will talk more about in the next section, and it is that we are being fooled by randomness, and that there is a significant effect of entirely chaotic and random developments of the nightlife industry which were affected by the different initial conditions under which they developed unpredictably over time, much like how pearls in two different oysters could develop very differently for reasons that have nothing to do with a specific attribute of each individual oyster.

Lastly, I want to devote a paragraph to glaze Najar's Place, because it is my absolute favorite place to eat in Oxford. I just want to point out how much of an outlier it is in terms of pricing: for £4.50 you get a massive footlong wrap with salad, falafel, and heaps of chicken, and each wrap is enough to function as 70-100% of a meal, depending on how hungry you are. This is just completely inconsistent with the pricing of any other kebab cart or restaurant (after normalizing for the fact that you get a seat indoors). In fact, I would estimate that the cost of putting all that material inside, after applying a 20% reduction on their raw material prices compared to Sainsbury's, would be around 60-80p for the chicken, 10-20p for the salad, 10p for the falafel and 5p for the wrap, for a total of £1 on average, and then they need to put all kinds of seasoning on the chicken, and pay for the toaster, for utilities, probably rent for the spot that they set their store up in, and the labor cost of the 4-5 people who work there. The margins are genuinely so low it's ridiculous. At these prices and for these portions, they're basically donating to the students.

### Chaotic outcomes

I mentioned that two things evolving according to very similar rules or functions could have vastly different outcomes depending on initial conditions. This is a trivial observation that I think gets applied too little in our daily life. We know the examples of chaotic behavior where it can be visibly observed, like the Lorenz system, but where it matters the most we tend to overlook its effect, for example in noisy games (poker, trading), in the development of historical events, and in peoples' lives.

So when I say that the nightlife industry developed differently in Singapore versus some other places in the world due to chaotic things that we cannot predict, I mean it in the narrow sense of there being complex reasons behind the emergent trends in the industry at large, perhaps due to odd kinks in the market structure or specific policies or the urban layout around popular clubs or something entirely inexpressible that cannot be summed up in a research report, a consultant's pitch deck, or a government whitepaper. This isn't specific to nightlife, but to basically everything that happens, where the impact of any individual "reason" has a much higher variance then we tend to believe.

I like this quote from [<u>this article by a trader</u>](https://whirligigbear.substack.com/p/mostly-beta){: .page-link target="_blank"}:
> "... it is easy to over-attribute your actions on your results. I can only reflect on my own experiences, but even in what’s considered one of the most meritocratic, competitive, and individualistic roles anywhere, my own success was the product of a community more so than my own individual agency."

I think that in life outcomes are highly environment-dependent and path-dependent.
<ul>
<li>
Environment dependence means that much of what we do is a reflection of what people around us do instead of an active agentic choice (assuming that free will exists, else this discussion is meaningless anyways). It's like if we put a bunch of speakers and microphones next to each other and turned them on all at once. From the dawn of time the earliest humans received inputs from the external world, and turned these into outputs directed internally towards human society, and since then we have been echoing successive distortions of ideas and behaviors in our little social bubbles. This is especially interesting when viewed from the perspective of children, because it means that parents have much less impact over their children than they would like, and it explains why there is so much variation in the way people turn out behaviorally, even from relatively similar social and educational backgrounds, because the kids are learning from their 5 closest friends, and this is almost completely RANDOM. So yes, it is the case that richer kids tend to associate with a more educated, dignified, and refined milieu from young, but that is the AVERAGE case and there is so much variance to how kids make friends within school, and even for a rich kid you could end up in Harvard or you could end up as a bum, and the difference could be the result of things that nobody would think of like being put next to someone in school because your last names were next to each other alphabetically. An additional note for 2026: since brainrot has become the new tool for in-group association, it is a losing fight for parents to stop their kids from making 67 jokes, because the kids need to find some group to belong to and they need to express this sort of mimetic behavior to be accepted.
</li>
<li>
Path dependence means that what we do is drawn from a much smaller distribution than the universe of "possible moves" because we can only look at the family of events under the filtration of already-elapsed events. This is most understandable when applied to the topic of IQ. Perhaps everyone is born with a different level of neuroplasticity (or whatever I'm not a neurobiologist) which lets some recognize patterns or remember things better than others, but by point 1 this then evolves in a very chaotic way based on random inputs from the environment, and so some people end up with low realized IQ despite their high potential and vice versa for others. Likewise, very similar people who graduate at the same time could end up in very different places in their career 10 years down the road, and motivational speakers would often sell it to you as "working 1% harder 365 days a year" or "you have to position yourself for luck" but we know that's all bullshit. Most people who want to make it work pretty hard, but some of these people make it to senior middle manager at 50 and others end up as the CEO. One didn't work 1000x as hard as the other; he simply compounded more luck. Sometimes, you just need to get lucky in order to get even luckier, and getting lucky is not something YOU choose. If there was a PNL attributor for life, you will notice that the largest winners and losers have the highest attribution to luck: <b>hard work is low vol, good luck is the manifestation of a vol event.</b> In non-financebro terms, if you have a game where you have 1 minute to either do pushups or roll a 1000-faced die, and you are paid \\$1 for every pushup plus \\$1000 for every time you hit a 1 on the die, then out of everyone who plays the game the biggest winners will be the ones who rolled 1 on the die despite the average dice roll taking much longer than a pushup (if you are moderately competent at pushups), and yes you can practice as much as you want for the pushups but that won't create changes in the order of magnitude of your winnings.
</li>
</ul>

I find this to be a very liberating perspective to take, because respecting that there is so much randomness in our lives that we cannot be personally liable for gives us a better idea of what our limited agency can really be applied to. Instead of saddling yourself with self-loathing over things that are out of your control, or giving yourself credit for things that were mostly handed to you by your environment but happened to work out in your favor, it's better to possibly even underestimate our own agency when attributing our life outcomes to various causes so that we respect that the world is much larger than us, that the tides of society can sweep us away, and that the march of history can be chaotic and tempestuous.

Much like how practitioners often use fractional Kelly betting in real life instead of full Kelly, being accurate and slightly conservative about how much we think we can control in our lives is about maximizing our returns. It's walking the middle path between nihilism, where the outcome is hypergambling (see Gambling society IV below), and hubris, where the outcome is becoming a startupbro. Notice how both sides of the path fall prey to the temptations of going into life with more variance than is necessary. If you respect the forces of the market (life) and discount your edges without spiraling into unfounded doubt, then you wouldn't have to take outsized, risky bets to meet your return targets (nihilism), or take outsized, risky bets because you think your bulletproof analysis reduces your chances of ruin (hubris).

### Walking the world (winter 2025 edition)

I waited until January to finish writing this piece, and I earlier explained why; here I give a recap of the things I did and what I thought about the places that I've seen.

After Michaelmas ended we first went to London to chill for the weekend before going to our first proper stop. Even though we were only there for less than 2 days, I thought it would be nice to walk through London, the central bits of it at least, in the spirit of Chris Arnade, who unfortunately didn't end up coming to Oxford during his UK tour despite saying that he would. However he still had his reflections on the rest of England:
> I was also happily surprised, because while I adore England, efficiency isn’t its strong point. While it has all the bits and pieces necessary to be a highly functional country, it never quite pulls that off. Despite possessing a cultural legacy of competence and excellence, which gave us the modern age — one of individual liberty via a political compact forged over centuries of negotiation between their commoners, nobility, and royalty, and of material wealth via the Industrial Revolution — that cultural vitality faded long ago, enveloped by a fog of ignorance, incompetence, and incontinence, like an elderly professor whose mind and body are withering with age.
>
> It’s now in a state of dilapidated glory, which they accepted long ago, or at least acclimated to, a weathered dog-eared tatteredness of the dingy, dreary, and dysfunctional. A landscape of dense narrow roads crawling with workmen trying to halt the decay, and endless roundabouts (an attempt to smooth out the irregular oddly-angled intersections inherited from a less efficient past) punctuated with scenes of august grandeur—a majestic block of grand terraced houses in the midst of fluorescent-lit chip shops and kebab takeaways, or a Tudor manor (gated of course) within stone’s throw of bleak Council housing, as if someone wanted an illustrated lesson in the trade-offs of utilitarianism: Everyone gets a home, but few get dignity.

Being able to see these things is quite the gift, because without this observation as a mental anchor to guide me I had much less to ponder about when I walked through the following cities. London was, however, exactly as he described. It was visibly run-down and poorly maintained except for in a handful of places next to Regent's Park, or in Mayfair, or around their main tourist areas. From my friends at LSE I learned about the concept of the "London Banana", which was a curved zone in the center of London where Nice Things still existed, and outside of it was a barren moonscape of council housing plagued with crime and overrun by roadmen.

We lived in a small and probably illegally modified area on the side of a council housing block, where a washing machine blocked a door in the bedroom, beyond which another family lived. When they smoked pot, we could smell the fumes coming through the gap under the door. They were most likely Middle Eastern judging from their language, and basically everybody in the neighborhood seemed to be either of Middle Eastern or African heritage. The closest minimart was an Arabic store and the two eating spots beside it served Indian food.

People like to point out that large metropolitan cities tend to be multicultural, and while I don't disagree, London is visibly not multicultural, in the same way that [<u>Sydney</u>]({{ "/2025/09/25/sep-25-quarterly-opex.html#walking-the-world" | relative_url }}){: .page-link target="_blank"} is not multicultural. Multiculturalism means that you have genuine assimilation and mixture between cultures. In Sydney, as it as in London, there were highly disparate enclaves, formed along the coincident axes of immigrant status, class, and race. In the neighborhood we stayed in, you could see maybe 1 white person for every 100 people you passed. In Mayfair, more than 9 in 10 people were white.

These are obvious observations that many people have pointed out before, but when they do so it's typically to prove a point about policy or argue about the merits of immigration. Instead of doing that, which I am unqualified to do anyways, I want to frame it in relation to British culture and how the state of things in the UK have come to be like this, this once-great kingdom that has resigned grudgingly to its "weathered dog-eared tatteredness".

I started my walk in Fitzrovia, a relatively central locale, where there was trash all over the floor, the pavement was cracked and sometimes jutted out like a rock formation, and you could spot literal human shit on the ground. On the way I checked the prices of the restaurants I passed by: not a single one looked affordable to me, and probably not to the average person there either. Then I crossed through Regent's Garden, which was nice save for the fact that all the trees were bare (I assume it would have been nicer in the summer), and was also much better maintained - though, right on the footsteps of the row of elegant old multistory houses opposite the southeast entrance of the park I saw a homeless man lying, but probably not for long before he would have been chased out.

I then went south onto Baker Street, which slowly eased into a more lively part of town. After a short detour into Selfridges, where the entire first floor was devoted to perfumery and makeup, I made my way to Mayfair. It was a decidedly better-maintained part of town, full of grand old architecture and iron bars surrounding each block like a moat. There were guards / doormen standing next to most doors, from consulates to restaurants to private spaces, and while you could peer into the brightly-lit eateries and see the people having their high tea inside, you would be kindly and firmly turned away at the door by men in suits.

Yes, every city has its upscale neighborhoods, but Mayfair was unique because it was not meant to be a quiet, unostentatious part of town. The essence of aristocratic British culture was that it was observed; it was a Spectacle. Flaunting one's wealth too openly was the tasteless enjoyment of the nouveau riche, so the British aristocrats turned their wealth into a symbol of culture: the opulence of the monarchy and the intrigues of the royal family, the cakes and pastries at teatime, the crisp suits and coats, the walking stick, the RP accent. These are the first things that foreigners like me think of when we think of the UK and its cultural output, and it is hard to find something equally powerful on a cultural scale coming from the working class other than fish and chips, having a pint, and watching football.

For every other major culture I can name many things that have simultaneously originated from or were given a significant twist by the working class, and are also a staple of that place's modern cultural image. Oysters and escargots started as peasant food. Much of postwar Japanese culture has nothing to do with their royals any more, and functions as cheap sources of entertainment for the masses. In hanging on to their past grandeur the Brits have preserved the artifacts of their distinctly upper-class culture, where the entire cultural identity associated with their modern image is based on unspoken cultural codes meant to exclude.

I said back then:
> "the entire cultural identity here is based upon being inaccessible there is no other place in the world that impresses this upon u so well when u walk through it as london"

Since then I have only become more convinced of this thesis, after having walked through a bunch of other cities in Europe, and I think it is no longer premature to conclude that the UK is rather unique in having this issue. The working populace is disillusioned with the lack of a meaningful culture that they belong to. This gives rise to the conflicting responses of "we need to kick the immigrants out to preserve our existing culture", which achieves nothing because there still isn't anything there, and "we need to take in more immigrants to strengthen our multicultural fabric", which doesn't address the fact that there is always a tension between your identity and a culture that isn't really yours.

Anyways I walked through Mayfair, turned at Buckingham Palace, and walked through Westminster, past Big Ben, then tried to use the toilets at the Westminster station only to find that they weren't free, observed an entire homeless encampment in the aforementioned station, walked up to Trafalgar square, where a crowd was watching a pro-immigration modern reimagining of the birth of Jesus, then up to Covent Garden and Soho, before turning back towards Southwark to sneak into LSE Bankside again for free dinner.

I should also mention that none of the things I ate in London were British food. I had kebab, tacos, pizza, and Chinese steamed buns in that order. This is a convenient city for people who are accustomed to multiculturalism, but you can't always force everyone to identify with this way of living.

Next we were in Paris, which despite all the talk of it being a smelly shithole of a city that was overrun by criminals and asylum-seekers, turned out to be just as charming as I had remembered it to be from 10 years ago. I was told that they cleaned up their act for the Olympics and that it was much worse in the prior years, but regardless, it's been a year since the Olympics and the city still looked much cleaner than the rumors would have suggested. The only places that were noticeably dirty were the elevators in many MRT stops, which universally smelt like pee, and the graffiti that was sprayed everywhere, though I found that quite bearable and sometimes aesthetically pleasing as well.

There's much less that I can say about Paris, or any of the subsequent cities for that matter, because 1. I understand less of the city's history and culture, and 2. I liked basically every place more than London, so there is less to complain about. The biggest difference that I felt when I first walked around Paris, and moreso later when I had been in Nice and Menton, is that gathering spaces in France felt more open and welcoming. Not just public spaces, which London also had plenty of, but places like dining establishments, since the French are so particular about what they eat and drink, and spend so much time just chilling alone or with friends at cafes. I would even go further to argue, at the risk of making generalizations, that many of the shoddier neighborhoods still seemed much more lively and communal than in London. In Paris we lived outside of the central city in an area that was similarly populated by a majority immigrant population, but our neighborhood had everything a neighborhood needed: grocery stores, lots of places to eat (including a small French restaurant packed with retirees when I walked in for lunch one day and where I had one of the best meals of my entire trip), and even a small sports center. The place we stayed in London had none of that, despite the two neighborhoods being comparable in terms of socioeconomic strata within their respective cities.

Paris was also one of the most walkable cities I had been in. Typically when you walk you need to find fast food restaurants along the way to go pee in (and in London I was actually stopped by a guard when trying to go into a fast food restaurant's toilet near Trafalgar Square ... why did a fast food restaurant have a guard?), but Paris had these free public toilets that you could enter scattered across the place, and it was never any trouble for me to find them.

There is the trope of the French person who drinks and smokes and eats cheese all day, and 1. it's not wrong, and 2. it's such a great life to live. It's great that these little pleasures are so accessible and normal in France, and that the working class man often shares in these pleasures in a way that isn't just individually hedonistic but culturally important to them. I bought a big slab of Comt&eacute; cheese for 6 euros in Carrefour on the first day we arrived and ate it slowly with bread over the span of the week, and it absolutely lived up to its reputation of being the French peoples' favorite cheese. I think back to the time I walked into a fromagerie on some small street decked with Christmas lights, and the full strength of over 100 different cheeses wafted into my nose. Or the time I went into a department store near the H&ocirc;tel des Invalides and the entire ground floor and B1 sold nothing but wine. It's always good when there's less gatekeeping of nice things.

Architecturally, Paris was also very pleasing to the eyes. Almost the entire central Paris area, which includes every neighborhood with "arrondissement" in the name, had a similar look from the outside: several stories tall, light-colored walls with dark sloping roofs, long narrow windows, small grilles on the balcony. The city was artistically geometric in its layout, and that made for great views when you looked down a street and could just see rows upon rows of stately buildings stretching away.

As a tourist I have little to say about Paris that is bad, especially not after comparing it with London. The food was great, the people generally looked less grouchy, and the weather was much less miserable. I skipped on going to any of the major attractions like the Louvre (which I had been to before) and Versailles, because I felt like I didn't have the adequate historical knowledge or the aesthetic understanding to appreciate what I was looking at. I think that in its totality, the city proved to be a much more interesting and multifaceted gallery than I could have experienced in a curated museum.

After Paris I went skiing for a week in La Plagne. Skiing was great fun, and I stayed with the Singaporean society, which made it more fun because I could see my friends. UCPA had buffets for every meal and they were always delicious. We once had raclette and hot wine. I went down a black slope for the first time in my life, and then I did it two more times. The Alps were refreshing and the views, especially at sunset, were breathtaking.

Ski trips usually last a week before people start to get tired (physically and of skiing), which I thought was the perfect length. We took a flight to Nice from Geneva Airport.

Geneva was one of the biggest letdowns of the entire trip. Our transfer bus to and from La Plagne stopped at Geneva, and when we first took the scenic Eurostar ride from Paris to Geneva I thought that it would be a city swaddled in rolling hills, sitting by a tranquil lake, where every person had a Patek Philippe. I was very wrong. The place was a fucking bum city, with industrial plants belching smoke near the city center, and no sign of any high-value commercial activities anywhere for what I thought was the epitome of first world countries. The airport was even worse, since it was crowded with a million people and there was nothing to do inside or outside. Even the airport in Sofia was larger and had more amenities. All in all Geneva gave me the impression of being a dingy industrial city in the French heartlands.

Nice was very nice. Everything about the place was pleasant, from the food to the weather to the rocks on the beach. When we got to the beach I finally realized why people kept pet rocks (our Airbnb owner had two in his bathroom), because the rocks were so smooth and satisfying to feel.

We stayed in Nice for a night before catching up with other friends, and made our way to Menton where 5 of us squeezed into a room meant for 2 people; it was our friend's student accommodation, which was just a minute from the Sciences Po campus situated on the hillside above the winding labyrinth of the old town. Staying with old friends was fun, plus we had been in Taiwan together earlier in the year (which felt very long ago).

Menton gave me the feeling that if we were in some alternate universe, it would have been completely plausible for it to have been overrun by tourists like Santorini or Cannes as a result of some minor differences in its development (see "Chaotic outcomes" above). The entire city was built on the hillside overlooking the sea, as was Ventimiglia across the border, but Ventimiglia was much steeper (we joked that walking up and down was like traversing a red slope, though we would later find that Athens had even more treacherous terrain) and through the city ran a river that swept mud and sediment into the sea, whereas Menton had a pristine beachfront, half rock and half sand, and the city was less tiring to navigate. I also have no words to describe the sea, except that it was a very, very pretty shade of blue.

Around this time the realization that collections were quickly approaching had crept in, and so I had less time to amble around the various cities we went to, though I tried to log at least one unconventional / non-scenic walk through the non-tourist neighborhoods in every place I was in. After Menton we went to Bucharest, where all the math sites I wanted to visit were closed due to Christmas + New Years, and so I couldn't write anything about it for my travel grant. We ended up going to Sinaia for a day, just to tour Castelul Pelișor and Castelul Peleș. I thought the latter was much prettier than the former, which was reflected in its ticket price being much higher.

<div align="center">
    <img src="/assets/images/dec25opex/pelesoutside.jpeg" alt="Peles Castle from the outside" style="max-width: 60%; height: auto;">
</div><div align="center">
    <img src="/assets/images/dec25opex/pelesinside.jpeg" alt="One of the rooms in Peles" style="max-width: 60%; height: auto;">
</div>

I noticed several things about Bucharest:
<ul>
<li>
Their churches were very small, and they were all nestled within big monotone slabs of residential buildings. When I say nestled I mean literally, there were tiny churches scattered all over the city, and it was like the urban planners just decided to wrap them in big brutalist blocks of grey tenements.
</li>
<li>
Their graffiti is angry and crass. Part of a city's charm is it's graffiti, but there is a point after which more graffiti makes a place look unclean and disorderly. Paris had a nice amount of graffiti, and some streets were full of amazingly vibrant graffiti art (eg around Rue de Belleville). However graffiti art in some places, for example on the tracks at metro stations or on drab infrastructure just looks out of place and unruly, like the graffiti in the Bibliothèque François-Mitterrand station in Paris and the graffiti around the train tracks in Geneva. In Bucharest there were some interesting ones, probably commissioned by some social organization, of homeless people stenciled onto the stone benches by the streetside; yet the vast majority was just messy and consisted of various slurs (many of which were in English), scrawled onto the walls of every residential block, or sprayed onto construction barriers, or on the door of the university library.
</li>
<li>
There were SO MANY casinos. One in every 10 storefronts was a casino where you could walk in and play the slot machines. We went into one at like 3 PM on a weekday, following Christmas, and there were people in there gambling. It was just a small room, maybe the size of a 2-room apartment, and probably with another floor above for VIPs, but this kind of physical gambling was so rampant in Bucharest that it was hard to think of another industry that was as visible as it. Even worse was that more than half the ads you would see on billboards or bus station posters, I'd say around 70%, were for some kind of online gambling or sports betting website. The online part is understandable, but the gambling society thesis has always been that the "gamblification" process, ie. taking something and increasing the variance and skewness of its payout, would permeate into our daily life through online platforms that encourage the easy transaction of money to express "bet-like" structures, NOT that people will start taking their money to the slot machines in real life. In fact, the gambling society thesis expressed as a trade would be explicitly SHORT real life casinos. In Romania I found the complete opposite, which was that physical gambling was still extremely popular, and that the government seemed to have no need to deregulate ANYTHING because there was already so much of it.
</li>
<li>
Related to the above was the observation that there were no office buildings in Bucharest at all. You physically cannot find a office building where you could see people <i>doing work</i>. I should caveat that the work I refer to here is the high value-adding type, like digital services, tech, business, etc. You would expect to see at least some office buildings, or some financial services at the very least, but I walked through the city several times and did not see that even once, except for one time when we were on the car to Sinaia. I think the only major industries in the city that I could think of were F&B, operating tourist sites (not many really), and gambling. So I really don't understand where all the money for gambling comes from.
</li>
</ul>

Overall I was quite disappointed with the state Bucharest was in, having thought that Romania was a relatively upper middle-class country, especially compared to the rest of the ex-Soviet nations. The countryside was nice, but I think I preferred the scenery on the Paris-Geneva Eurostar more than the southern Transylvania scenery, possibly because we went in the winter; we also took a 10 hour train ride from Bucharest to Ruse then from Ruse to Sofia, and the landscape outside the window was just average.

We went to Sofia to watch a friend debate at WUDCs, but unfortunately he didn't break, and when I watched the finals the debate wasn't very good either. The rest of Sofia felt remarkably different from Bucharest. Compare the first two pictures to the third:

<div align="center">
    <img src="/assets/images/dec25opex/bucharest1.jpeg" alt="Picture of Bucharest at night" style="max-width: 60%; height: auto;">
</div>
<div align="center">
    <img src="/assets/images/dec25opex/bucharest2.jpeg" alt="Another picture of Bucharest at night" style="max-width: 60%; height: auto;">
</div>
<div align="center">
    <img src="/assets/images/dec25opex/sofia1.jpeg" alt="Picture of Sofia at night" style="max-width: 60%; height: auto;">
</div>

Obviously the first two were taken with the dramatic foggy context and the large brutalist architecture in mind, but you just don't see much of that in Sofia whereas you could see a lot of that in Bucharest. Even in residential areas which were bound to be uniform rows of grey housing (nothing wrong with that), the way the blocks were spaced and separated, and the way that the buildings still had some kind of uniqueness or differentiability in Sofia, made the place feel more like a place where people lived versus a place where $\exists$ people. Even if everything else was the same, the smaller scale made everything seem normal and cosy like a neighborhood ought to feel, unlike the cold inhuman scale of the residential projects in Bucharest, that still carried the brutal realism of Eastern bloc architecture.

Surprisingly I learned there that Romanian, Bulgarian, and Greek all had different linguistic roots, despite the countries being in a straight line on the map. Romanian shared more in common with the other Romance languages than Bulgarian, despite it being geographically closer to Russia. Bulgarian turned out to be somewhat similar to Russian without many of the declensions. As a result I could guess the meaning of quite a few things on the signs in Bulgaria, because many of the words were quite similar either to words in Russian or to words in Romance languages but transliterated into their alphabet.

In Menton we couldn't observe the Sciences Po students, who had without exception left for home or had gone traveling. In Sofia I had the chance to observe them, both local students and the ones who had arrived in Bulgaria for WUDCs. On our train from Ruse to Sofia we were in the same cabin as a young student couple, who were most likely students at Sofia University, and they invited us to their university's New Year party. As friendly as they were we declined, and as it turned out we would have felt very out of place there because the primary activity at such parties, as I was later informed of, would have been drinking, vaping, and partaking in substance use. This was also the case for the debaters, which I found odd, since people who self-select into debate as an activity and are then further selected by capability to compete at the highest-level competition in the world should be more rational than the average person, and yet by my friend's account they do things like smoking and drinking and other even more unhealthy things just as much or more than the average student would. In fact, not even 10 minutes after the final round of WUDC ended, the entrance to the venue was already blocked by all the debaters who had exited for a post-competition smoke.

In Sofia, as in Bucharest, gambling was still very prevalent. On top of their national stadium you could see the big logos of all their sponsors: without exception they were gambling sites. There were much fewer physical casinos out on the streets though.

Athens was our last stop, and we intended to go there and actually get some studying done for collections, which we did, but I did take some time out to look around the city. Athens had a central area fenced in by a ring of mountains and getting to the central area from the airport took over an hour by public transport because you had to go around the mountains. We stayed in Vyronas, named after Lord Byron, who I learned funded the Greek independence effort against the Ottomans and died fighting for the Greeks. The area was extremely steep, more so than Ventimiglia, and the streets didn't all point up or down in one direction, but rather alternated between sloping up and sloping down like sine waves.

Athens was a very beautiful place. I saw the Parthenon and the bay and the sunset view atop Mount Lycabettus. The houses were squat and squarish, all colored in healthy brick shades or painted a clean coat of white, and there was no grey architecture anywhere. Every floor on every building also had an open walkway or balcony of some sort, and every one of those also had a retractable awning. The people were friendly and we got free food twice, once at a [<u>family restaurant</u>](https://maps.app.goo.gl/AY81zAvQTdCz8kPQA){: .page-link target="_blank"} where we got 3 whole plates of traditional desserts and some wine, and another time at a [<u>seafood place</u>](https://maps.app.goo.gl/G4hgrojJWudrRbLV9){: .page-link target="_blank"} where we got free mastika and ice cream. I think all considered, it was my favorite place with Paris a close second.

Lastly I found something very interesting in the Eugenides Foundation's library: a copy of <i>Euclid and His Modern Rivals</i>, written by a math lecturer from Christ Church whose pen name was Lewis Carroll and who was perhaps better known for other things, which was a very strange and whimsical play about the ghost of Euclid defending why his <i>Elements</i> was superior to 13 different modern geometry textbooks.

<div align="center">
    <img src="/assets/images/dec25opex/carroll.jpeg" alt="Page from Euclid and His Modern Rivals" style="max-width: 60%; height: auto;">
</div>

### Other interesting things

I read a few very interesting articles during this period. Two of them were from Sam Kriss, which I link below with some excerpts that I liked.

[<u>A review of Burning Man:</u>](https://substack.com/inbox/post/177472684){: .page-link target="_blank"}
> But the strangers persisted, and eventually there came an ordinary, cloudy, blustery springtime day when I didn’t have to go to the hospital any more. Suddenly I wanted very badly to get out of London, this grey piggledy city mouldering through its last decades of decline. Suddenly I was acutely aware that life is short, very short, and most of it happens while you’re not really paying attention. I had a strong need to do all sorts of things I wouldn’t normally do. How absurd that we only ever get to be one person. Maybe I should try being a football fan. Maybe I should start going clubbing again. Become a gym bro. Completely reverse all my political opinions. Pilot light aircraft. Join a gang, splash my opps on the 37 bus. But of everything I could imagine, there was probably nothing more foreign to the person I’d become than Burning Man. I said fuck it, yes, I’ll do it, let’s go.

[<u>An account of language as evocative rather than descriptive:</u>](https://substack.com/inbox/post/177472684){: .page-link target="_blank"}
> So: language has betrayed us. Now what? What can language do, besides simulate reality? There are the various perlocutionary acts, persuading, forbidding, seducing, offending, and so on. Language mediates social games and forms the structure of subjectivity. It throws up its own internal problems that can be solved or expanded for fun and profit. It has a shibboleth function, which allows you to distinguish between friend and enemy based on whether they use words like hegemony or not. Some of these intersubjective functions are not always particularly positive, and definitely not useful to philosophy. But others are. We can still use language to access objective reality, as long as we’re prepared to let it take a more active role than straightforward description. Language, and especially philosophical language, changes how the world discloses itself to us.
> [...] All I can say is that it strikes me as very obvious that Heraclitus and Philip K Dick were right: when God created the world, he did so as a kind of play, in the way a child plays. Evil and suffering exist because God is an innocent, and there’s more joy in the wide infinity of imperfect forms than there would be in remaining as a single perfect circle. God put thoughts in our head for the same reason he put whales in the ocean: because they’re big and because they’re absurd and because he wanted to see them leap, and because they are, in ways we can’t understand but might sometimes glimpse, just for a moment, two instances of the same thing.

Then there are some other things written by other people that I thought were nice.

[<u>Speculative fiction about brain uploading</u>](http://qntm.org/mmacevedo){: .page-link target="_blank"}. A terrifying and well-constructed piece about the potential effects of being able to upload an exact image of your brain as an executable program.

[<u>On the poverty line</u>](https://substack.com/@michaelwgreen/p-179492574){: .page-link target="_blank"}. This post blew up because the claim that the poverty line was a 6 digit figure was outrageous, but I think the argument he makes is quite clear and strong, even if it is a bit exaggerated.

### Music

I should start by talking about Spotify wrapped, because it was the biggest thing to come out during this quarter, but actually my wrapped was quite unrepresentative of what I listened to this year. For example, out of my top 5 tracks 3 of them were from Кино which I had stopped obsessively listening to in the second half of the year, but because I listened to so much Russian music in the first half it displaced all the other stuff which I thought I had listened to more of (maybe due to recency bias). In order, my top 5 were:

<ol>
<li>Группа крови by Кино, 65 plays</li>
<li>Constellations by Tokyo Shoegazer, 44 plays</li>
<li>Lover, You Should Have Come Over by Jeff Buckley, 41 plays</li>
<li>Спокойноя ночь by Кино, 46 plays</li>
<li>Лето by Кино, 38 plays</li>
</ol>

Since Spotify stops tracking plays after a certain point I took the data from lastfm's API to check my playcount for the entire year. By that data, my 5th most listened to song was actually 슈게이저 by Misty Blue, which came in at 39 plays.

Unsurprisingly my top overall artist was again Beach House for like the 4th year in a row, and this year I bumped myself up to their top 0.02% of listeners, from last year's 0.05%, clocking 4597 minutes listened (Spotify data, not the full year) and 1089 plays (lastfm data, this is for the full year). The Spotify data did align, however, with the lastfm data on my top artists for the year, which understandably didn't change that much in a month or two; the second to fifth were Deftones, Kino, Radiohead, and Slowdive in that order. Top new artist of the year was Kino with 476 plays, with Tapping the Vein at second with 274 plays (and all within the last quarter). Top classical artist was Wagner at 216 plays, mostly from listening to the Ring cycle.

Anyways during this quarter I listened to private music (the new Deftones album) a few more times and I have somewhat changed my mind on it. Back in September I wrote:
> Some of the tracks on this album like “ecdysis” and “cXz” gave me the feeling that they decided to just spam the formula without bothering to think about whether there was anything else memorable about the song other than being just another Deftones track.

But after listening to it a few times the album grew on me and I started to understand the vision. I could feel that they were taking a step in the experimental direction, which was lost on me in the first few listens but became more apparent in comparison to Gore and Ohms. It's not a big step, and its easy to miss because its noticeable in everything except for the way Chino sings, which often obscures the other things that are going on in the drumming, in the way the various guitars are mixed at different points, etc. Anyways I added <i>i think about you all the time</i> to my playlist.

My biggest find this quarter was Tapping the Vein, which has easily become of my favorite artists of the year. They've only released two full albums, but both of the albums are full of gems, and I didn't actively dislike any of their songs other than the remixes.

Another find was Trout Mask Replica, which I found from reading a review on black midi's album Hellfire, which compared it to TMR. In December I also listened to quite a bit of black midi, because I could finally grasp the full extent of Geordie Greep's insane musical abilities. I think a great litmus test for what type of music listener you are is whether you think Sugar/Tzu is noise or the one of the best fucking musical compositions of all time (even if you don't enjoy the song). If you think it's noise, chances are you hear music in its totality as it is usually delivered, anchoring against the melody and accompaniment (there's nothing wrong with appreciating music in a different way), but that kind of listening doesn't really work on black midi. Anyways I went to listen to their whole discography plus Geordie's debut solo album (which I had listened to before but it left me thinking everything sucked except for Holy, Holy) and discovered many sounds that I liked, and then I read a review of Hellfire which then introduced me to TMR. To be very honest I couldn't see the vision, despite everyone saying it was amazing and it was music but deconstructed and it had 50 motifs every 2 minutes. But I liked Pachuco Cadaver, especially the line at the start:
> A squid eating dough in a polyethylene bag is fast and bulbous

It reminds me of what Sam Kriss said in that article I linked above:
> However much you might hate Derrida, he said it first, and he said it better. He’s great any time he gets a chance to talk about ancient Egypt, or geology, or ghosts. Or in Aphorism Countertime: ‘Survival and death are at work, in other words the moon.’ Fantastic line. <b>Stop worrying about what it means; just think about it next time you see that chilly face looking down on you at night, and see what it does.</b>

As is usual, I list some of the tracks and artists I've been listening to on repeat over the past few months, except that this time I take a bit of liberty to include a banger track that I discovered in some random restaurant in Greece that was too good to leave out, even though it technically goes under the next quarter's plays. There are a lot of standout tracks this time.

Songs / Pieces:

- All My Heart, Bury Me, Butterfly, Hurricane, Burn, Beautiful, and Razor Blades, all by Tapping the Vein
- χειραψία / Gay Anthem for the New Millennium by Κόρε. Ύδρο.
- Ruby by Kaiser Chiefs
- 高级动物 by 孟维来
- i think about you all the time by Deftones
- Glum by Hayley Williams
- Deep Inside by Lite
- Wood Cabin by Saint Etienne
- ペース・ロード by Casiopea
- 将进酒 by 厨子和戏子
- Play Dead by Bj&ouml;rk
- Sugar/Tzu by black midi
- Skins by The Orchestra (For Now)
- P.O.V. by Clipse

Albums:

- Another Day Down and The Damage, both by Tapping the Vein
- Breathe In by Beauty's Confusion
- Φτηνή Ποπ για την Ελίτ by Κόρε. Ύδρο
- Ego Death at a Bachelorette Party by Hayley Williams
- The New Sound by Geordie Greep
- Hellfire by black midi
- Let God Sort Em Out by Clipse

Since the previous opex post, my big beautiful playlist has grown from 186 to 191 tracks, but we are still missing artists whose names start with V, X, or Z.

## Finance

### Gambling society IV

I've already written plenty of things about the gamblification of our world in the two previous opex posts, but it's not something you can point out once and forget about. It's a big thesis that I have a huge amount of confidence in as one of the defining macrosocietal trends in the next 5-10 years. Also very interesting is the question of how to monetize this idea. But first, two posts:

[<u>This post</u>](https://substack.com/@michaelwgreen/p-179492574){: .page-link target="_blank"} refers to the thesis as "long degeneracy" and the manifestation as "hypergambling". In any case it is referring to the same thing as I am. An excerpt:
> long degeneracy is your college friend sports betting. long degeneracy is your uncle trading options. long degeneracy is your participation in an online community instead of an irl one. these trends are modern efficiency applied to human nature - the shortest-term reward cycles.
>
> imagine you are a new college grad from a middle class family.
>
> if you are lucky you have no education debt, but many do. if you are lucky, you land a 100k+ job, but many don’t. and even if you are lucky you still look up at astronomical asset prices (houses, stocks) and try to work out how you can maybe afford one in 20 years. with the understanding that they will only continue to go up in the meantime.
>
> you are surrounded by online examples of success (usually fake or survivorship bias). your attention span has been fried by tiktok and youtube shorts. you simply don’t have the patience or discipline for the slow path.
>
> so instead, you start taking outsized risks with your monthly paychecks - crypto, options (pls no), meme stocks, meme coins, sports betting (pls no). your rationale is that this current amount could never buy a house, but if you win it might. and if you lose you simply have to wait a week or two before you can reload.
>
> that is hypergambling, and if you participate in crypto with a significant percentage of your networth, congrats you are hypergambling too.
>
> hypergambling came into public consciousness around covid. in january 2020 peter thiel wrote to mark zuckerberg, with the observation that:
>
> “from the perspective of a broken generational contract, there seems to be a pretty straightforward answer to me, namely, that when one has too much student debt or if housing is too unaffordable, then one will have negative capital for a long time and/or find it very hard to start accumulating capital in the form of real estate”.
>
> while he was talking about millennials being socialist, that is just the other side of the same coin. hypergambling is the emergent seethe, socialism is the cope.

Then [<u>another post</u>](https://x.com/systematicls/status/2004900241745883205?s=46){: .page-link target="_blank"} that blew up on X:
> [T]he casino is the only place they feel agency. The only place where their decisions might actually unlock the next tier, on a timeline that matters.
>
> Traditional career path? Your manager got promoted for being there first, not for being good, and your whole department might get automated anyway. Stock market? Sure, you can earn 10% annually and afford a house in 47 years, assuming your job still exists.
>
> But crypto? Prediction markets? Sports betting? Your research actually matters here. Conviction pays. Even an imagined edge feels like yours, not something you're waiting for someone to grant you. You're placing bets where your judgment directly determines your results.
>
> [...] The ones who say "gambling is bad, you should stop" are almost always the ones speaking from a privileged position of being in the financial upper class. They SEE a way out; they SEE a path. So they espouse the goodness and kindness of god on staying the path.
>
> For the many imprisoned, gambling is their salvation, and you are literally telling them to accept a life of eternal damnation. That is why they rebel against you. That is why your well-intentioned advice falls on deaf ears.

Reading this in the context of the poverty line article by Mike Green above makes a lot of sense. You can lay down and accept a life of survival bereft of any dignity or agency, or you can strive to escape the middle income "regulatory valley of death". These are the physical world conditions telling you to go long on vol. Then there is the moving baseline of what constitutes sufficiency in life, and this specifically targets people who were already easily impressable to further skew their utility curves to overweight jackpot scenarios. Combined, this makes for systematic overbidding in far OTM vol.

But I would go one step further and suggest that there is no easy way to escape this trap just by employing first-order thinking. Because if you read the second article, it goes on to suggest that the way to play the long degeneracy thesis is to be long the house and any services that enable the demand for gamblification, which is the most surface-level response to "people are gambling more". I don't disagree and I am long a basket of names in gambling, but I'd like to point out that 1. so much of the edge in gamblification is not specifically in gambling, 2. a lot of gambling / prediction contract companies, especially major ones like Polymarket, are currently private, and I think it will continue to be a rather fragmented market for quite a while, and therefore 3. being "long the house" is itself a form of hypergambling if you are playing it with a significant portion of your capital, because there is still so much idiosyncratic risk left EVEN IF you commit to diversifying across public companies that supposedly all get a tailwind from the gambling society thesis.

Rather, I think much of the edge that comes from gamblification is the creation of new sources of inflexible, price-insensitive flow. The biggest story in options during this quarter was the [<u>blowup of Captain Condor / David Chau</u>](https://x.com/insideoptions_/status/2004326880460104119?s=46){: .page-link target="_blank"} and his "Inside Options" trading group, which has been moving so much size in 0dtes in the past years that it visibly affected dealer hedging behavior around their condor strikes. And while I respect the balls of this man to defend a martingale strategy that he supposedly "backtested" (cope), I don't feel any kind of sadness from this because being short vol on your strategy (selling condors), and then being short vol on your implementation (martingle betting) cannot possibly have a 0% risk of ruin. Like there has to be some understanding of the fact that if you are waking up and shorting vol every single day regardless of what price the market is giving you, it is not a foolproof strategy!

Similarly I view many supposed "premium harvesting" strategies with suspicion, and I suspect that the existence of anti-WSB subreddits like r/thetagang is a net positive for professional traders, because on average thetagang and WSB are not looking at the same kinds of stocks, and so you can get price-insensitive uninformed flow in both directions.

I'm starting to think the gambling society thesis as a whole is not about being blindly long gambling-adjacent things, but being a cautious provider of things that people turn to in desperation. This is a hard thing to balance if you don't want to increase your own vol allowance, because volatility is contagious. If you're playing poker with someone who's down several buy-ins and he starts open shoving every single hand he gets, you can either call him any time you have a hand with more than 50% equity, which makes it more likely that YOU get his last buy-in as compared to anyone else but drastically increases your own return variance, or you can wait until you get premiums or pockets, at which point he might already have been called off by someone else, but conditional on you being the one who goes up against him you have a much better chance of winning. However, how exactly you frame this in trading and in life is still unclear to me and requires more reflection.

### Doing math does not excuse you from thinking

Onto some updates about my own strategy. Over the holidays I had planned to actually code up a bot to trade my VX basis strategy, but a few things stopped me from doing that: I got a bit lazy, plus I had a bunch of other things to do like studying and writing this and also enjoying my travels. I'm not sure when I will come around to coding up this bot, because I still think that the strategy has positive expectation, but its recent performance has given me a lot to think about.

Without disclosing the PNL graph, the strategy experienced a prolonged slow drawdown that as of now is still ongoing due to its stubborn insistence on being long vol pretty much since mid-November. This reduced its out of sample post-cost post-spread Sharpe from 3.6 in early Nov to 2.2 on 31 Dec. This is still significantly higher than the in-sample performance, largely due to a period of extreme outperformance during the wild swings in October.

The question then becomes how to attribute this recent performance to random draws from the intended strategy return distribution vs unforeseen changes or flows in the VIX complex, and whether I should rethink my range for the strategy's expected returns, since there were pretty unexpected outcomes in both directions. Firstly there was the unexpected period in October where it got every single move correct during a period of 2 weeks, and secondly there was the unexpected period from late November until now where it got the entire vol crush wrong and has been stubbornly long vol for 2 months.

If I were to be very honest with myself about this strategy, I would say that there is a good deal of historical overfitting in the way this strategy was tested and then implemented. The strategy itself was derived from a paper on the VIX futures basis against a replicating portfolio using options, but there are many issues with the way I implemented it:

<ul>
<li>
The proposed mechanism for why this alpha exists is because of inelastic flow from ETF rebalancing. This was tested by varying the execution time of this strategy across different hours, and predictably the final hours of the trading day showed the most outperformance as such an explanation would suggest, but the issue was that I only had historical EOD options data, and so the backtest wasn't even fully accurate.
</li>
<li>
A further issue is how sensitive the strategy is to the inputs, which I talk more about later. Clearly having different data at 2pm vs 4pm would make a big difference in the final basis value. But despite the strategy being so sensitive to the exact values of the option prices being fed in, there is a relatively large corrective term that I added to the function to account for the fact that on some days, especially on volatile trading days where the data matters the most, there are <i>insufficient</i> strikes to properly compute the value of the VIX futures, at which point we need to extrapolate the value that it should have been if there were sufficient discrete strikes (which is another source of error, since the basis itself is calculated with an approximation of a continuous function, DESPITE the VIX itself being calculated with a finite number of strikes - this is because we have to have a comparable estimator for the vol of vol). The way I do this is very primitive: I assume that the differences between the prices at the strikes prior to the cutoff stretch linearly onwards forever, which if you think about it is extremely prone to garbage in, garbage out calculations, since the prices of highly OTM options are usually worth 2 or 3 spreads at most. In normal times this makes less than a percentage point of difference on the final basis value which itself is a percentage of spot VIX, but when shit gets wild, which is what this error term was designed for in the first place, it <i>works</i> in the sense that it corrects in the right direction, but it introduces new problems with the epistemic soundness of the strategy.
</li>
<li>
Further problems with the soundness of the strategy: the option dataset that I tested on was from an options data provider. The data I use to generate the live signal is from my broker. I believe that EOD prices on something as liquid as SPX + VIX options shouldn't differ by that much, but stale quotes or shit spreads could really mess things up.
</li>
<li>
I definitely introduced a source of overfitting in my backtest where I tested a close position signal compared to a bunch of other possibilities, which helped the strategy avoid the huge drawdowns of the baseline strategy in the 2018 Volmegaddon and the 2020 Covid vol explosions. I don't have data on the 2024 Volmegaddon round 2 or the Liberation Day explosions unfortunately. But this closing signal really has no justification other than the fact that it works and a very hand-wavy and speculative explanation that isn't epistemically sound because I came up with the stopout rule before I came up with the reason for its existence. However this is not super relevant because it has not kicked in meaningfully during the out of sample period yet (I made it after Liberation Day).
</li>
</ul>

While I think that this basis certainly exists and that the base strategy is sound, it's hard to tell whether the changes I made had deviated from the original intention of the paper, which was to capture a noticeable, measurable, and explanable basis spread that, very importantly, exists due to inelastic flow by FORCED actors (ETFs). But the mechanism for the basis' correction to 0 is not clear, due to the difficulty of trading both legs of the basis, and the calculation of the basis itself was prone to minute changes in the prices of a few illiquid options a couple months out. The changes I made, rather than addressing those issues, focused on forcing the returns curve to look more like $y=x$. It reminds me of a quote that I saw somewhere (I forgot exactly where):
> Doing the math about a strategy does not excuse you from thinking about the reason why this strategy should work, and if you can't explain why the strategy exists and isn't arbed away instantly in simple terms, then your strategy is probably full of shit.

The adjustments to the baseline strategy worked in the backtest and in the out of sample period, but they don't work in theory, and that is my primary concern with the way I approached the strategy's construction. I can bite the bullet on the extrapolation function and say that it's a noisy estimator that functions as well as it can during the high-variance periods, but there is no justification for why, say, I use np.sign(signal) instead of weighing by the absolute strength of the signal or by taking a band around 0 where the signal does not trade at all. The only justification is the backtest, which showed that these more epistemically sound ideas somehow performed worse.

Anyways I lost the backtest document, which was saved to my work email account from my internship, and there are plenty of details that I've forgotten. But I do remember a couple periods in 2016 and 2017 where the strategy also performed pretty badly:

<div align="center">
    <img src="/assets/images/dec25opex/ss.png" alt="Screenshot of something I said" style="max-width: 70%; height: auto;">
</div>

It would be very unfortunate for the PNL curve if we get a repeat of the 2016-2017 episode, despite the vol landscape having changed significantly since then, especially in 2018.

In December my bot also broke a few times, most of which had to do with stupid tastytrade changing their data schema which screwed over the API I was using which required an emergency monkey patch while I was supposed to be enjoying my holiday in Paris ... at least it wasn't during the ski trip, where I would have been too tired to work on it at all.

But during that time I ran a whole bunch of debug tests one after the other, and a very concerning phenomenon emerged. Below are the timestamps of the runs and some of the output values (the variable names are just placeholders, S1 and S2 are the two signal outputs):

2025-12-31 23:30:03
a1 = 308.1232 || b1 = 28.0862 || c1 = 16.7343 || a2 = 414.1519 || b2 = 89.8982 || c2 = 18.007
S1: -1.4200
S2: 2.5593

2025-12-31 23:31:10
a1 = 308.3138 || b1 = 29.7751 || c1 = 16.6895 || a2 =: 414.524 || b2 = 93.3886 || c2 = 17.9203
S1: -1.1483
S2: 2.8713

2025-12-31 23:32:29
a1 = 308.4433 || b1 = 28.4645 || c1 = 16.7326 || a2 =: 414.6839 || b2 = 89.3429 || c2 = 18.0372
S1: -1.4095
S2: 2.3961

These runs were 30 minutes after market close (in Sofia time), so granted there was a bit more noise due to spreads and whatever, but this is still quite concerning: a few small adjustments in the options chain somewhere, and I wouldn't even know where, could just throw the whole calculation around by such a large fraction of its value within minutes of each other.

While this isn't exactly garbage in garbage out, it's probably accurate to classify it as noise in noise out, which is just another way of saying that a signal that is this noisy would naturally lead to a very volatile PNL curve unless run over many many iterations. And yet the strategy itself can only be run at roughly a daily timeframe before experiencing extreme Sharpe decay due to spreads and other costs. Besides, the underlying rationale for this strategy isn't meant to be a high frequency one.

Reasons such as this, that could only be understood through actual practice, are part of the reason why I have come to view some of the more theoretical methods used in finance with some skepticism. Things like the complex curves that fit onto unexplainable phenomena spit out by a black box factor model, or complicated portfolio optimization models named after Person A hyphen Person B, which are so frequently cited in academic finance, just find themselves so easily abused as a substitute for thinking. I will repeat this to myself:
> Doing math does not excuse you from thinking.

For any strategy to exist that hasn't already been picked up by Rentech or JS, it must have a measurable and nonconspiratorial reason for existing.

### Polymarket Jesus II

I [<u>previously wrote about</u>]({{ "/2025/06/23/jun-25-quarterly-opex.html#polymarket-jesus" | relative_url }}){: .page-link target="_blank"} the existence of a bet on Polymarket that traded at 3 cents on the dollar with around 6 months to expiry, which would settle to "yes" if Jesus returned in 2025. And people were making fun of it for existing, but actually I thought it was a very smart demonstration of paying to take the other side of a plausible future flow, as the Matt Levine column had basically pointed out.

Anyways the Jesus bet was back in the public eye after Polymarket themselves posted about it, and now that we know it's not some mystery why this bet exists and why the price diverges from just the plain risk-free rate, we can start to understand how this was a clever advertising gimmick on Polymarket's part, because they knew some seemingly nonsensical shit like this would blow up and give them tons of free visibility.

But seeing this made me think about the people who were taking the "yes" side on the contract. I don't think that they made money at all, to be honest. The more that you think about it, the more it doesn't make sense: this market should not exist. You are not <i>loaning</i> money that you can then deploy somewhere else by taking the yes bet; you are simply tying up your capital in some prediction contract structure. And this is where it gets confusing, because the prediction contract locks up everyone's money for a period of time, and during that period of time there is no accrual of interest income to anyone except for the platform. So the upper bound for the no side of the bet should be the current value of a bond expiring at the end of the year, and notice how I didn't say it was a no-arbitrage bound, because nobody is going to arbitrage this, and ONLY YOU would be losing money for being stupid enough to bet "no" above the bond price instead of just buying the risk free bond. The yes side of the bet should be trading at 0, which is the weighted value of the payout (if Jesus comes back your USDC is worthless). Therefore, no trades should be happening at all on this bet, and the fact that the stupid thing still exists means that there are still degenerates out there gambling on the "yes" side of the contract.

It reminds me of [<u>this piece</u>](https://reducibleerrors.com/prediction-markets/){: .page-link target="_blank"} by Agustin Lebron. He writes:
> The absence of natural hedgers in prediction markets ends up being its Achilles heel. Everyone in the market is either a noise trader (the polite term for "degenerate gambler") or a sharp. The former eventually run out of money, so a mature prediction market is full of people with the same risk preferences and goals: to make money trading. And that brings us back to the the no-trade theorem.
>
> The only way for prediction markets to sustain themselves is on the back of new gamblers willing to lose money to the sharps. Is it any wonder that Kalshi, Polymarket and all the others are so pro-deregulation? After all, all the real money is locked up in institutions: pension funds, mutual funds, etc. If prediction markets provided value to institutional participants, why the obsession with getting retail onto their platforms? The answer is clear. Prediction markets only work when there is a steady supply of dumb money.

<div align="center">
    <img src="/assets/images/dec25opex/ss2.jpg" alt="Twitter screenshot" style="max-width: 40%; height: auto;">
</div>

### Other finbro things

Why does the stock market persistently go up? [<u>According to Jean-Philippe Bouchaud</u>](https://www.ft.com/content/6f549890-c2a6-4823-a095-c8ea73f7e6bb){: .page-link target="_blank"}, it's because money flows into the stock market and causes a permanent increase in valuation, and this valuation has nothing to do with intrinsic value. He is supported by a [<u>paper</u>](https://www.nber.org/system/files/working_papers/w28967/w28967.pdf){: .page-link target="_blank"} on the inelastic market hypothesis by Gabaix and Koijen.

VC investor Keith Rabois got in a dick-measuring contest with some random guy and got [<u>ragebaited</u>](https://x.com/compound248/status/1988595495451893763){: .page-link target="_blank"} into offering 1:1 odds on a 31.5 to 1 event. Moontower Kris had this to say:
> Keith is offering an even-money bet, his \\$100k to Compound248’s \\$100k on the stock multiplying by 31.5 [...] I don’t understand how rewarding a troll with the easiest money I’ve ever seen is anything but encouraging future trolls, but maybe this is why Keith is rich and I’m writing on the weekend.

Lastly, vol is elevator up stairs down. This is what the surface looked like in October, before and after the mini vol event.

<div align="center">
    <img src="/assets/images/dec25opex/atmivskew.png" alt="Twitter screenshot" style="max-width: 70%; height: auto;">
</div>
<div align="center">
    <img src="/assets/images/dec25opex/ivsurface.png" alt="Twitter screenshot" style="max-width: 70%; height: auto;">
</div>

## Final thoughts

I think the next quarterly post I write will be a lot shorter. Most of the stuff in this post came from the trip reflections, which I will not have next time. During term time, it is hard to have time to sit down and work on writing something for hours on end, which is the frame of mind I need to produce this. The work we will have next term is highly nontrivial and I am afraid it will get much worse in Trinity.

Additionally, despite the title suggesting that life is 99% luck and 1% effort, this reflection isn't a call to laziness. It is very much the opposite. Much of the luck in our life happens before we are born, because the circumstances of our birth and upbringing prune so many of the random paths that we could have realized instead. Like skiing, where the activity is 99% mountain and 1% you, life has so much room in it for choice despite there being physical and temporal limitations on the individual's agency. In the next quarter, I want to be more conscious of what I can control and what I can't, what blindspots in my mind predispose me to believe that something is in my interest when it's not and vice versa, and what I can optimize in my habits and my thinking.

&nbsp;&nbsp;

[<u>Back to top</u>](#){: .page-link}
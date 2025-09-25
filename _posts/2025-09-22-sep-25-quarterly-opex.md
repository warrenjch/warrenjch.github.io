---
layout: post
title: "Sep 25 Quarterly Opex"
date: 2025-09-22
tags: [quarterly-opex, 2025]
excerpt: Jul-Sep 25 wrap
---

# Introduction

Over the past 3 months many things have happened:
<ol>
    <li>I finished my internship</li>
    <li>Went on a trip</li>
    <li>New updates to the <u><a href="https://github.com/warrenjch/tastytrade-calculator" class="page-link" target="_blank">calculator repo</a></u></li>
</ol>
And some others. I've had around 2 months of time after my internship to basically do whatever I want; some of that time was devoted to reading a book (see my [<u>previous post</u>]({% post_url 2025-09-15-vol-drag-ito-stratonovich %}){: .page-link}). Some of the remaining time was spent relaxing. One unfortunate realization is that aside from being involuntarily unemployed, being put on gardening leave, or retiring, this would probably be the last 2-month stretch in my life where I would have had absolutely no commitments whatsoever. It's very rare to have "intermezzo time" such as this, where the next large objective seems too large and far away to begin worrying about (so strictly speaking, these two months were not really the best time for relaxing because I <i>did</i> have things to worry about). Regardless of whether it was justified for me to do so, I have taken my last short period of freedom easy.

This post is not going to be as long as the inaugural opex post, because as I previously said, part of the reason for me starting a personal blog was that I had too many things I wanted to write down, and some of those things were ideas I had prior to the 3-month period that my quarterly posts were supposed to represent. That said, there were still many dull thoughts that occurred to me this quarter which I feel obliged to post.

## Content links
- [Math](#math){: .page-link}
- [Random thoughts](#random-thoughts){: .page-link}
    - [Cheaters cheat](#cheaters-cheat){: .page-link}
    - [Walking the world](#walking-the-world){: .page-link}
    - [Numbers that go up](#numbers-that-go-up){: .page-link}
    - [Other interesting things](#other-interesting-things){: .page-link}
    - [Music](#music){: .page-link}
- [Finance](#finance){: .page-link}
    - [Gambling society III](#gambling-society-iii){: .page-link}
    - [Sticky trees](#sticky-trees){: .page-link}
    - [The Ross Recovery Theorem](#ross-recovery-theorem){: .page-link}
    - [Futarchy](#futarchy){: .page-link}
    - [Things I've been working on](#things-ive-been-working-on){: .page-link}
- [Final thoughts](#final-thoughts){: .page-link}

## Math

Much of the math I have been doing in the past 3 months is not worth writing about because I would basically be copying off my textbook. Some of the other math is also possibly too trivial or puzzle-like to include. But these two are interesting:

### Kernel density estimators

If you ever try to make a model-free approximation of the IV surface, or for that matter even with nonparametric, non-fitted models, just know that the raw output is going to look absolutely nothing like a curve unless your spreads are practically 0. There are several ways to smooth these kinds of noisy curves, and KDEs are one method.

Say we start with some finite number of empirical observations. We want to, hopefully, reconstruct the underlying true distribution that generated these datapoints. For example, we observe BS IV values for some set of discrete strikes:

<div align="center">
    <img src="/assets/images/sep25opex/kde1.png" alt="Discrete empirical observations" style="max-width: 70%; height: auto;">
</div>

Yes, we can fit a cubic spline through this and smooth it afterwards, which is what I currently do, but the point of this section is to show that KDEs are cool. If we think of these individual datapoints as Dirac delta functions, we then approximate them with kernels (usually gaussian), which are then scaled to properly integrate to 1. For the $i$-th strike $s_i$, we have $K_h(s_i) = \frac{1}{h}K(\frac{x-s_i}{h})$, for whatever the kernel function $K$ is. The idea is that as we add more observations $n$ and let $h \to 0$, then $\frac{1}{nh} \sum_{i}^{n} K(\frac{x-s_i}{h}) \to$ the underlying distribution.

<div align="center">
    <img src="/assets/images/sep25opex/kde2.png" alt="Kernel estimations" style="max-width: 70%; height: auto;">
</div>

Now if you add them up, it should look something like this after rescaling:

<div align="center">
    <img src="/assets/images/sep25opex/kde3.png" alt="Voila" style="max-width: 70%; height: auto;">
</div>

### Yet another ridiculous AC problem

Every time I hear about some question involving the axiom of choice I know it's about to be some brain-melting nonsense, except it's not really nonsense if you assume that AC is true!

Consider [<u>this problem</u>](https://math.stackexchange.com/questions/371184/predicting-real-numbers){: .page-link target="_blank"}. There are 100 rooms and 100 mathematicians. Each room has countably many boxes labeled with the natural numbers, and in each box there is a real number, and the 100 rooms are identical with respect to the boxes and the numbers in them. The 100 mathematicians discuss a strategy, then each enter a separate room in order to open a countable number of boxes before guessing the real number in an unopened box of their choosing. How many mathematicians can guess correctly?

It turns out that at least 99 of the 100 mathematicians can in fact guess correctly. A simple explanation of the solution: let the $i$-th mathematician be assigned the sequence of natural numbers that is equal to $i$ modulo 100. At the start of the discussion phase, they use AC to decide on a representative sequence for any sequence of reals which are equal after some point. When they go into their rooms, each person will open all the boxes that are <b>not</b> assigned to them; for example, mathematician 1 will open the boxes equal to 2, 3, ... , 100 mod 100. For each of those sequences, they have agreed on some representative sequence, so there will be a maximum index $n_i$ (possibly equal to 0) associated with the position of the last box where our actual sequence from the boxes differs from the predetermined representative sequence. For example, if our representative sequence for $i = 2$ is $\sqrt{2}, \sqrt{3}, \sqrt{5}, \sqrt{7}, ...$ and the numbers in the boxes happen to be $1, 2, \sqrt{5}, \sqrt{7}, ...$ then $n_2 = 2$. After mathematician $i$ opens all the box sequences that do not belong to him, he takes the maximum $n_j$ across all $j \neq i$, he then opens all the boxes in sequence $i$ (his own sequence) up until $\max_{j \neq i} n_j +2$ and according to the representative sequence of that, he guesses box $\max_{j \neq i} n_j + 1$ from his own sequence (this index represents that lowest index for which the box sequence matches the representative for everybody else).

If it turns out that he is not the person with the highest $n_i$ among all the mathematicians, then his sequence will be equivalent to the representative sequence at the index of his chosen box. If he is the person with the highest $n_i$, then he's the only person who doesn't know that at index $\max_{j \neq i} n_j + 1$ his representative sequence is no longer the same as the actual sequence; since everyone else's $n$ is lower than his, and thus everyone else will guess correctly. If there are multiple people with the same maximum $n$, then all of them will guess correctly, since they are all guessing the exact index where their box sequence matches their representatives for the last time (max + 1).

And thus, by assuming AC, it is possible that by looking at numbers which are completely random and independent, you will be able to accurately guess an exact real number more than 99% of the time...

## Random thoughts

### Cheaters cheat

In my June opex post I wrote about why, to put it nicely, I am not a big fan of Cluely and the people running it. So it didn't strike me as a big surprise when this happened:

<div align="center">
    <img src="/assets/images/sep25opex/ss1.jpg" style="max-width: 40%; height: auto;">
    <img src="/assets/images/sep25opex/ss2.png" style="max-width: 80%; height: auto;">
</div>

To me it's quite obvious that Cluely is problematic, the people behind it are problematic, and to an extent the whole startup culture glorifying this hyperaccelerationist "just ship more" ethos is problematic. In fact, the guy calling them out ([<u>Soham Parekh</u>](https://news.ycombinator.com/item?id=44468641){: .page-link target="_blank"}, whose work they stole) has quite a bit of lore and arguably better embodies the "just ship more" idea.

I think part of the reason why Cluely and other founders who try to run the same playbook can get attention is due to the normalization of blatant unscrupulousness. The blatant part is important; there have always been unscrupulous individuals at every level of society, but increasingly it seems that from the top down, outcome-oriented disregard for principles and norms IS the new norm. A society that maintains superficially scrupulous standards is at an equilibrium because of the ostracism mechanism, but once hypercompetitiveness sets in we see the signal for being a decent human being, which in theory loads positively on other desirable traits like being a trustworthy counterparty or partner, being easy to work with, etc. being superseded by the sole signal of volume and "quality" of output, which we as humans do not have as strong of an intuitive estimate for, and is much easier to disguise / "hack". And it does seem that in the absence of a signal for being rule-abiding, these people tend to behave in less than desirable ways: the people building a tool to help you cheat on everything, unsurprisingly, cheated in making their own tool.

This sums up everything else I was too lazy to say:

<div align="center">
    <img src="/assets/images/sep25opex/ss3.png" style="max-width: 60%; height: auto;">
</div>

### Walking the world

Chris Arnade is one of my favorite writers on Substack, where he has a blog called [<u>Walking the World</u>](https://walkingtheworld.substack.com/){: .page-link target="_blank"}. My ideas of what travel should constitute have been influenced by his writing to quite a great extent, and though I don't think I'll ever reach his level of hardcore, this time when my friend and I went to Australia we decided to kind of put the "walking" part into practice. Coincidentally, Chris was actually walking around Australia at the same time that we were there, but he left Sydney before we arrived to go to the middle of nowhere.

We witnessed two interesting things there:

The first was when we went to Bondi Beach on the very first day at 6am to see the sunrise. At 6 in the MORNING the beach was PACKED with people who were swimming, surfing, jogging, or doing some other kind of physical activity. Anywhere else I have been in the world, people would either be sleeping or getting ready for work at 6 in the morning. At Bondi it was indistinguishable from midday. We decided to walk all the way back to our hotel from the beach, which took us over 4 hours, but it was a quaint way to observe how the suburban houses with their landed detached plots grew denser and taller as we made our way into the city. There was also a very stark difference in the racial composition of the people we saw along the way; at Bondi we saw maybe 1 non-white person in 1000, and we were also very boisterously accosted by a white man in the toilet who was shouting at us: "You guys already have the city and the university, just leave the beach to us!" (we thought he was talking on the phone at first). He was not even wrong, because the further you walked west into the city the more Asian it became. You could see more Asian people on the street, and more Asian-run shops, and by the time we got back to where we were living, which was just on the fringe of the CBD (a very central location), we were ironically in the middle of an entire row of Thai and Chinese grocers, minimarts, and bars. Just 1km from the town hall, you could see maybe 3 Asians for every 10 people on the street.

What's crazy was that the man was even more right about the university, because we went to USYD that afternoon and on their front lawn and around the quad, roughly 4 in 5 people were Asian, many of them tourists. We snuck into the campus and there weren't as many Asians, but there was still a noticeably high proportion of Asian (likely international) students. For all this to happen in just a generation or so would be quite a shock to people like that man, who perhaps think of themselves as natives of the land, in the sense that he was "in the queue" first, and should have a greater claim to the state's benefits.

This is really the primary contradiction within their immigration policy, which is that immigration works like a $\frac{1}{n}$ function whereas they believe it should either work like a queue, or if it doesn't then we shouldn't increase $n$.

The second interesting thing we saw was related to this. We were fortunate enough to have arrived in Melbourne during the period of their massive anti-immigration protests. I was actually scared that we would miss it, but as I walked out of the restaurant after lunch to find them I saw the front of the protest march right down the street we were on:

<div align="center">
    <img src="/assets/images/sep25opex/au1.jpg" alt="I later found out that the people at the front were a bunch of white supremacists" style="max-width: 70%; height: auto;">
</div>

There was nothing special about what they were saying; it was just like any other anti-immigration protest you would see on the news. But I believe this was the first large-scale demonstration that I had seen in real life, because living in China and Singapore really insulates you against public expressions of outrage at the government or at anything in particular. I was quite surprised, however, by how many Asians there were in the march. I didn't expect a single Asian to be in the march prior to seeing it, partly because the massive influx of Asian immigrants was pretty much what triggered the protests in the first place, but there was quite a sizable minority in the predominantly white parade, whom I thought were either very passionate about the cause or very unconcerned about their personal safety.

We also had the privilege of seeing the counterprotest prior to the main protest, though it was much smaller in scale, occupying only the front plaza of the library and the street beside it (I don't know why they chose to do it outside of the library where people were studying), whereas the main protest stretched on for at least 4km by my estimates. There were plenty of Palestinian flags and anti-Israel signs; I'm not quite sure what the purpose of that was other than perhaps ragebaiting the anti-immigration protesters (which worked, because some of them got into physical altercations), but the only reaction I witnessed as I passed the counterprotester encampment was an old white man shouting "We hate Israel too, take all that shit outta Australia" to a chorus of cheers.

In a sense, protests are mainly social and emotional events. It's a place to share in the revelry of being angry together at some target, be it immigrants, other races, sexual minorities, the government, or whatever. There is no attempt at all to convince anyone, not the people on the other side, or the politicians. The whole purpose is to make your vocal dislike known to everybody. As a tool of persuasion, it is completely useless. As an event you can enjoy with your like-minded friends, it is quite fun.

Slightly unrelated but also slightly related: [<u>here</u>](https://walkingtheworld.substack.com/p/walking-america-albany-again-and){: .page-link target="_blank"} is one of Chris' posts that I recently read and I think it's great.
> Because the idea that you can engineer happiness, contentment, or fun, is about as high brow and detached from humanity as you can get. That isn’t how people, outside perhaps the small group of us overly rational uptight Front Row types, operate. Most people don’t try to build their lives around grand long-term schemes of fine tuning a matrix of variables. They don’t think in terms of Max efficiency, Min pain. What they want is both far simpler but impossible to model in a spreadsheet. They want to belong, hopefully as a valued member of something larger than themselves. That often means those shabby organic communities, because they understand life is complicated.

### Numbers that go up

Slightly related to everything above: [<u>a good piece</u>](https://moontower.substack.com/p/adam-smiths-backdoor){: .page-link target="_blank"} on the imperfect metrics that we swear allegiance to. Numbers going up is a lot easier to measure than some complex composite assessment of prosperity. But when we abstract away what we are really trying to measure (prosperity) into numbers given by the market, which can be manipulated separately from the underlying, then it becomes easier to play the different game of "making numbers go up" instead of "making prosperity go up".

The numbers that make up our current measures are [<u>highly leveraged</u>](https://moontower.substack.com/p/capitalism-is-a-temporary-condition){: .page-link target="_blank"} to <b>volume</b>. If you recall my gripe about the abomination of "just ship more" + being blatantly unscrupulous, the problem is that everyone is optimizing for some form of volume, be it in memetic attention or in hypercompetitive industries. You can ship more, iterate more, grow faster, cannibalize your opponents. This way your CAGR goes up, your NPV goes up, you make your numbers bigger and you are happy. Unfortunately there are externalities to this that eventually come back to bite, like the anti-immigration protests. The government was just trying to make their numbers go up, and the people who didn't get a say in that weren't too excited about it; unsurprisingly the response is to reduce the volume of immigrants, which in other words is to deleverage the numbers that go up.

### Other interesting things

- [<u>Zombie formalism</u>](https://news.artnet.com/art-world/history-zombie-formalism-1318352){: .page-link target="_blank"}. If art is the dual space to the societal psyche, this is in some sense the dual to identity politics: the backstory outweighing the outcome, displacing the viewer's agency in judgment, and taking the emphasis away from perception and presentation, towards "process-based abstract[ion]".
- [<u>VR rave parties</u>](https://www.wired.com/story/60-hour-dance-sessions-simulated-sex-and-ketamine-inside-the-world-of-hardcore-vr-ravers/){: .page-link target="_blank"}. I think most people will naturally have some slight sense of aversion/discomfort at the idea of spending so much time in VR, almost like a kneejerk reaction towards escapism (with its negative connotations). But consider: VR is essentially an extension of many other escapist tools we have, like many forms of fictional media, or doomscrolling, etc. It's probably better framed as a lossy experience machine. I don't think there's anything wrong with wanting to enter an experience machine insofar as it completely removes the need to deal with real life; the problem here is that VR does not fully supersede reality, and that makes your choices in the VR world bleed into the real world and vice versa. So if you take drugs in VR, with our current state of technology it means that you took drugs in real life. Will there come a time when VR and neural chips are able to simulate all the senses? If this technology is not used to enslave the world, then perhaps there is a point where I would go from saying "this would make me uncomfortable" to "this form of escapism will better maximize my happiness".
- [<u>Sam Kriss on the rationalists</u>](https://samkriss.substack.com/p/against-truth){: .page-link target="_blank"}. A long-winded and heavily intertextual and hilarious roast of Yudkowsky and the entire rationalist community after they criticized him for not clearly signposting his made-up characters as fiction.

### Music

I wrote a great deal about music last time because I thought it was appropriate to explain how I compare music. This time I don't have to do that again, so this section will be a lot shorter.

The biggest thing I was looking forward to in this period, other than the surprise Silksong announcement, was that Deftones was finally releasing a new album. When I heard the singles I was actually quite disappointed at first, because 1. it sounded a bit overproduced and tinny, 2. I fancied myself as an old geezer and complained that:
> the fact that in just a couple weeks the new deftones single has already double the plays of some tracks on gore and ohms is proof that many of the current deftones fans are POSERS who only listened to 5 deftones songs from tiktok

I guess the fact that they styled the track titles and the album title all in lowercase grated on me because there was no reason why they, as a relatively popular and respectable band, had to perform this imitation of shitty newgen artists (in light of Sam Kriss' article I will clearly signpost that I meant this in jest). But in reality I don't actually care about the optics of it. They can name the tracks whatever they want, but the real problem was that many of the tracks didn't have that distinctive jagged melodic sound that made them my second most played artist of all time. There's a Deftones formula that makes their songs unmistakeably Deftones even if you didn't hear Chino's voice. Some of the tracks on this album like "ecdysis" and "cXz" gave me the feeling that they decided to just spam the formula without bothering to think about whether there was anything else memorable about the song other than being just another Deftones track.

To be fair this is not a new thing for them, because both Ohms and Gore had plenty of tracks that gave off the same feeling (and those were understandably not very popular). The last really good album, imo, was Koi No Yokan, which gave us incredibly melodic tracks from start to finish. I would say that all the albums from White Pony to Koi No Yokan defined their sound as a kind of rugged, creative harmony with a liberal dose of accidentals. On average, you don't hear that in Gore or Ohms except for the standout tracks, and it's the same for private music.

It's not like I don't like some of their less melodic stuff; Korea and Dai the Flu are great tracks that are relatively less melodic than some of their others, and yet they work because there's invariably something else like a strong riff or a driving bass to back it up and turn the monologuing into something with a rhythmic purpose. I don't think they have managed to pull that kind of track off recently. From Gore I saved 4 tracks to my playlist, from Ohms 3, and from private music only 2: infinite source and ~metal dream. These two are pretty good, and they're the two most melodic tracks from the album, which unsurprisingly ended up being the ones I liked.

Aside from the new Deftones album I also tried listening to other new things. I got into bluegrass and tried to get into country. I've found plenty of good bluegrass songs and albums, and in fact one of my most played albums in the past 3 months was The Phosphorescent Blues, a prog bluegrass album. I can't say the same about country, from which I have yet to find any songs or albums that I truly enjoyed. I think the genre as a whole suffers from a few problems: there's a very constrained universe of melodic motifs to select from because nearly all the songs are entirely in G or C major, and there is a lack of focus on the timbre of the instruments because most of it is driven by the quality of the singer's voice. For the "energy level" of a typical country song, there isn't enough tonal richness in the lower registers to drive it because all the common instruments like the guitar, banjo, harmonica etc. are all in a relatively higher register and produce a flatter, thinner sound. Put all that together and you get an artform that, without some modifications, usually struggles to produce any outstanding or highly memorable tracks. I hope to be proven wrong on this in the future.

I also listened to music written in other kinds of English. There's the album A&eacute;gis by Theatre of Tragedy, written wholly in Early Modern English, which I am not qualified to judge the accuracy of (but it did sound pretty decent). I also tried listening to reggae and found the gem of a track, "Ganja Smuggling", which is so effortlessly funny that I'm not even sure whether it was meant to be funny.

Over the past 3 months these were the new things I've been listening to on repeat, ordered by plays:

Songs / Pieces:

- Осколок льда by Aria
- Mutter by Rammstein
- Flying by Anathema
- Cassandra by Theatre of Tragedy
- Shooting Star by Anekdoten
- Take Everything by Mazzy Star
- Familiarity by the Punch Brothers
- Do It Again by Steely Dan
- Ganja Smuggling by Eek-A-Mouse
- Take the Box by Amy Winehouse

Albums:

- Der Ring des Nibelungen by Wagner (my most played album of the past 3 months, simply because there are 178 tracks in it...)
- Mutter by Rammstein
- private music by Deftones
- Among My Swan by Mazzy Star
- The Phosphorescent Blues by the Punch Brothers
- Rumours by Fleetwood Mac
- Stories From The City, Stories From The Sea by PJ Harvey

Since the previous opex post, my big beautiful playlist has grown from 173 to 186 tracks, and from missing artists whose names start with E V X and Z, to now only missing V, X, Z.

Another side note: I've been trying to learn how to do the hand flute on and off, and recently I finally figured it out. Right now I can only consistently play B3 to E4 or F4 at best. I have no idea how people can get up to [<u>3 octaves</u>](https://www.youtube.com/watch?v=yZxxVlGAy08){: .page-link target="_blank"}.

## Finance

### Gambling society III

I previously argued that our society has normalized gambling because:
1. People are uninformed and think that their EV is positive when it's actually negative, or they don't care that it's negative and just love to gamble.
2. Under a change of measure it is possible that the EV will not be negative.

However I think I missed the even easier explanation, which is why there is now a part 3. In the spirit of my previous post on variance drain, this section will explain why people misunderstand what they should be calculating the expected value of.

Consider a coin flip game with the following payouts: if you flip heads, you double your bankroll, and if you flip tails, you lose $\frac{3}{4}$ths of your bankroll. There is a clear positive drift if you play this game over many rounds with a proper betting strategy; if you Kelly bet $\frac{1}{6}$th of your bankroll on each flip, this would be a very attractive game to play.

The problem is that people are not interested in the only real free lunch, which is rebalancing, and instead want to maintain a fixed allocation to their speculative gambles. The people on WSB who have gotten big wins from having 0 risk management did not stop YOLOing after hitting the jackpot once, and this is the same for many things where the distribution of outcomes is similarly skewed by extremely unlikely jackpot events. In the coin game, similarly, almost everyone who plays this without rebalancing will end up with nothing in the long run, since the geometric mean return is $\frac{1}{\sqrt{2}}$ of your bankroll. The reason why the arithmetic average of the flip looks good, in the same way that variance drain is disguised under a continuous process, is that over all possible universes there will be one or a few paths where you keep winning and winning and become a megagigagillionaire, whereas every other path effectively leads to ruin.

You can call it nonergodicity, or variance drain / vol drag, but fundamentally it's the same idea: AM > GM and AM here is highly deceptive because of the influence of big jackpots.

I think the reason why this explanation eluded me the first time around is because it leads to the odd conclusion that gamblers <i>can</i> be profitable if they just rebalance and do Kelly betting. Most bets that are being sold to us in real life are not going to be profitable regardless of what betting strategy you use. However, there are still cases where people do have quantifiable and repeatable edges (recall that the gambling society thesis is not purely a financial concept), and these CAN be messed up by having bad risk control because you misunderstood which EV is actually relevant to you.

[<u>This article</u>](https://convex-strategies.com/2025/06/18/risk-update-may2025-just-do-it/){: .page-link target="_blank"} puts it brilliantly:
> "It is the flawed practice, throughout the industry, of applying ensemble averaging as though wealth were an ergodic progression, and therefore using simplistic short term, probabilistic, expected returns as a decision-making tool. Properly evaluated, investment returns must be evaluated as non-ergodic and evaluated with time averages." ... You put good brakes on your car, not to drive slowly but, rather, to drive faster, safely.

### Sticky trees

One problem with modeling option IV surfaces is that whatever you calculate is only valid for the fleeting moment when your spot price hasn't moved. After the spot price moves, the entire vol surface tends to reprice itself in some unpredictable ways, and you have to make plenty of assumptions to make your previously calculated values work. The two intuitive methods for making extending your vol surface's shelf life are:

1. You cover your eyes and pretend that the IV hasn't moved.
2. You take the vol surface from the previous spot price, and map it onto the options with the same delta at the new spot price.

According to [<u>this note</u>](https://emanuelderman.com/wp-content/uploads/1999/03/risk-regimes_of_volatility.pdf){: .page-link target="_blank"} from the widely revered E. Derman, the first method is called "sticky strike" and the second is called "sticky delta". But there's a third method proposed here:

3. You calculate what the local implied vol is at each price level, and assume that is fixed as spot moves.

This means that you assume IV to be conditional on price and that it changes locally according to where the price is. Typically, as put skew would suggest, you expect that price is more locally volatile when it is low than when it is high. If we assume that, when we go from a spot price of $S_0$ to $S_1$, the overall contribution of the local vols between those levels are roughly uniform, then as an estimation we can consider the IV of $S_0$ at $t_0$, when we calculated the vol surface, to be the (linear) average of the local vols at $S_0$ and $S_1$.

Example: $S_0 = 100$, and from our vol surface $\sigma_{90} = 25$%, $\sigma_{100} = 20$%, $\sigma_{110} = 18$%. The local vols at $t_0$ will satisfy $\frac{l_i + \sigma_{100}}{2} = \sigma_i$ for each price $i$. Therefore we get: $l_{90} = 30$%, $l_{100} = 20$%, $l_{110}=16$%. Now suppose that at $t_1$ the price moves up to $S_1 = 110$. Now we can reprice the IVs as such: $\sigma_{90} = 23$%, $\sigma_{100} = 18$%, and $\sigma_{110} = 16$%. As you see this is quite the opposite of what is suggested by sticky strike and sticky delta; under SS the IVs would have stayed the same, under SD the IV of the 90 strike would have gone up, whereas under ST the IVs deflated across the board.

Clearly each of these has their own moments of applicability but to me ST seems like the most reasonable set of assumptions, followed by SD and then SS. The note includes some general observations on when each set of rules will most accurately describe reality, which in terms of the realized vol regime go from SS applying in low RV regimes, SD applying in trending regimes, and ST applying in choppy regimes, which, if you think about it, is the most important regime to know how to adjust your implied vol surface in.

### Ross Recovery Theorem

While trying to figure out whether it was possible at all to recover the physical stock measure from the risk neutral measure I came across [<u>this paper by Stephen Ross</u>](https://www.nber.org/system/files/working_papers/w17323/w17323.pdf){: .page-link target="_blank"}, which I completely did not understand, and a [<u>SE post on this topic</u>](https://quant.stackexchange.com/questions/15099/what-are-the-main-flaws-behind-ross-recovery-theorem){: .page-link target="_blank"} answered by Peter Carr (whose name seems to pop up everywhere in option pricing literature), which I did not completely understand. But from what I did understand it turns out that you can recover the pricing kernel IF you assume a bunch of very specific and unrealistic things!

### Futarchy

Futarchy is a proposed form of government where voting decisions are decided by futures contracts. You specify some metric you want to optimize for, like GDP, and people bet on how much different policy proposals will generate in GDP. For example if we are optimizing for GDP and the two proposals are "implement UBI" and "don't implement UBI", and the futures on each settle at \\$1T vs \\$1.1T respectively, then the "don't implement UBI" proposal is taken, and the people who bought futures contracts in that market will be paid out according to the difference between their bets and the actual final GDP value. The interesting part is that the people who bought contracts in the other market, the "implement UBI" market, will have their trades reversed so that they don't lose any money at all.

It's quite similar to some other kinds of "multidimensional blockchains" but in general it's just some nerd shit with little practical use. However, there's a very interesting counterargument to futarchy outlined in [<u>this post</u>](https://dynomight.substack.com/p/futarchy-market){: .page-link target="_blank"}: that the cancellation property of futarchy, which is meant to make it fair to people who didn't vote for the policy that was eventually implemented, distorts the markets depending on what type of uncertainty is attached to the bets. I think the concern raised by this article is pretty inconsequential wrt the actual implementation of futarchy because when the contracts settle, any certainty that was previously an uncertainty has already been priced in, and any uncertainty that's still an uncertainty will be priced the same way regardless of whether it's aleatoric or epistemic.

More interesting, I think, is the idea of the epistemic uncertainty premium. Consider a slightly more consequential variation of the experiment in the article. Say that in the future we are visited by an alien race. They offer us a deal: at a uniformly random time within the next 48 hours, they will come back and ask us for our decision whereupon we can offer a treaty of peaceful coexistence, and they will prepare to roll the holy tetrahedral die of their religion which has a 25% chance of deeming us worthy of coexistence with them, and a 75% chance of instantly blowing up the Earth with alien magic. However, ChatGPT 218 tells us that if we decline their treaty and instead surprise them with an attack before they can use their die, it estimates that we have a 20% chance of completely beating them and an 80% chance of losing and going extinct, but it requires 24 full hours to deterministically calculate exactly which of these scenarios will play out. Since we are living under futarchy, two contracts are set up on "peace" vs "war", where the metric to optimize for is the probability of humankind's survival. Because the markets are not fully liquid, whatever contract has a higher price at the exact instant the aliens come back will be taken (instead of waiting for the prices to adjust to reflect the "expiration event" occurring; this is necessary because if the markets were allowed some time to factor in the news of the aliens' re-arrival, then the probabilities will instantly collapse back to 25% and <25% respectively and it's no longer fun to think about).

The argument in the article is that at the very start, the war futures will definitely be priced higher than 20% and almost certainly also higher than 25%. This is because if ChatGPT comes back and tells us that we are in the deterministic universe where we are 100% going to beat them, the contracts will instantly go to 100%, whereas if we are in the universe where we lose and die, the contract will drop slightly below 25%, after which existing holders will not want to sell any more given that their money will be returned anyways. So if time is perfectly continuous (in the mathematical sense) and everyone is perfectly rational, then in theory the price of the war futures will start somewhere between 25% and 100%.

However this thought experiment differs from the post in that the expiration time of the contract is not known. If we knew for a fact that the aliens will come back after 48 hours, then the contract will be priced at $1 \times 0.2 + 0.25 \times 0.8 = 40$% before we get the answer from ChatGPT, and it would be priced according to the simulation results afterwards. But now, there is only a 50% chance that we get the answer before we are forced to make a choice, so the futures (I think, but I might be wrong) should start at $0.4 \times 0.5 + 0.2 \times 0.5 = 30$%, and this figure slowly climbs towards 40% as the first 24 hours pass since the probability that the aliens come before we get the answer drops. Following the reveal at the 24 hour mark, the prices will again act as they would in the fixed expiry case.

You see how this is different from the idea in the post, because it actually allows for the possibility that at the time of expiration, the prices of the contracts do not actually reflect our best interests. If everyone is voting according to what <i>actually</i> maximizes our survival probabilities, the peace treaty is obviously the winner. However under the futarchy scenario, theres a 50% chance that we choose the option that gives us a lower chance of survival.

### Things I've been working on

I got around to making the second update to my options repo, and it now has a few new methods regarding greeks, the yield curve, etc. I was planning to release another update some time in September but many other things happened and the third update didn't really materialize. However on the private repo that it mirrors, I've had to switch the login method from username + password to OAuth, and the public repo doesn't have that yet, so I have to stop being lazy and update that as well.

Last time I wrote that:
> The Sep and Oct expiries are highlighted in the chart because CRWV's IPO lockup ends 24 Sep. IF, and this is a big if, we can even trust the calculations of my pricer at all, then this is suggesting that people expect at least part of the event vol from the IPO lockup to resolve <i>before</i> the lockup ends, meaning people are pricing in a frontrunning of this event.

It is now 24 Sep as I write this and absolutely nothing has happened. The vol surface can lie.

## Final thoughts

This month marks a time for endings. It will be the final full month in a 3-year educational gap and also the end to nearly a decade spent in Singapore. Contrary to what others say this is not a bittersweet moment. The bittersweet moment is when you revisit the place you left years ago and realize that that unnameable quality of being 12 or 21 comes only once and that the people and places which anchored this feeling have long since changed or disappeared.

The next time I write this will be in December, which coincides with my first term break; very fortunately my planned publication timings all happen to coincide with my holidays. I hope that the next 3 months will not completely overwhelm me to the extent that I wouldn't have time to write, but it is the time to be locked in after all. If there's one more thing I hope for, it's that life will be enjoyably challenging.

&nbsp;&nbsp;

[<u>Back to top</u>](#){: .page-link}
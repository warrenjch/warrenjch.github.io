---
layout: post
title: "Jun 25 Quarterly Opex"
date: 2025-06-23
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
- [Final thoughts](#final-thoughts){: .page-link}


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

This is still being simplistic because there are other motivations for gambling. Peer pressure is one of them. You get peer pressured by people you see online who struck it big. We didn't have this problem before social media.

The funny thing is that we have a risk-averse culture in most parts of the world, and yet this is the one thing everyone seems to be risk-taking on. Because most actions with convex, risky payouts require work, and gambling is easy. Of course there are people taking the convex risky bets (like making a startup). I'll talk about them in the next section.

The last bit of the "why", I think, has to deal with existential dread. Everything feels out of reach, and more so with AI. What's the point if actually trying to work towards something offers little upside? This is a doomer viewpoint, but I think a sufficient number of people are starting to buy into this idea, and a good number of them are by no means "stupid".

This motivates the idea of <i>scam theory</i>. It's just a dumb name for the fact that the worst, scammiest, dumbest sounding names in the equity space have all seemed to outperform spectacularly over the past months to a year. It was especially apparent during the post-liberation day rally. While funds were net short and every macro person was calling for risk-off, retail names like PLTR, CRWV, and CRCL just kept going up. RGC makes quack traditional Chinese medicine, has never turned a profit in its history, and its stock went up 600x in a year. I think if we are to believe that the endgame for the dollar based world is to inflate their way out of their mess, then there is merit to buying the most fundamentally unsound companies that have captured retail interest and pump the hell out of them.

Everyone looks at historical bubbles and comes to the conclusion that you should not be investing in a speculative bubble. I think that the opposite is true. Obviously this is not financial advice, but you should absolutely be investing during a speculative bubble, and in the most leveraged retail-heavy names, because that's upside convexity. The worst thing that can happen is that everything crashes all at once, but the default assumption is that stocks keep going up and in the case of these stocks, you have a very long right tail. It's free convexity for delta-1 investors. When everyone wants tulips, and the left tail is priced richly since people know what happened to bubbles in the past, you can buy tulips and put spreads.

One last thing I heard about recently was that Labubus were becoming ridiculously popular again in China. I thought this trend died last year, but apparently it is alive and well. When there is money sloshing around everywhere with no feasible outlets, these kinds of stupid things become the release valve.

### AI and the "smell"

[<u>Terence Tao went on Lex Fridman's podcast recently.</u>](https://www.youtube.com/watch?v=HUkBz-cdB-k){: .page-link} I don't know how Lex convinced him to do a 3 hour podcast but it's quite interesting (I skimmed through most of it). Terence puts complicated things in an accessible way.

One of things they talked about (I think around the 2 hour mark) was how AI could "hijack" our human sense of smell for the quality of something, such as a mathematical proof or a piece of code. That's what most people have observed after using AI for a while: it bullshits very confidently. It's ok in qualitative disciplines to an extent, but its horrible in math because it would make a nice-looking proof that looks completely correct but the error would be some absolutely asinine mistake that no real human would make. He says that before AI, you could tell if somebody's mathematical output was good or bad from the way it was written (its "smell"). I get his frustration because I've seen it before too (in way less complex contexts than him no less).

Something I noticed is that this has never been unique to AI. AI succeeded in convincing people to treat it as a competent expert on everything because it bluffs its way into success. That is the same thing people have been doing for years to give themselves a leg up in their workplace, to get seed funding for their startups, to get into good schools with "shell projects" that might have been the work of an admissions advisor. In effect, AI just managed to hijack this kind of behavior and replicate it on a massive scale to people who have never really had to deal with the issue of differentiating between quality and confident bullshit before (at least at high stakes).

This brings me to the topic of techbros. There's this trope of young, visually successful uni dropout founders that really irks me because I don't think it used to be so prevalent. On one hand we admire them for their ability to take the convex bets that actually require hard work and effort. On the other hand we all know that it's shallow and psychopathic to some degree. Who the hell is using all these products from the AI startups when OpenAI, Gemini, Claude etc are years ahead? And yet these insufferable startupbros, who would have gone quietly and neatly into the business of consulting or finance in the past few decades, are now crowding into the "trade" of starting an AI startup.

A few observations on this:
1. I want to single out Cluely as the one that annoys me the most, because its founders [<u>keep</u>](https://x.com/benaratame/status/1936198119622164668){: .page-link} [<u>posting</u>](https://x.com/cluely/status/1932969921086115860){: .page-link} [<u>this</u>](https://x.com/im_roy_lee/status/1936138361011585190){: .page-link} [<u>kind</u>](https://x.com/benaratame/status/1934345585232154993){: .page-link} [<u>of</u>](https://x.com/benaratame/status/1934009291129880899){: .page-link} [<u>shit</u>](https://x.com/benaratame/status/1933787207011348580){: .page-link}. It's so intentional and insufferable. The worst thing is that everyone in the startup sphere seems to post and behave like this.
2. There is something to derive from their branding of going <b>viral</b>, which is that the endgame is clearly not to be profitable for most startups. The endgame is to get more and more rounds of funding before getting bought out, or better, going public via a SPAC. To do that, you first need a crazy marketing strategy to cover up the "smell". It's perfectly legitimate but it's a twisted way of doing capitalism.
3. I call this a "trade" because we can analyze it from the perspective of payoffs. More and more smart people are funneling themselves into this sinkhole with infinite money at the center. But it's not really infinite money. At some point the user infra for AI will be built out and it will probably be done by the same players who are actually making the big LLMs. All the startups that are currently piggybacking on this wave are bidding for a call option on something where the right tail is getting smaller and smaller.
4. From a utility point of view, it makes no sense to go all in on this kind of stuff for a normal person, ie. dropping out and playing the startup game. It makes no sense to go all in on anything that's not near certain really. But there is a lot of self selection here and I suppose most of the people who are able to play this game in the first place have some kind of safety net in place (privilege).

I think it would be a better world in which these people ended up in consulting and finance, because the point of those industries (the client facing part at least) is to cover up the "smell" and bluff your way through. It feels odd to see this being applied to a somewhat serious industry. At least that's one real world application of scam theory: the flip side of Buffett's claim, which is that when the tides are high you can go swim naked. (When else would you have the chance?)

### Signaling

In NS I was a signaler (didn't really do much though I guess that's why they call it Slackmont). The funniest thing about signalers is that we go through a whole course to learn how to operate a bunch of radios that we bought from Israel or some other country in the 80s and 90s and have been using until today. These radios are a huge hassle to set up and the process of setting them up requires so much communication and coordination that the enciks end up using Whatsapp or their walkie talkies to get it done anyways.

The point is: signaling, like lots of other things we do, is about <i>signaling</i>. The army as a whole is quite an apt example for this: we signal that we are following "regimentation". Yes we need to learn how to do things the "proper" way except that we have perfectly legitimate alternatives (like the MCR) that work in all the cases where we would need to use the radio anyways, but noooo only the enciks can use the MCR and everyone else still needs to do this whole theater of setting up the radios and antennas.

I wanted to write about signaling because it's so intertwined with everything we do now. We have a game where everyone wants to get X, and there are people who are in charge of distributing X (think college admissions, company HR), so we need to devise ways to signal that "I have the qualities that make me deserve X". The "I have" is the important part because it can be gamed. Crimson Education is basically in the industry of doing this for rich uni applicants. I'd like to think that the people who distribute X have some kind of incentive to try and weed out the people who are bluffing from the people who don't know how to present themselves, but that's probably not really true, and even if it was true, we already talked about how people can mask their "smell".

[<u>Here's an article</u>](https://yaschamounk.substack.com/p/the-college-essay-is-everything-thats){: .page-link} that argues why the college essay is more unfair than standardized testing for the less privileged, and I can't agree more. The gist of it is that it's a game of separating those who can mask their "smell" and those who can't, and this has a positive correlation to your level of privilege. Also, as the writer points out, it is extremely <b>CRINGE</b>. It's like whoring yourself out. Dear admissions officer, please look at my entire life history and tell me that I am acceptable for your tastes. If there's anything to celebrate about AI taking over selection jobs, it's that the thought of an AI parsing your essay is less cringey.

I need to go on a bit of a digression here: the conventional path of education is one of those weird things everyone accepts. Sure, you develop interpersonal skills and learn a bunch of basic things that you absolutely need to know in order to survive. But I'm quite certain there's much better ways of doing this and that the current school systems in most places don't optimize for the outcome of "making this person functional in society". They optimize for the outcome of "getting this person into the next stage", be that high school, university, or a job. This is very similar to the startup pipeline. Each round of funding is done with the intention of making the company survive until the next round of funding, at which point the startup is offloaded to the next stage. It's a neat compartmentalization of risk because hardly anyone has the money or expertise to get a startup from incubator to IPO.

Risk compartmentalization is probability curve control. You cut the left and right tails of the distribution off (or at least shove them very hard towards the middle). It doesn't mean we don't have enough people working on individual ways to help gifted students or special students, but man if this was the final evolution of education I would be very disappointed. Unfortunately risk compartmentalization is a staple of capitalism so it is what it is.

The point of this digression was to say that in fact, school isn't about learning. It's about signaling. So when students are cheating on their assignments, it's not just because they are lazy (maybe some are), but that most students know that the most important thing about your education is the piece of paper you get at the end. It's a "stepping stone". It's a 敲门砖 (same idea). If you get A's, you are halfway there to covering up the "smell".

The guys at Cluely figured this out and made it known to the whole world. They want you to be able to cheat on everything. Which is part of why I hate them: nobody wants to play this stupid game but if you forced everyone in the world to play chess and some people start using Stockfish to cheat, the outcome is that everyone will start using Stockfish to cheat unless we make a new game. And it's infinitely more fun to play the game without everyone having Stockfish but guess what, because these dumbasses said the quiet part out loud, everybody is gonna have to settle for the stable but worse Nash equilibrium.

A more common example is that if the people at the front of a movie stand up for no reason then everyone else will have to start standing up and the outcome is the same. This is the idea of 内卷 in China. I don't think there is a good English translation for this (social involution?) and it's weird because I see it happening everywhere but this is only a part of public discourse in China and not so much elsewhere. But I also think it's very obvious in Chinese industries in particular. The joke goes that in China the purpose of a public company is not to maximize shareholder value but to minimize the shareholder value of their competitors. It's true: look at EV and delivery engaging in their ridiculous price wars.

内卷 causes market dysfunction. This is coming for (or has arrived in) everything else we care about, like our schools and jobs, because there is no real antidote to it unless you tell the people in the front to sit down. Too bad the people in the front don't give a shit!

One more good piece I'm sharing is [<u>this piece by slatestarcodex on the purpose of schools.</u>](https://slatestarcodex.com/2014/05/23/ssc-gives-a-graduation-speech/){: .page-link} Everything in this blog is really well written. I am nowhere as well read as Scott but I hope the quality of this blog converges upwards towards the quality of his in the future.

### Music

Before I go back to talking about the gambling society we are going to discuss music at length. Anyone who knows me well in real life knows that I am very passionate about finding and listening to good music. I might write more on this topic in its own post some time in the future but here are some thoughts about it:

I think peoples’ music tastes can be generally explained by two factors with a combined $r^2$ of around like 0.7. The first factor is musicality, ie. how much you enjoy the music based on its melody, chords, and other purely tonal things that make music music. The second factor is lyricism, ie. how much you enjoy the music because of the lyrics. I think there is a third factor called style, ie. how much you enjoy the instrumentation, structure, and the idiosyncratic quirks of a particular artist or genre but I’m not sure how much this overlaps with the other two factors and I haven’t thought about it that much.

This isn’t to say that you can’t think that musicality and lyrics need to go hand in hand or can elevate each other or whatever. You can think that your enjoyment of music is dependent on some nonlinear function of M and L and you can have a very highly weighted cross term. For the sake of simplicity however I’m just going to assume that there’s a subjective weighing scale for musicality and lyricism (and the unknown other factors U), and that how much you enjoy any piece of music is $\text{enjoyment} = am + bl + \mathbf{c}\cdot\mathbf{u} + \epsilon$.

For me, $a \gg b$. I care a lot about whether the music has a memorable melody, a good riff, good chord progression, etc. and not so much about what the lyrics are. My friends know my favorite genre is shoegaze and the whole point of this genre is that you can’t hear what the hell they are saying. I also like a lot of the adjacent genres, eg. metal, where sometimes the point is the lyrics but you can enjoy them without the lyrics and the vibe is still there. This is also why I don’t like some of the old school metal stuff because I prefer my metal with more melody (eg. Alcest).

Another way to test this for yourself is to see if you like listening to music in languages you don’t understand (or classical music). I listen to a lot of music in foreign languages, mostly Japanese because they have a huge shoegaze and indie rock scene. It doesn’t matter that I don’t understand the lyrics because the chords and texture (this is arguably in the style dimension) carry the song.

I also really like Cocteau Twins, which is another good example of maxing out on musicality and not caring about lyrics because most of their lyrics are gibberish or very lazily pronounced Scottish English. One of the difficult things about being a Cocteau Twins fan is that if you get a song stuck in your head and you forgot the name, it’s almost impossible to figure out what song it is unless you go back and listen to everything again (there are no lyrical markers to search for a song with).

I want to put classical music in a separate category from these because I think most classical music is actually an acquired taste (actually all music is but moreso for classical). If your parents forced you to learn an instrument when you were young chances are you would be less bored by classical. I know there’s a lot of people nowadays who swear classical music bores them to death. Some of the solo piano stuff can really feel that way if you didn’t acquire the taste, and it’s complicated because that’s a marker of privilege. Therefore, I think it's a more biased test compared to listening to your favorite genre in a different language to determine if you are type M or type L.

To go further on this I think it’s an acquired behavior to want to acquire a taste for classical music. This should kind of make sense if you agree with my previous statement that it’s a status marker for upper-middle class kids. I would go further to posit that yes, there is a form of negatively connoted signaling game here. If you are the type to unironically listen to Sorabji you probably think the brutes who listen to “50 Best Mozart Pieces for Studying” are uncultured brutes (I dislike Sorabji and I think the same). I don’t know enough about the philosophy of aesthetics but I think there’s a mapping from the “harmony - atonality” scale to the “average enjoyability” scale that’s concave and peaks around the French impressionist composers. Most people who go to the right of Scriabin on the atonality scale are, imo, signaling more than enjoying. (Maybe I’m the uncultured brute here)

I got around to writing about this music stuff because my friends and I were comparing our music tastes and I realized that the guy who I thought would have the most polar opposite music taste to mine actually matched my taste very highly on the musicality scale. I used to disavow everything pop-related (actually, I think before 2021 I barely listened to anything aside from classical, but the evolution of my music preferences probably requires a separate post to explain) but I started listening to Lana Del Rey because I’d rate her music high on the musicality axis (and nice on the style axis too).

Many of my friends are Taylor Swift fans. Statistically speaking it’s not surprising, but I really don’t get the hype. The number one reason I hear is that she has great confessional lyrics. Ok, maybe it’s my personal preference but I don’t care much for confessional writing, which is why Elizabeth Jennings was my least favorite writer back in high school Lit. And the thing is, as someone who doesn’t have a high bar for lyrics, I don’t even think her lyrics are that mindblowing. So let’s just say that this is my skill issue. The next reason I hear is that her music is catchy. I don’t disagree, <i>some</i> of the radio hits are catchy, like the ones from 1989, but most of the songs are not “catchy” because to my untrained ear they all start to sound very similar after a while. For context, in order to figure out what the hype was about I went to listen to every single one of her songs, some more than once, like some time last year and I decided that most of it was really mid melody-wise except for a few tracks. I’m sure that there have been people talking about how her music is formulaic before, I’m not going to repeat it but there most definitely are a bunch of formulas that obviously work well because most people like her songs, but for some people whose coefficient for musicality is sensitive it gets boring after a while (yes I like formulas but her type is a bit too linear for me).

Something that part of her fanbase believes is that her different eras featured different genres of music. Look I don’t think genres are fixed and it’s not a very important distinction, but let’s be real: all of it is pop. The reason why I want it to be rightly classified as pop is that pop can and should achieve pop musicality without having to veer into other genres which have their own rules for musicality. “Wildest Dreams” and “Style” are good because those are representations of pop musicality through a “moving” melody and strong delivery. Here “moving” doesn’t mean emotionally moving, it means that the melody is moving around onto different notes instead of staying and droning in one cluster. That’s what pop is supposed to be ie. playful singable music.

As I said there were a few of her songs that I really liked, which are cardigan, seven, Innocent, Better Than Revenge, and Miss Americana. I actively dislike the lyrics of Miss Americana but the texture of having the piano accompaniment is nice. I think the latter half of Speak Now has a nice rock influence to it but I wouldn’t call it pop rock.

Aside from that I really think the rest of the songs are alright and not “really good I want to listen to it again and again”. As the most popular artist in the world right now it makes sense for her average song to be above the global average. I think she gets a lot of unjustified hate from people who lump her music in with a bunch of other stereotypes of people they dislike who happen to listen to her music. You only get the right to call someone’s music “mid” if you listened to all of it, though I can say that in this case if you didn’t like a random sample of her songs you are not going to like the rest.

Two final quips:

I get a lot of really good recommendations from Spotify’s discover weekly. Their algo is actually insane. It doesn’t just recommend you things it knows you will like (based on genre preferences) but things you yourself didn’t know you would like from completely different genres. I’m sure it’s not just taking what other people with similar tastes like because that would overweight “nearby” genres. I’m talking like mixing EDM and 80s jazz into the stuff I listen to and knowing I’d like those. For some reason the algo that decides what songs to pick for you after you finish a playlist are nowhere as good.

I also just checked that in my shoegaze playlist, I am still missing artists whose names (romanized) start with the letters E, V, X, and Z. If I don’t count romanized names I am also missing Q. I expect this to be remedied when the playlist grows to 300 songs (currently at 173).

Some of the new things I’ve been listening to a lot over the past 3 months, ordered by most played:

Songs / Pieces:
- 슈게이저 by Misty Blue
- Genie by Crumb (I think I would have listened to this more if it wasn't for my trip to Taiwan where I basically didn't listen to music for 5 days)
- Air Supply by Sweet Trip
- Movies by Weyes Blood
- Death by Computerwife
- Woodland Rites by Green Lung
- El Makina by Jadal
- Time by Pink Floyd
- Tubuh Yang Padam Tersulut by Harum Manis
- Группа крови by Kino

Albums:
- El Makina by Jadal (yes the track above is from this album)
- 너의 별 이름은 시리우스 B by Misty Blue
- Trigger by Design19
- Static and Silence by The Sundays
- Verspertine by Bj&ouml;rk
- Malyoun by Jadal
- чёрный альбом by Kino

I am surprised that Kino is still on this list. Against all odds I have still not given up on learning Russian and one of the biggest motivators I had back in February or so was to eventually understand Kino's lyrics. I am like nowhere near that goal and I wouldn't bet on myself not giving up before the end of the year but we'll see.

The problem with my music listening habits is that I get tired of things way too fast. At the end of last year I thought this year was going to be my Radiohead year because I experienced a huge resurgence of interest in the earlier Radiohead albums around that time. I think I was obsessed with "Black Star" for at least a month which is one of the longest times that I've been obsessed with a track, but by around February my Radiohead listening stats had gone off a cliff. I then thought that this year would be my Russian music year but that also didn't last too long. In April I thought this year would be my Bj&ouml;rk year, and in fact she's the second highest new artist on my top listened for 2025 list (after Kino) so far at 234 new plays. But that also didn't last very long.

On the classical side of things I listened to a bit more of Lang Lang playing Liszt. His performance of R&eacute;miniscences de Don Juan is sooo good. The funny thing is, my most played classical composer year to date is neither Liszt nor any of my normal go-tos (Ravel, Grieg) but Mozart. It is possible that I am the uncultured brute who listens to "Mozart study music"!

## Finance

### Gambling society II

Earlier I talked about the gambling society as a culture in which lots of people make high variance, negative EV decisions with their money. I said: “People gamble on negative EV outcomes for two reasons. The one we are talking about now is that they don’t have perfect information and think that the EV is actually positive.”

Now let’s talk about the other one. In the derivatives world there’s this neat concept called the risk neutral measure. One way to think of it is that it’s the probability of events weighted in such a way that reflects peoples’ risk tolerance for the event. If everyone is positioned long and is averse to a sharp drawdown, then puts will be priced in a way that is not supported by the actual “physical” probability of a drawdown but once the risk aversion is accounted for, then they are priced correctly. Simple example of why this is necessary is that you buy insurance even though the expected payout is less than what you are paying, because the left tail events need to get overweighted in your decision making calculus. If $\mathbb{P}$ is the default physical probability measure and $\mathbb{Q}$ is the risk neutral measure then you can have $E_{\mathbb{P}}[X] < 0$ but $E_{\mathbb{Q}}[X] = 0$.

How this applies to gambling is that the second reason people gamble on negative EV bets is that the EV under the risk neutral measure is actually positive. Assume this simple model of an individual K: K earns a monthly salary, most of which is used to cover rent and expenses, and has almost nothing left over to save. This is the reality for an increasing number of people due to inflation! Consider K’s individual utility function: they can save their extra bit of money, perhaps put it in the S&P 500 if they are prudent, and wait for it to grow. Say they earn the median American salary of 40k and save 5% of their monthly disposable income (consistent with BLS data). In 30 years, assuming the S&P grows 6% a year in real terms, they will have around 160k in 2025 dollars. What can 160k buy for a 50 year old in 2025? Jack shit! In 2055 I don’t reckon AI gives us luxury state funded communism yet, and actually if it does then you should be gambling all your money away NOW while it still has value. So you end up with 160k that doesn’t do jack shit, and the utility value of 160k when you’re 50 is much lower than spending the money when you are young. Not to mention that a few visits to the doctor in the US and K will be bankrupt anyways, regardless of whether they saved or not.

So the alternative is to gamble right now on sports betting and meme stocks and altcoins. Yes it is negative EV, but imagine if you actually hit a jackpot. Maybe you invested in the next GME or the next Bitcoin (there will never be another Bitcoin until SHA256 gets cracked and someone invents a Qitcoin, but there can always be pumps here and there in meme coins). That one large payoff is enough to completely change your life. 1k to 1m is more than 500x as good as 1k to 2k on the utility scale because it's a qualitative change in how your life operates.

In the process of writing this I found out that I wasn’t the first person to theorize about this idea of a [<u>convex utility function</u>](https://en.wikipedia.org/wiki/Friedman%E2%80%93Savage_utility_function){: .page-link} (so sad man). My idea of it is actually a lot less nuanced than the Friedman-Savage hypothesis, because all I’m saying is that at a certain point above for example 3-5x your annual income, your utility curve starts becoming convex instead of concave, and only flips back much higher. If lots of people are in the same boat then naturally there will be demand for “call options” on your own wealth ie. lottery tickets, and that means the risk neutral measure shifts to reflect that.

Two ways which this links back to what we discussed in part I:

Firstly social media is responsible for changing the risk neutral measure. This is a roundabout way of saying that social media has made wealth more attractive because we see it and we want to have that kind of life instead of the one we are stuck with. If your life still feels like shit no matter how much financial prudence you practice, and you are bombarded every day with people who flaunt their wealth, then it’s natural for your utility curve to skew more convex on the upside.

Secondly this is a uniquely capitalist problem. If you were in a feudal society gambling couldn’t suddenly make you an aristocrat. Among other things, it’s not that easy to mask your “smell” when social classes and upbringing are so disparate. In today’s world it’s easier than ever to mask your “smell” and it’s also easier than ever to get access to lottery tickets. (On the topic of “smell” I think being nouveau riche is even something people want the rest of the world to know.) I know it sounds completely trivial but I think it’s not because a lot of societies around the world are capitalist in the sense that money is a proxy for power, which is usually political. You can’t just gamble yourself into power in those countries. You can however gamble yourself into money in western liberal democracies (in the sense of the difficult convex bets from the second section, not recreational gambling) and the forward implication of "money &rarr; power" is <i>probably</i> stronger than the reverse implication, which is more prominent in less transparent democracies and autocracies.

To close off I think it’s also important to look at gambling together with the other choices we make in life instead of as a standalone “bet” on your future wealth. If you think about it, jobs are basically short calls on your future. If you have a shitty dead-end job, perhaps gambling is a right-tail hedge for the opportunities you’ve given up. Of course most people aren’t considering these things when they gamble and I’m definitely ascribing more rationality to gamblers than they possess, but it’s a good way to make sense of what’s going on.

I’m long on gambling but the public gambling companies are kinda mediocre so I need to find other ways to gamble on this. The other way is just to increase factor exposure to scams and ponzis ie. scam theory. You can still make money doing thematic or macro-based value, but in today's world I think value purists who absolutely disavow shitty investments will probably only see their stocks revert to fair value by the next ice age.

(I didn’t know BRK was a shark in the derivatives scene but apparently they hire MIT PhDs for this stuff, so much for value investing.)

### Unreasonably good backtests

Lately I’ve been interning at a quant firm and one of the models I’ve been working on is a model to trade VX futures based on some spread that should converge. The problem is that one side of the spread is near impossible to trade so the idea is to just go unhedged and trade only the VX futures. There are two very odd things about the backtests of this strategy:
1. It performs <i>very</i> consistently in the hours after the signal is generated, in the sense that the EV in each hour seems to be quite similar, which many other rebalancing based strategies don’t exhibit because unless the agent that is doing the rebalancing is slowly rebalancing small constant amounts, you should be seeing a few big moves when they actually do the rebal and small moves otherwise.
2. It performs unreasonably well given that it’s unhedged. If there’s a spread between A and B and both are freely moving values, you would expect to need both legs of the spread trade to make money. For some reason this thing performs well with only one leg, albeit the more liquid leg, but the liquidity difference is not enough to explain why this performs so well.

I’ve done enough backtests to rule out lookforward bias and it uses a very strict formula so it’s not overfitting either (probably, because I did make a few small adjustments that might have p-hacked the outcome but realistically they weren’t huge adjustments). I can only think of a few reasons:
- There is some problem with the data, which is not that implausible because I recently got a new data source with higher granularity and it disagrees sometimes with my old data.
- The overall sharpe isn't actually that good if you take the measurement from the start of the data sample (2010) but there was a very visible and very explainable inflection point after 2018 volmageddon, and the sharpe hugely increased after that. I’m making the assumption that since then there has been a permanent shift in the vol landscape to make it reasonable to take the post 2018 sharpe as an indication of future returns instead of the full sample sharpe, but I could be completely wrong. This can only be proven if I get data for 2024 to test whether the strategy performed even better after volmageddon 2 but I don’t currently have that data.
- I also worked on replicating another strategy involving FX from an academic research paper. The paper was published in late 2020 but only used data up to 2018. I started testing this strategy earlier this year (2025) and the data provider, who is the same data provider from the paper, gave us data until the end of 2024. This paper claimed to get 1.7 sharpe post cost (and this is a high capacity strat). The funny thing is that I managed to replicate their strategy (even though it was VERY vaguely worded) and it performed like absolute shit after early 2018. I wonder why they conveniently stopped the backtest in 2018… anyways, this is the “past results are not indicative of future returns” possibility.
- The last reason is the scariest reason and the one I really hope is not the case. Theoretically this strategy has unlimited risk because it's naked short VX around 40% of the time. A wise man once said that if you can't explain the source of your returns, then you are probably getting compensated for toxic risk that nobody wants to take on. In the vol space that means holding the hot potato (short VX) when the music stops. If "hedged" trades like the Parplus corridor varswap can blow up, this spread most certainly can also blow up especially since I am only running one side of the spread trade. There is a persistent premium effect observed in this strategy and I really hope it's not a case of the peso problem because I actually plan to trade this.

### Ipad kids

In the spirit of analyzing everything using options I wanted to share this half-baked idea: when parents give their young kids Ipads and other devices to entertain themselves with, it's equivalent to selling a risk reversal on the kid's overall lifetime satisfaction. The same line of logic applies to most actions that involve trading off long term benefit for short term happiness but I just wanted to talk about Ipad kids because I always see them in public. I sympathize with the parents because they always look tired as hell but if your kid is going to play Cocomelon brainrot on the bus can you at least give them earbuds or tell them to turn that shit down?

Let's take another look at the risk reversal idea. I think it's reasonable to say that Youtube kids is full of brainrot slop content and that this is both fun to the kids in the short term and harmful for them in the long term. So what is the benefit of doing this? I can think of one very obvious answer that makes sense when translated back to plain English, which is that you profit when skew goes up. Notice that I don't say that you profit when spot goes down because you are long the underlying and you don't want it to go down. But if let's say AGI comes out when the kid is in high school and causes widespread panic for everyone competing to enter the white collar workforce. Guess what, your kid is probably happier and more well adapted than the other kids whose parents were scared to death of AGI when their kids were young and forced them to study math and coding all day to try and outrun the development of AI. The kid doesn't have that emotional sunk cost baggage of "my parents spent so much effort on me just for me to lose to AGI". That's a big benefit in the post AGI world imo: being relatively unbothered by the whole thing on an emotional level. If AGI comes and the guy who had no childhood because he was busy playing the signaling game and participating in the nonsense involution process turns out to be as useful as the guy who spent his childhood chilling and doing whatever he wanted and probably had a lower expectation for his future achievement level anyways, who is going to have a higher overall lifetime satisfaction level? I don't know but I've got my money on the guy who had a life.

### Polymarket Jesus

I'm going to copy paste something I wrote in my telegram chat because it's a banger of a topic.

interesting take from matt levine today: the fact that "Jesus will return in 2025" is trading at 3 cents on the dollar on polymarket is NOT because people are stupid, but rather its a bet on the discount rate of "polymarket dollars" going up, because:
1. at the current interest rates, if u believe "jesus will not return in 2025" is a 100% guaranteed thing, then u should be paying 97-98 cents on the dollar for that outcome otherwise u would be better off holding treasuries
2. since polymarket allows u to combine a yes bet and a no bet into 1 USDC, it enforces arbitrage conditions so that the no + yes prices > 1 (with cost), which is why the yes bet HAS to be $0.03 even if it is impossible;
3. and if it is impossible, the point of betting on "yes jesus will come back" is that a. ur betting on the interest rate to go up and the fair value of "no" to go down, and under no-arb conditions yes will go up, or b. something happens that requires people to sell their "risk free" contracts in "no", eg if they want to take bets on some other very sudden thing that happened, and that increases the discount rate on "no" which again causes yes to go up

[<u>This is the link</u>](https://ericneyman.wordpress.com/2025/03/24/will-jesus-christ-return-in-an-election-year/){: .page-link} to the original post that Matt Levine got this idea from.

### Things I've been working on

I've been working on overhauling my whole old tastytrade bot stuff using the tastyware sdk, because my own code was just really complicated and I suck at programming so I'm just going to freeload from now on. Anyways I managed to get the VX strat working as well as an option data storage pipeline in Supabase, which is nice because otherwise I'd have to pay for this data, but the problem is that it will be years before this data is of any use to me, and by that time I will hopefully have graduated from university and <i>hopefully</i> will be working somewhere that has access to all this data at a higher granularity and precision anyways...

The good part about this is that in the process of building out the option database infra I got around to making an IV visualizer. Here's the visualizer applied to CRWV (taken from Jun 19 iirc):

<div align="center">
    <img src="/assets/images/crwv-jun-25.jpg" alt="CRWV IV chart">
</div>

It's so ridiculous that my pricer can't even apply Black Scholes, which is why the left side drops to 0 because it broke the pricer (and I'm using Gaussian smoothing so most of the stuff past the peak is useless). Good news: this is not just MY skill issue, because I checked on the same day and moomoo's IV pricer broke too!

The Sep and Oct expiries are highlighted in the chart because CRWV's IPO lockup ends 24 Sep. IF, and this is a big if, we can even trust the calculations of my pricer at all, then this is suggesting that people expect at least part of the event vol from the IPO lockup to resolve <i>before</i> the lockup ends, meaning people are pricing in a frontrunning of this event. I don't see any reason otherwise that explains why the Sep expiry is more expensive than the surrounding expiries.

## Final thoughts

This post took me several days of intermittent work to write. I did not expect it to take this long, and I know my prose here is very unpolished, which I would like to improve upon in the future.

I have so many things I want to do that I've written down in my notes but never got around to doing. But actually when I look back at my list, a lot of things that I forgot I had even written down in the first place were actually the things I finished! I don't think I will be able to find another internship right now and I'm quite happy at Quantos, plus they are chill with me staying until end Aug. If that's the case (90% probability) then I plan to take the whole of Sept to just chill at home and clean up all the things I promised myself to do but didn't do. I've gotten too good at canceling plans for stuff in order to balance the rate of increase in plans vs the rate of completion of plans.

I got two textbooks from China the last time I went which was 2024 March. One of them I took several months during NS to finish because I read like less than 10 pages a day. It was Fraleigh's abstract algebra book and it was a hard slog because studying during NS is not easy when there's distractions and saikang everywhere. Also, abstract algebra is not easy without a teacher or mentor because I don't have 150 IQ. The other one looks to be even harder and I will challenge myself to finish it in September so that I won't have to bring it to Oxford where I definitely won't have the time to finish it because I will have so many other things to do.

That is all. [<u>Here is a picture of pear baby, who was a placeholder in the 2025 section of my old blog while I was working on revamping it.</u>]({{ "/assets/images/pear-baby.jpg" | relative_url }}){: .page-link} Thank you pear baby.
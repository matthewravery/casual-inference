---
title: "Analysis Philosophy"
author: "Matthew Avery"
date: "2019-01-03"
menu: main

---

From what I understand, teaching professors (maybe all professors?) write a "Philosophy of Teaching Statement". The goal of this documen is to describe the individual's approach to teaching and why they use that approach. It basically says, "Here's what I do, and here's why I do it," and maybe you get into a little bit of how they got there. In my view, it's akin to a teaching world-view. It's an opportunity for a professor to organize (and interrogate a little) their entire approach to their chosen profession. 

That sounds to me like a useful exercise, so here goes my Philosophy of Analysis Statement!

### The things that have had the largest impact on the way I approach analysis

My academic background is Economics and Statistics (the latter in undergrad, the former for my master and PhD). My professional background includes a lot of experimental design and quantitative data analysis on a wide variety of data sets. The subject matter is defense testing tends to be complex. While many times we have designed tests, they're rarely executed according to the DOE. Data sets I've dealt with range from $n < 10$ to an $n$ in the hundreds of thousands, and they cover everything from tight, hyper-specific DOEs to purely observational studies. The kicker is trying to turn this analysis into something you can trust a Congressional staffer to understand. 

On top of this mix, I'd add sports, politics, and policy into my bag of influences. I've always found public policy debates interesting and read a lot of papers both when I was studying Economics and since then. And sports statistics is one of the things that got me into looking for ways to do data analysis in the first place. I started with Baseball Prospectus back when Nate Silver and Kevin Goldstein were still there. Due to the nature of my work, many of the examples I'll use on this blog will come from sports and politics rather than my work directly. 

So that's where this comes from. 

### How I approach data analysis

Briefly, "Don't be wrong". Slightly less briefly, "Be as little wrong as possible." At this point, everyone's heard the old George Box saw about models, and this is more or less the same. But my point is to be constantly vigilent for ways that humans can make errors when looking at data and do my best to avoid them. Aside from the typical <a href = "https://www.uzh.ch/cmsssl/suz/dam/jcr:00000000-64a0-5b1c-0000-00003b7ec704/10.05-kahneman-tversky-79.pdf">Khaneman and Tversky</a>-style cognitive errors the human brain tends to make when approaching randomness, there are a few points I tend to focus on. These are things that bring complexity to problems and analyses but tend to be easiy to avoid or overlook. I'll briefly discuss each in turn.

#### Dimensionality

Reality is highly dimensional. As a result, so are most of the problems we look at. That means that getting full, comprehensive models of them is very challenging. We typically get around this by collapsing the problem into a workable number of dimensions and addressing those. Examples abound, but sports statistics provide convenient ones. From <a href = "https://legacy.baseballprospectus.com/glossary/index.php?search=WARP">baseball</a> to <a href = "https://www.basketball-reference.com/about/per.html">basketball</a> to <a href = "https://en.wikipedia.org/wiki/Corsi_(statistic)">hockey</a> to whatever else you want, people are always trying to devise useful single-number summaries of player value. The motivation is obvious. The job of "sports player" requires a combination of specific athletic abilities, technical skills, and mental capabilities. Everyone doing it at a professional level is an outlier relative to the overall population, and no two players are identical, even when <a href ="https://www.hockey-reference.com/players/s/sedinhe01.html">they</a> <a href ="https://www.hockey-reference.com/players/s/sedinda01.html">are</a> <a href ="https://www.basketball-reference.com/players/m/morrima03.html">identical</a> 
<a href ="https://www.basketball-reference.com/players/m/morrima02.html">twins</a>. So if we want to have any hope of understanding this problem, we've got to find some way to collapse those dimensions down. 

This isn't a statistics or data science thing, either. MLB scouts were reducing position players to <a href = "http://fivetoolschool.com/what-are-the-five-tools-in-baseball/">five tools</a> since before Billy Bean was playing let along a GM. 


But often times by collapsing a high-dimensional problem into a few-deminsional problem introduces new challenges. The single-number stats for player evaluations mentioned above have well-known deficiencies. It's just the nature of the best that when you reduce dimension, you lose information. Well-informed practitioners understand the limitations of their tools and are able to account for these deficiencies as part of their analysis. For example, <a href = "http://www.espn.com/nba/story/_/id/10740818/introducing-real-plus-minus">Real Plus-Minus (RPM)</a> is a single-number statistic that <a href = "http://www.espn.com/nba/statistics/rpm/_/sort/RPM">ESPN</a> defines as follows: 

> Player's estimated on-court impact on team performance, measured in net point differential per 100 offensive and defensive possessions.

And it does this pretty well. But folks familiar with how it behaves. They know that it's not particularly stable with small sample sizes, so you should take it with a huge grain of salt the first few weeks (months?) of a season. They also know that it doesn't account very well for opponent's shooting "luck". (I put luck in scare quotes because determining what is luck and what isn't measurable and whether the distinction is meaningful beyond semantics is a whole other post.) RPM is also weirdly disconnected from the sport of basketball. Depending on your team's composition, grabbing the player with the highest RPM won't always be the best way to improve it. Becuase of these limitations (and others), some folks simply dismiss deminsion-reducing statistics like RPM out of hand. 

I find a similar phenomena arises when non-statisticians talk about p-values. They often fall into one of two camps. The first camp consists of True Believers. They're not sure how to winnow their model or determine which factors matter the most, so they look to the p-value to save them. They adhere to their chosen $\alpha$-level with religious fervor. The other camp dismiss p-values out of hand. They're subject matter experts, and they know an important factor when they see one, damnit!

The answer of course is in the middile. My view is that p-values are useful tools, and I often use them for model selection and helping me determine whether a factor is important enough to call out in a report. But its always within the context of the larger problem. It's always after taking into account those extra dimensions (the circumstances of the analysis, results from similar analyses, the potential relevance of the effect size, etc.) of the problem that he p-value has collapsed away. 

#### Distributionality

Things have distributions, especially groups of things.

#### Non-linearity

Things have interactions and they're not always smooth. 


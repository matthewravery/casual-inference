---
title: "Analysis Philosophy"
author: "Matthew Avery"
date: "2019-01-03"
menu: main

---

From what I understand, teaching professors (maybe all professors?) write a "Philosophy of Teaching Statement". The goal of this documen is to describe the individual's approach to teaching and why they use that approach. It basically says, "Here's what I do, and here's why I do it," and maybe you get into a little bit of how they got there. In my view, it's akin to a teaching world-view. It's an opportunity for a professor to organize (and interrogate a little) their entire approach to their chosen profession. 

That sounds to me like a useful exercise, so here goes my Philosophy of Analysis Statement!

### The things that have had the largest impact on the way I approach analysis

My academic background is Statistics and Economics (the latter in undergrad, the former for my master and PhD). My professional background includes a lot of experimental design and quantitative data analysis on a wide variety of data sets. The subject matter is defense testing tends to be complex. While many times we have designed tests, they're rarely executed according to the DOE. Data sets I've dealt with range from $n < 10$ to an $n$ in the hundreds of thousands, and they cover everything from tight, hyper-specific DOEs to purely observational studies. The kicker is trying to turn this analysis into something you can trust a Congressional staffer to understand. 

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

I only get 1,750 hits on Google when I search for "Distributionality", so maybe I should clarify what I mean, though I don't think it's anything profound.

That data follow distributions is a tautology. When this doesn't appear the case, it means we've failed to properly model hte data generation function. The most typical failure mode is to assume that the distribution is simpler than it is. Statistics (and science, and human cognition, and ...) is rife with simplifying assumptions, so there's nothing inherenly wrong about them. 

Take the opposite approach, and imagine modeling data using a purely empirical CDF. Your tool box is now limited, and a lot of inference is now harder, but those are mechanical problems. But you still haven't solved the most challenging problems like, "What can I predict about a new observation that might come from a different sub-population?" 

So we make basic assumptions, either about our data ("IID") or about our inference ("Future observations come from the same distribution as my sample!"), all of which have dubious relation to reality. 

The subpopulation thing is a real challenge, and it crops up all the time. One of the constant demands I have in my current job is summarizing complex systems that are used in a wide variety of environments in the most pithy way possible. How do you explain to that quintessential, "non-technical, executive-level" audience that, across a four-variable space, there are some places where the system works well, others where the performance is indistinguishable from the requirement, and a few where its disastrously bad in a few sentences, while being sure to include the reasons for this variation? 

The most egregious place I see su-populations creep up is when political analysts are attempting to summarize polling results. Even for high-quality polls, they typically get on the order of $n = 1,0000$ respondents. Which is fine, right until they start breaking out the cross-tabs and talking about things like "non-white Hispanic males between the ages of 30 and 49". My main gripe here isn't the sample sizes they have for these inferences, which are necessarily limited. Rather, my complaint is the way such things are discussed. I can't recall hearing even the most data-literate politics reporting (e.g., <a href = "https://fivethirtyeight.com/">538</a>) point out variation across sub-groups in opinion polls then identify which factors are driving the differences and which are a result of correlation across factors. A brief example:

Suppose Americans over 65 favored Policy X by a 56% to 44% margin compared to a 48 to 52 difference among Americans 65 and under. Seems a simple story:  Old people like Policy X! And a lot of times you see political reporting stop there. Or maybe they go one step further and note that, among Whites, the policy is favored 55% to 45, but non-whites are against it by a margin 42 to 58. Well, now we've got a conundrum, because $Age > 64$ is correlated with $Race != White$ in America. So was the initial reporting, about the difference in opinion being based on Age, correct? Incomplete? Useful? It's hard to say, and this is a relatively simple example. You can break these polling results down along a number of additional dimensions (gender, political affiliation, geographic location, etc.) to get a much richer picture of how different groups of people feel about things, but you almost never see this in popular discussions because the samples aren't big enough and the analysis is a bit more complex. It's very frustrating, and in my view, means we typically don't really understand what's going on in these cases. 

When I'm doing my own analyses, I try to bear this in mind. How many subpopulations am I really averaging over when I do my analysis? Are there more robust options (mixed models, etc.) for accounting for subpopulations? If I aggregate over subpopulations, am I distorting the results? 

Conventional wisdom is that the most common failure mode for a statistical analysis is starting from the basis that your data is Gaussian. This is incorrect, IMO. The most common failure is in not accounting for the complexity of the "top-level" distribution and trying to treat data from many subpopulations as if they're from a single, uniform population. Thinking properly about your data's distribution and allowing it to be adequately complex is both challenging and fundamental to doing sound analysis. 

#### Non-linearity

Things have interactions and they're not always smooth. 


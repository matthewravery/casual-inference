---
title: Data Science and Data Generation Processes
author: Matthew Avery
date: '2019-01-28'
slug: data-generation-processes
categories:
  - statistics
  - data generation
tags: []
description: ''
thumbnail: ''
---

I was talking about a curriculum for a new Data Science degree program, and the topic of experimental design came up. Design of Experiments (DOE) is classical subject area for statisticians, and the context of an applied statistics masters degree makes perfect sense, but in the context of data science, it seemed pretty out of place. I say that not because DOE isn't important but because I think its something "data science" doesn't often consider.

## Statistics vs. Data Science, Briefly
The difference between "data science" and "statistics" is <a href = "https://mixpanel.com/blog/2016/03/30/this-is-the-difference-between-statistics-and-data-science/">talked</a> <a href = "https://dataworks2018.testscience.org/wp-content/uploads/sites/8/2018/03/demystifying-data-science_Alyson-Wilson.pdf">to</a> <a href = "http://www2.isye.gatech.edu/~jeffwu/presentations/datascience.pdf">death</a>, and I don't want to get into that here. Instead, I'll just stick to my observation that while data collection and generation are <a href = "https://en.wikipedia.org/wiki/Statistics">regularly</a> <a href = "https://www.mathsisfun.com/definitions/statistics.html">mentioned</a> <a href = "https://www.stat.uci.edu/what-is-statistics/">when</a> <a href = "https://www.merriam-webster.com/dictionary/statistics">defining</a> "statistics", they <a href = "https://en.wikipedia.org/wiki/Data_science">rarely</a> <a href = "http://varianceexplained.org/r/ds-ml-ai/">come</a> <a href = "https://www.datarobot.com/wiki/data-science/">up</a> for "data science". 

I don't think this is unreasonable. Fisherian statistics is about deriving estimators and finding causal explanations. The field evolved in a time before computers, where data was typically difficult and costly to acquire. As a result, people spent a whole lot of time thinking about exactly which data points they should collect and exactly how much information they can extract. "Data Science", on the other hand, came of age in a computerized, connected world where "big data" was already a passe phrase. The question isn't so much, "How much data can I afford to collect?" as it is, "How can I process and learn from all this data that's been dropped on my head?"

## The Data Generation Process
Back when I was taking DOE courses in grad school, this was a straightforward concept. In fact, we took the time to write down mathematical models for what it looked like! We'd say something like:

$$y_{i} = \beta X_i + \epsilon_i$$

where the errors are iid Gaussian, etc., etc. If we knew we wanted to answer a specific questions (e.g., "Will Fertilizer A produce higher yields than Fertilizer B?"), we'd make sure we generated data with these two fertilizers, and we'd account for confounders. We'd note that our inference would only apply for the types of soils and environments where we did the testing, etc. These caveats and limitations are foregrounded because we often made conscious decisions to trade them away for a leaner test as part of the DOE process. 

Things don't tend to work that way in the world of data science. Instead of thinking about which data points you'd like to get, you build a data set by scraping, cleaning, and joining data from various sources. Often times, the questions you asked are informed by the information available to you. To a statistician, this looks like an <a href = "https://en.wikipedia.org/wiki/Observational_study">observational study</a>, which have a host of limitations. Fortunately for the data scientist, in many cases you don't have a sample but instead what amounts to a census. 

The breadth of available data is often a saving grace. Issues like sampling bias and out-of-scope inference go away when you can look at the whole distribution. But I fear this makes analyst complacent and unaware of pitfalls that are readily apparent when data points are consciously and carefully selected. And if it turns out that the data generation process changes, you're less likely to notice if you didn't go through the trouble to model it in the first place. 
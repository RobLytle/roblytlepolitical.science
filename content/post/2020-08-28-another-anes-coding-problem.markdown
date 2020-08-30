---
draft: false
title: "ANES Coding Problem: VCF0731"
subtitle: "Another ANES Goof-em-up"
slug: /anes-problems-too/
author: "Rob Lytle"
date: 2020-08-29
categories: ["political science", "public opinion", "ANES", "R"]
tags: ["R Markdown", "plot", "visualization", "rstats", "survey", "anes", "politics", "political science", "public opinion", "tidyverse", "tidy data"]
---



At this point, it's well established that the ANES CDF's [codebook](https://electionstudies.org/wp-content/uploads/2018/12/anes_timeseries_cdf_codebook_var.pdf) is [not to be trusted](/post/anes-problems/) ([I'm repeating "not to be trusted to include a second link!](http://gojiberries.io/2010/12/29/coding-issues-in-the-anes-cumulative-file/)). Recently, I stumbled across another example of incorrect coding in the [cumulative data file](https://electionstudies.org/data-center/anes-time-series-cumulative-data-file/), this time in `VCF0731` - Do you ever discuss politics with your family or friends?

The codebook reports 5 levels:

```
Do you ever discuss politics with your family or friends?

1. Yes
5. No

8. DK
9. NA

INAP. question not used
```

However, when we load the variable and examine the unique values:

```r
# pulling anes-cdf from a GitHub repository
cdf <- rio::import("https://github.com/RobLytle/intra-party-affect/raw/master/data/raw/cdf-raw-trim.rds")


unique(cdf$VCF0731)
```

```
## [1] NA  5  1  6  7
```

We see a completely different coding scheme. We are left adrift, wondering "What is `6`? What is `7`?" Do `1` and `5` _really_ mean "yes" and "no"?

We may never know. 

For a survey that costs several million dollars to conduct, you'd think we could expect a double-checked codebook (or at least some kind of version control to easily fix these things as they're identified). 










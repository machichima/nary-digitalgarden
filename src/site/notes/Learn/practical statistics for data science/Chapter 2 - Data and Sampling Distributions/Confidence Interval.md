---
{"dg-publish":true,"permalink":"/learn/practical-statistics-for-data-science/chapter-2-data-and-sampling-distributions/confidence-interval/","tags":["gardenEntry"]}
---


[[Learn/practical statistics for data science/practical statistics for data science\|practical statistics for data science]]
**Tags**:: #statistics/distribution 
**Links**:: ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=83&annotation=RC6E82ZT))
**Canvas**:: 

## Def

> 90% confidence interval: interval that encloses the central 90% of the bootstrap sampling distribution of a sample statistic ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=84&annotation=MX8CJ3U5))

- 包含 sample 中間 90% 的 entities 的區間

![Pasted image 20230421174629.png|300](/img/user/@attachments/Pasted%20image%2020230421174629.png)

> The bootstrap is a general tool that can be used to generate confidence intervals for most statistics, or model parameters ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=85&annotation=L6D97NBW))


> [!info] Interesting Point
> “What is the probability that the true value lies within a certain interval?” This is not really the question that a confidence interval answers, but it ends up being how most people interpret the answer. ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=85&annotation=FFE74R6T))

## Steps to get the bootstrap confidence interval

1. Draw a random sample of size n with replacement from the data (a resample). 
2. Record the statistic of interest for the resample. 
3. Repeat steps 1–2 many (R) times. (到這裡為 bootstrap 的步驟)
4. For an x% confidence interval, trim [(100-x) / 2]% of the R resample results from either end of the distribution. 
5. The trim points are the endpoints of an x% bootstrap confidence interval.

## Confidence level

> The percentage associated with the confidence interval is termed the level of confidence. The higher the level of confidence, the wider the interval. Also, the smaller the sample, the wider the interval (i.e., the greater the uncertainty) ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=86&annotation=PJFBDLV3))

- wider interval: (greater uncertainty)
	- higher level of confidence
	- smaller sample
	> the more confident you want to be, and the less data you have, the wider you must make the confidence interval to be sufficiently assured of capturing the true value. ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=86&annotation=6H83HJLT))


## Use case in Data Science

> how variable(多變的) a sample result might be ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=86&annotation=5V5DTUSL))

- The more data you have, the less variable a sample estimate will be.

> communicate the potential error in an estimate, and perhaps to learn whether a larger sample is needed ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=86&annotation=YD8M3ADI))


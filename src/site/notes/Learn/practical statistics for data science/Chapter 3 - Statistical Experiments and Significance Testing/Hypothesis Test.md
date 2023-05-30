---
{"dg-publish":true,"dg-path":"Practical Statistics for Data Science/Chapter 3 - Statistical Experiments and Significance Testing/Hypothesis Test.md","permalink":"/practical-statistics-for-data-science/chapter-3-statistical-experiments-and-significance-testing/hypothesis-test/","hide":true}
---


[[Learn/practical statistics for data science/practical statistics for data science\|practical statistics for data science]]
**Tags**:: #statistic/experiment  
**Links**:: [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Statistical Significance\|Statistical Significance]]
**Canvas**:: 

- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Hypothesis Test#Def\|Def]]
- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Hypothesis Test#Why do we need a hypothesis?\|Why do we need a hypothesis?]]
- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Hypothesis Test#用處\|用處]]
- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Hypothesis Test#使用\|使用]]
- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Hypothesis Test#One-Way and Two-Way Hypothesis Test\|One-Way and Two-Way Hypothesis Test]]
	- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Hypothesis Test#One-Way and Two-Way Hypothesis Test\|One-Way (One-Tail) Hypothesis Test]]
	- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Hypothesis Test#One-Way and Two-Way Hypothesis Test\|Two-Way (Two-Tail) Hypothesis Test]]
	- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Hypothesis Test#One-Way and Two-Way Hypothesis Test\|One-Way vs Two-Way]]


## Def

> Their purpose is to help you learn whether random chance might be responsible for an observed effect ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=111&annotation=SXBWNNLH))

> also called significance test

## Why do we need a hypothesis?

- 因為我們會低估 "自然的隨機變化"，會造成以下結果
	1. fail to anticipate (預測) extreme event (or so-called [[Learn/practical statistics for data science/Chapter 2 - Data and Sampling Distributions/Long-Tailed Distributions#^a75286\|black swans]] )
	2. misinterpret random events as having patterns of some significance
		- 將 random events 誤判成具有某種重要意義

> Statistical hypothesis testing was invented as a way to protect researchers from being fooled by random chance ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=111&annotation=GIWTPAJD))
> - 用來避免被 random events 糊弄


## 用處

> In a properly designed [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/AB Testing\|A/B test]], you collect data on treatments A and B in such a way that any observed difference between A and B must be due to either: 
> - Random chance in assignment of subjects 
> - A true difference between A and B ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=112&annotation=JIP8AJRE))

- A 和 B 間的不同可能是由
	- assign subjects 時的隨機性 或
	- A 和 B 間真正的差異

> A statistical hypothesis test is further analysis of an <u>A/B test, or any randomized experiment</u>, to assess ==whether random chance is a reasonable explanation== for the observed difference between groups A and B ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=112&annotation=TWFCD6IF))
> - 檢測 "隨機性" 是否為 randomized experiment 的良好解釋


## 使用

> assumes that the [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Null Hypothesis\|null hypothesis]] is true, creates a “null model” ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=114&annotation=EK8Y8CHJ))
> - tests whether the effect you observe is a reasonable outcome of that model
- 希望證明 [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Null Hypothesis\|null hypothesis]] 為 False
## One-Way and Two-Way Hypothesis Test

### One-Way (One-Tail) Hypothesis Test

> [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/AB Testing\|AB Testing]] 中較常用的方法

- A one-tail hypothesis test often fits the nature of A/B decision making, in which a decision is required and <u>one option is typically assigned “default”</u> status unless the other proves better
	- 我們只需要避免誤認為非 default 的效果較好 -> 只需要驗證其中一個 direction

> Often in an A/B test, you are testing a new option (say, B) against an established default option (A) ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=113&annotation=CQKE5NID))
> > presumption is that you will stick with the default option unless the new option proves itself definitively better ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=113&annotation=XBA9ERSI))
> - [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/AB Testing\|AB Testing]] 中，時常用來測試新的方法，若新方法並沒有更好，則會使用原先的方法

- extreme chance results in only one direction count toward the [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/p-Value\|p-value]].
	- 只有那些極端偶然結果偏向我們所關注的一側的情況才會計入p值的計算中

> [!important]
> [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/AB Testing\|AB testing]] 常用

### Two-Way (Two-Tail) Hypothesis Test

- 用於需要驗證兩個 direction 時
- extreme chance results in either direction count toward the [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/p-Value\|p-value]]

> [!important]
> 軟體給出的 default 結果大多都是使用 two-way hypothesis test


### One-Way vs Two-Way

> [!info]
> One-tail versus two-tail is a confusing subject, and not that relevant for data science, where the precision of [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/p-Value\|p-value]] calculations is not terribly important ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=113&annotation=RAYJ5C2X))


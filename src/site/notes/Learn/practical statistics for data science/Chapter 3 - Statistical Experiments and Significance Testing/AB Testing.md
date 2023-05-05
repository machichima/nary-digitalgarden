---
{"dg-publish":true,"permalink":"/learn/practical-statistics-for-data-science/chapter-3-statistical-experiments-and-significance-testing/ab-testing/","hide":true}
---

[[Learn/practical statistics for data science/practical statistics for data science\|practical statistics for data science]]
**Tags**:: #statistic/experiment
**Links**:: 
**Canvas**:: 

- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/AB Testing#Def\|Def]]
- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/AB Testing#Show the result\|Show the result]]
- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/AB Testing#Key terms\|Key terms]]
- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/AB Testing#Why have a control group\|Why have a control group]]
- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/AB Testing#常用的情景\|常用的情景]]
- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/AB Testing#比較多個 treatment 的結果\|比較多個 treatment 的結果]]

## Def

> 完整名稱為: A/B Testing

> an experiment with two groups to establish which of two treatments, products, procedures, or the like is superior ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=106&annotation=XUZBRLEQ))

> typical hypothesis is that a new treatment is better than the control. ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=106&annotation=24HIRA46))  
> 
> - 將新的 treatment 和 1)現有的 treatment or 2)沒有實施任何 treatment 進行比較
> - control 看下方 [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/AB Testing#^cf0aed\|key term: control]]  解釋

- Ex for A/B testing:
	- Testing two web headlines to determine which produces more clicks

## Show the result
- 常用的 test statistic (metric):
	- binary variable
- if the metric is a <u>discrete variable</u>:
	- results will be summed up in a 2x2 table
	- ![Pasted image 20230501230439.png|300](/img/user/@attachments/Pasted%20image%2020230501230439.png)
- If the metric is a <u>continuous variable</u>, the result in 2x2 table will be:
	- ![Pasted image 20230501230637.png](/img/user/@attachments/Pasted%20image%2020230501230637.png)

> [!important]
> 此資料中有 a small set of relatively high values (page views with conversions) and a huge number of 0-values (page views with no conversion)，分布不對稱 + 許多極端值，參考 [[Learn/practical statistics for data science/Chapter 1 - Exploratory Data Analysis/Estimates of Variability/Standard Deviation#Mean absolute deviation vs. Standard deviation\|Standard Deviation#Mean absolute deviation vs. Standard deviation]] ，在此情況中使用 Mean absolute deviation 較適當


## Key terms
- control
	- standard existing treatment, or no treatment (沒有實施任何 treatment)
- Subjects 
	- The items (web visitors, patients, etc.) that are exposed to treatments.
- Treatment
	- Something (drug, price, web headline) to which a subject is exposed.
- Treatment group 
	- A group of subjects exposed to a specific treatment.
- Control group 
{ #cf0aed}

	- A group of subjects exposed to no (or standard) treatment.
	- 控制變因: 除了 treatment 以外，其他狀態都一樣
- Randomization 
	- The process of randomly assigning subjects to treatments.
		- (將一 treatment 分配得隨機的 subject)
- Test statistic = metric
	- The metric used to measure the effect of the treatment.


## Why have a control group

> Without a control group, there is no assurance that “all other things are equal” ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=108&annotation=8CXCJ27Y))
> - 控制變因 (control) 會讓除了 treatment 以外的其他狀態都一樣

> If you simply make a comparison to “baseline” or prior experience, other factors, besides the treatment, might differ. ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=109&annotation=KNXCZAGY))


## 常用的情景

- A/B testing in data science is typically used in a "web context"
- Treatments might be the <u>design of a web page, the price of a product, the wording of a headline, or some other item</u>

> [!important] 
> if the experiment is expected to lead to a decision between treatment A and treatment B, a single <u>metric</u>, or test statistic, needs to be established <u>beforehand</u> ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=109&annotation=F4JIMH28))

- selecting a test statistic <u>after</u> the experiment would leads to =="researcher bias"==


## 比較多個 treatment 的結果
- 可以使用 [[Multi-Arm Bandit\|Multi-Arm Bandit]]

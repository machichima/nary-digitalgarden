---
{"dg-publish":true,"dg-path":"Practical Statistics for Data Science/Chapter 3 - Statistical Experiments and Significance Testing/Null Hypothesis.md","permalink":"/practical-statistics-for-data-science/chapter-3-statistical-experiments-and-significance-testing/null-hypothesis/","hide":true}
---


[[Learn/practical statistics for data science/practical statistics for data science\|practical statistics for data science]]
**Tags**:: #statistic/experiment  
**Links**:: 
**Canvas**:: 

- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Null Hypothesis#Def\|Def]]
- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Null Hypothesis#用處\|用處]]
	- [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Null Hypothesis#用處\|作法]]

## Def

> a baseline assumption that the treatments are equivalent, and any difference between the groups is due to chance ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=112&annotation=YR8HBBRA))
> - 假設 groups 間的差異皆來自隨機發生

- nothing special has happened, and any effect you observe is due to random chance

## 用處

> prove the null hypothesis wrong and show that the outcomes for groups A and B are more different than what chance might produce ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=112&annotation=DB7JXSMW))
> - 我們希望證明 null hypothesis 為 False，以顯示 A 和 B 之間試真的有差異，而不是因為隨機抽樣而造成的差異

> The nature of the null hypothesis determines the structure of the [[Learn/practical statistics for data science/Chapter 3 - Statistical Experiments and Significance Testing/Hypothesis Test\|hypothesis test]] ([pdf](zotero://open-pdf/library/items/XC4XLTB4?page=113&annotation=3UYBM6U7))

### 作法
- 其中一種作法為 ==resampling permutation procedure==，稱為 null model
	1. mix the results from group A and B together
	2. repeatly resample two groups from it (重複的從 1. 中 resample 出兩個 group)
	3. observe how often we get a difference between the two groups as extreme as the observed difference (觀察得到極端差異的頻率)
- 如果以上方法得到極端值的頻率也很高，表示 null hypothesis 成立，gruop A and B 之間的差異皆來自隨機發生

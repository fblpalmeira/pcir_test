# pcir - Potential for Conflict Index in R

## Introduction

I plan to develop a package called ‘Potential for Conflict Index - PCI’, which is a descriptive statistical method used to enhance the understanding of outcomes in human dimensions research developed by Manfredo et al. (2003). The package will equip users with the tools required for calculating, comparing, and graphing the potential for conflict. The concepts of consensus and disagreement/conflict hold relevance across various fields, including economics, political science, psychology, sociology, and natural resources. It is worth noting that although PCI can currently be computed using software such as Excel, SPSS, and SAS, there is no dedicated R package available for conducting this specific analysis. 

Additional information: [rOpenSci Champions Program](https://ropensci.org/champions/)
                        [Introducing rOpenSci Champions - Cohort 2023-2024](https://ropensci.org/blog/2024/02/15/champions-program-champions-2024/)
                        [Potential For Conflict Index](https://sites.warnercnr.colostate.edu/jerryv/potential-conflict-index/)

## Methods

### Theoretical approach

The PCI indicates the ratio of scoring on either side of the center point on a rating scale. This might include the center points “neutral”, “neither agree nor disagree”, “neither acceptable nor unacceptable”, or “neither support nor oppose.” We assume that the greatest possibility for conflict occurs when there is a bimodal distribution between the two extreme values of the response scale (e.g., 50% strongly support, 50% strongly oppose, 0% neutral). In that case the index attains its highest possible value of 1. A distribution with 100% on one side of the neutral point will yield a PCI of 0 (i.e., no conflict). 

The PCI formula requires a response scale in which there is a neutral center point with an equal number of response options on either side. Numerical ratings must be assigned in ordinal fashion with the center point receiving a value of 0. 

In the examples presented in this package, the univariate scale was:

- (3) Highly Acceptable,
- (2) Moderately Acceptable,
- (1) Slightly Acceptable,
- (0) Neither Acceptable nor Unacceptable,
- (−1) Slightly Unacceptable,
- (−2) Moderately Unacceptable,
- (−3) Highly Unacceptable.

The index is computed using a variable’s frequency distribution following the formula: 

<img src="https://github.com/fblpalmeira/pcir/blob/main/images/Fig1a_formula.png" width = "300px"> 

where: 
- PCI = Potential for Conflict Index 
- Xa = an individual’s “acceptable” (e.g., 1, 2, or 3) score 
- na = all individuals with acceptable scores 
- Xu = an individual’s “unacceptable” (e.g., −1, −2, or −3) score 
- nu = all individuals with unacceptable scores

<img src="https://github.com/fblpalmeira/pcir/blob/main/images/Fig1b_formula2.png" width = "200px">  

- Z = the maximum possible sum of all scores = n × extreme score (e.g., Z = 3n),
where n = total number of subjects

### Pratical example: Univariate model

This study used in the example assessed wildlife value orientations, management action acceptability, and wildlife-associated recreation behaviors in six western states in US. We used data for the state of Alaska on a series of items dealing with bear management. Subjects were then asked to rate the acceptability of five different management responses (e.g., leave the bear alone, capture and destroy the bear). 

**Table 1.** Alaskan Respondents’ Ratings of Acceptability of “Leave the Bear Alone”.

| Response scale |  Scoring  | Frequency  |  Percent | 
| -------------- | --------- | ---------- | -------- | 
| Highly unacceptable | -3 | 26 | 8 | 
| Moderately unacceptable | -2 | 31 | 9 |
| Slightly unacceptable | -1 | 20 | 6 |
| Neutral | 0 | 15 | 4 |
| Slightly acceptable | 1 | 52 | 15 |
| Moderately acceptable | 2 | 90 | 26 |
| Highly acceptable | 3 | 108 | 32 |
| Total | - | 342 | 100 |

<img src="https://github.com/fblpalmeira/pcir/blob/main/images/Fig1c_formula.png" width = "100px"> (|-3| * 26) + (|-2| * 31) + (|-1| * 20) = 160

<img src="https://github.com/fblpalmeira/pcir/blob/main/images/Fig1d_formula.png" width = "150px"> (3 * 108) + (2 * 90) + (1 * 52) = 556
 
- Xt = 160 + 556 = 716 
- n = total number of subjects = 342 
- PCI for “Leave Bear Alone” = [ 1 - |556/716 - 160/716| ] * 716 / (3 * 342) = 0.31

**Table 2.**  “Potential for Conflict Indices” and Mean Scores for Alaskan Respondents’ Ratings of Acceptability of Bear Management Actions.

| Management action |  Conflict index  | Mean score(1)  |
| ----------------- | ---------------- | -------------- |
| Leave the bear alone | 0.31 | 1.16 | 
| Capture and destroy the bear | 0.39 | -0.91 |
| Capture and relocate the bear to a new location in hopes that it will NOT return | 0.18 | 1.54 | 
| Use techniques (for example, loud noises or rubber bullets) designed to frighten the bear away | 0.10 | 2.02 |
| Educate people who live near bear habitat on how to avoid problems with bears  | 0.04 | 2.62 | 

(1) The following scoring was used in the computation of means for these variables: “Highly unacceptable” = −3, “Moderately unacceptable” = −2, “Slightly unacceptable” = −1, “Neither” = 0, “Slightly acceptable” = 1, “Moderately acceptable” = 2, and “Highly
acceptable” = 3 (see Table 1).

<img src="https://github.com/fblpalmeira/pcir/blob/main/images/Fig2_bubble_graph.png">  

**Figure 1.** Univariate measures using the PCI and the graphic technique: Alaskans’ ratings of acceptability of bear management actions. Numbers listed for each bubble in the graph represent the Potential for Conflict Index (PCI). 

## References

Manfredo, M., Vaske, J., & Teel, T. (2003). [The potential for conflict index: A graphic approach to practical significance of human dimensions research](https://www.tandfonline.com/doi/abs/10.1080/10871200304310). Human Dimensions of Wildlife, 8(3), 219-228.

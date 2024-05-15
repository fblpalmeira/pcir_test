# pcir - Potential for Conflict Index in R

## Introduction

I plan to develop a package called [‘Potential for Conflict Index - PCI’](https://sites.warnercnr.colostate.edu/jerryv/potential-conflict-index/), which is a descriptive statistical method used to enhance the understanding of outcomes in human dimensions research developed by [Manfredo et al. (2003)](https://www.tandfonline.com/doi/abs/10.1080/10871200304310). The package will equip users with the tools required for calculating, comparing, and graphing the potential for conflict. The concepts of consensus and disagreement/conflict hold relevance across various fields, including economics, political science, psychology, sociology, and natural resources. It is worth noting that although PCI can currently be computed using software such as Excel, SPSS, and SAS, there is no dedicated R package available for conducting this specific analysis. 

Additional information: 
- [rOpenSci Champions Program](https://ropensci.org/champions/)
- [Introducing rOpenSci Champions - Cohort 2023-2024](https://ropensci.org/blog/2024/02/15/champions-program-champions-2024/)
                        
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

This study used in the example assessed wildlife value orientations, management action acceptability, and wildlife-associated recreation behaviors in six western states in US. We used data for the state of Alaska on a series of items dealing with bear management. Subjects were then asked to rate the acceptability of five different management responses (e.g., leave the bear alone, capture and destroy the bear)(Table 1). 

**Table 1.** Alaskan respondents’ ratings of acceptability of “Leave the bear alone”.

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

<img src="https://github.com/fblpalmeira/pcir/blob/main/images/Fig1e_formulab.png" width = "400px"> 

<img src="https://github.com/fblpalmeira/pcir/blob/main/images/Fig1f_formulab.png" width = "400px"> 
 
- Xt = 160 + 556 = 716 
- n = total number of subjects = 342 
- PCI for “Leave Bear Alone” = [ 1 - |556 / 716 - 160 / 716| ] * 716 / (3 * 342) = 0.31

The potential for conflict index for “leave the bear alone” was approximately 0.31 (Table 2). Similar computations for the other four management actions varied between 0.04 to 0.39.

**Table 2.** Potential for conflict indices and mean scores for Alaskan respondents’ ratings of acceptability of bear management actions.

| Management action |  Conflict index  | Mean score(1)  |
| ----------------- | ---------------- | -------------- |
| Leave the bear alone | 0.31 | 1.16 | 
| Capture and destroy the bear | 0.39 | -0.91 |
| Capture and relocate the bear to a new location in hopes that it will NOT return | 0.18 | 1.54 | 
| Use techniques (for example, loud noises or rubber bullets) designed to frighten the bear away | 0.10 | 2.02 |
| Educate people who live near bear habitat on how to avoid problems with bears  | 0.04 | 2.62 | 

(1) The following scoring was used in the computation of means for these variables: “Highly unacceptable” = −3, “Moderately unacceptable” = −2, “Slightly unacceptable” = −1, “Neither” = 0, “Slightly acceptable” = 1, “Moderately acceptable” = 2, and “Highly
acceptable” = 3 (see Table 1).

To enhance the ease of understanding, Figure 1 displays the conflict indices and variable means graphically.

<img src="https://github.com/fblpalmeira/pcir/blob/main/images/Fig2_bubble_graph.png">  

**Figure 1.** Univariate measures using the PCI and the graphic technique: Alaskans’ ratings of acceptability of bear management actions. Numbers listed for each bubble in the graph represent the Potential for Conflict Index (PCI). 

### Script in R

Materials:
- [Script `.R`]
- [Data `.xlsx`]
- [Table 1 `.xlsx`](https://github.com/fblpalmeira/pcir/blob/main/data/Table1.xlsx)
- [Table 2 `.xlsx`](https://github.com/fblpalmeira/pcir/blob/main/data/Table2b.xlsx)
- [Figure 1 `.png`](https://github.com/fblpalmeira/pcir/blob/main/data/output_pci.png)
  
Stages of the 'pcir' package:
1. Read the data input from the interviews;
2. Count the frequencies of responses within each question / Write [(Table 1)](https://github.com/fblpalmeira/pcir/blob/main/data/Table1.xlsx);
3. Calculate the potential conflict index for each question / Write [(Table 2)](https://github.com/fblpalmeira/pcir/blob/main/data/Table2.xlsx);
4. Create a bubble chart using the indices / Save [(Figure 1)](https://github.com/fblpalmeira/pcir/blob/main/data/output_pci.png).

<img src="https://github.com/fblpalmeira/pcir/blob/main/images/diagrammer_pcir.png">     

**Figure 2.** Workflow of the 'pcir' package.

### Data input

Read the respondents’ ratings:

``` r

.
.
.

```

### Formula

Calculate the PCI indices:

``` r

.
.
.


```

### Output

Create a bubble graph to illustrate the potential conflict indices:

``` r

###################################################
# Part 4: Output                                  #
#                                                 #
# Create a bubble graph to illustrate the indices #
###################################################

y3 <- readxl::read_excel("Table2b.xlsx", na = " ")
head(y3)

y3 <- dplyr::mutate_at(y3, c('PCI', 'Mean'), as.numeric)
head(y3)
summary(y3)

y3$Management <- factor(y3$Management, levels = c("Leave bear alone",
                                                  "Capture and destroy",
                                                  "Capture and relocate",
                                                  "Frighten the bear",
                                                  "Educate about bears"))

png(file="output_pci.jpeg", width = 500, height = 500)
library(ggplot2)
p <- ggplot(y3, aes(x = Management, y = Mean, size = PCI)) +
     geom_point(alpha=0.25) +
     geom_text(aes(label = after_stat(y3$PCI)),
                   nudge_y = 0.35, nudge_x = 0.1, size = 5) +
     ylab("Action acceptability") + xlab("") + 
     ylim (-3,3) +
     scale_size_area(max_size = 14) +
     theme_bw() +
     theme (panel.grid.major.y = element_blank(), 
            panel.grid.minor.y = element_blank()) + 
            theme (panel.grid.major.x = element_blank(), 
            panel.grid.minor.x = element_blank()) +
     theme (axis.title.x=element_text(size=16)) +
     theme (axis.title.y=element_text(size=16)) +
     theme (axis.text.x=element_text(size=14, angle = 45, vjust = 1, hjust = 1)) +
     theme (axis.text.y=element_text(size=14)) +
     theme (legend.key.size = unit(1, 'cm'),
            legend.key.height = unit(1, 'cm'),
            legend.key.width = unit(1, 'cm'),
            legend.title = element_text(size=16), 
            legend.text = element_text(size=14))
p
dev.off()

```

<img src="https://github.com/fblpalmeira/pcir/blob/main/data/output_pci.png">     

**Figure 3.** Bubble graph illustranting the potencial conflict indices.

## References

Manfredo, M., Vaske, J., & Teel, T. (2003). [The potential for conflict index: A graphic approach to practical significance of human dimensions research](https://www.tandfonline.com/doi/abs/10.1080/10871200304310). Human Dimensions of Wildlife, 8(3), 219-228.

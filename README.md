pcir: Potential for Conflict Index in R
================

[![R-CMD-check](https://github.com/fblpalmeira/pcir/main/R-CMD-check.yaml/badge.svg)](https://github.com/fblpalmeira/pcir)

`pcir` is an R package designed to help researchers and practitioners
calculate, compare, and visualize the Potential for Conflict Index
(PCI). The PCI is a descriptive statistical method used to enhance
understanding of outcomes in human dimensions research. It is relevant
across fields such as economics, political science, psychology,
sociology, and natural resources.

## Features

- **`counting()`** summarize data by calculating counts, percentages,
  means, and standard deviations.

- **`pci()`** compute the Potential for Conflict Index from summary
  data.

- **`bubble()`** visualize PCI results using a bubble plot.

## Installation

You can install the development version of `pcir` directly from GitHub:

``` r
# Uncomment the line below if devtools is not installed
# install.packages("devtools")
devtools::install_github("fblpalmeira/pcir")
```

## Usage

Load the Package:

``` r
library(pcir)
```

Example dataset:

``` r
df1 <- data.frame(
  A = c(-1, 2, 2, 3, -1),
  B = c(-1, 2, 3, -1, 2),
  C = c(1, 2, -2, 3, -1),
  D = c(3, 2, 1, -1, -2),
  E = c(2, 3, 1, -1, -3)
  )
```

Counting function:

``` r
# The counting function summarizes data by counts, percentages, means, and standard deviations
df_count <- counting(df1)
df_count
```

PCI function:

``` r
# The pci function calculates the Potential for Conflict Index (PCI)
df_pci <- pci(df_count)
df_pci
```

Bubble plot function:

``` r
# The bubble function creates a bubble plot to visualize the PCI results
bubble_plot <- bubble(df_pci)
bubble_plot # Display the bubble plot
```

## License

This package is licensed under the MIT License. See the LICENSE file for
more details.

## Contact

For any questions or inquiries, please contact Francesca Palmeira at
<francesca@alumni.usp.br>.

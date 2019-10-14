---
title: "Gapminder analysis"
author: "Weili"
date: "10/14/2019"
output:
  html_document:
    keep_md: yes
    fig_caption: yes
    toc: yes
    
---

#Introduction

Here is my first rmd document

#Let's embed some r code

we'll write an R chunck that loads the tidyverse package and reads in the Gapminder data set from the data subdirectory of the project

CMD+OPT+i quick keys to insert new r chunck

```r
library(tidyverse, quietly = TRUE)
```

```
## ── Attaching packages ────────────────────────── tidyverse 1.2.1 ──
```

```
## ✔ ggplot2 3.2.1     ✔ purrr   0.3.2
## ✔ tibble  2.1.3     ✔ dplyr   0.8.3
## ✔ tidyr   1.0.0     ✔ stringr 1.4.0
## ✔ readr   1.3.1     ✔ forcats 0.4.0
```

```
## ── Conflicts ───────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
```

```r
gm <- read_csv("Data/gapminder.csv")
```

```
## Parsed with column specification:
## cols(
##   country = col_character(),
##   continent = col_character(),
##   year = col_double(),
##   lifeExp = col_double(),
##   pop = col_double(),
##   gdpPercap = col_double()
## )
```
#Investigate gm data

Let's take a look at the gm


```r
head(gm)
```

```
## # A tibble: 6 x 6
##   country     continent  year lifeExp      pop gdpPercap
##   <chr>       <chr>     <dbl>   <dbl>    <dbl>     <dbl>
## 1 Afghanistan Asia       1952    28.8  8425333      779.
## 2 Afghanistan Asia       1957    30.3  9240934      821.
## 3 Afghanistan Asia       1962    32.0 10267083      853.
## 4 Afghanistan Asia       1967    34.0 11537966      836.
## 5 Afghanistan Asia       1972    36.1 13079460      740.
## 6 Afghanistan Asia       1977    38.4 14880372      786.
```
#our first plot
Show gdp per captia on x and life expectancy on y


```r
ggplot(gm, aes(x=gdpPercap, y= lifeExp)) + 
  geom_point(aes(col = continent)) + 
  scale_x_log10()
```

![Life Expectancy v.GDP with color](rwithdata_files/figure-html/unnamed-chunk-3-1.png)
# Possible chunk options

Options include:
- echo (TRUE by default) whether to include code in output
- results
  - hide will hide the results
  - hold will hold results until end of r chunk
- include (True by default) if FALSE then the code will not be run
-fig.width, fig.height set the figure dimensions int the output
-cache (FALSE by default) if TRUE saves the result from r chunk

#Table in RMarkdown

See some data using head

```r
head(gm)
```

```
## # A tibble: 6 x 6
##   country     continent  year lifeExp      pop gdpPercap
##   <chr>       <chr>     <dbl>   <dbl>    <dbl>     <dbl>
## 1 Afghanistan Asia       1952    28.8  8425333      779.
## 2 Afghanistan Asia       1957    30.3  9240934      821.
## 3 Afghanistan Asia       1962    32.0 10267083      853.
## 4 Afghanistan Asia       1967    34.0 11537966      836.
## 5 Afghanistan Asia       1972    36.1 13079460      740.
## 6 Afghanistan Asia       1977    38.4 14880372      786.
```
now head function as a nicely formatted table

```r
library(knitr)
kable(head(gm))
```



country       continent    year   lifeExp        pop   gdpPercap
------------  ----------  -----  --------  ---------  ----------
Afghanistan   Asia         1952    28.801    8425333    779.4453
Afghanistan   Asia         1957    30.332    9240934    820.8530
Afghanistan   Asia         1962    31.997   10267083    853.1007
Afghanistan   Asia         1967    34.020   11537966    836.1971
Afghanistan   Asia         1972    36.088   13079460    739.9811
Afghanistan   Asia         1977    38.438   14880372    786.1134

If you like tables, look at **gt** table package

! sh: pdflatex: command not found


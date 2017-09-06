Problem Set 1 R exercises
================
EJ Arce
August 30, 2017

``` r
knitr::opts_chunk$set(echo = TRUE)
library(tidyverse)
```

    ## Loading tidyverse: ggplot2
    ## Loading tidyverse: tibble
    ## Loading tidyverse: tidyr
    ## Loading tidyverse: readr
    ## Loading tidyverse: purrr
    ## Loading tidyverse: dplyr

    ## Conflicts with tidy packages ----------------------------------------------

    ## filter(): dplyr, stats
    ## lag():    dplyr, stats

### Exercise 1.43

``` r
# To run a simulation on the outcome of rolling 2 dice, I will sample two dice
# separately and then make a data frame out of both samples. Meanwhile, I will
# mutate a new variable displaying the sum of both rolls.
set.seed(23)
diceRoll1 <- sample(1:6, 10000, replace = TRUE)
diceRoll2 <- sample(1:6, 10000, replace = TRUE)
diceRolls <- data.frame(diceRoll1, diceRoll2) %>%
  mutate(sum = diceRoll1 + diceRoll2)

# I will now calculate the total number of rolls out of 10000 with a sum of 
# at least 8. This command returns the number of rolls with a sum of at least
# 8 as TRUE, and rolls with a sum lower than 8 as false.
count(diceRolls, sum >= 8)
```

    ## # A tibble: 2 × 2
    ##   `sum >= 8`     n
    ##        <lgl> <int>
    ## 1      FALSE  5780
    ## 2       TRUE  4220

The count shows that the probability of rolling two dice with a sum of at least 8 is .4220.

### Exercise 1.44

``` r
# We are now using a four sided die and rolling it 5 times.
set.seed(30)
tetra1 <- sample(1:4, 10000, replace = TRUE)
tetra2 <- sample(1:4, 10000, replace = TRUE)
tetra3 <- sample(1:4, 10000, replace = TRUE)
tetra4 <- sample(1:4, 10000, replace = TRUE)
tetra5 <- sample(1:4, 10000, replace = TRUE)
tetraRolls <- data.frame(tetra1, tetra2, tetra3, tetra4, tetra5)
# Now the count command will count the number of rows in the dataset where at
# least one 2 is rolled
count(tetraRolls, tetra1==2|tetra2==2|tetra3==2|tetra4==2|tetra5==2)
```

    ## # A tibble: 2 × 2
    ##   `tetra1 == 2 | tetra2 == 2 | tetra3 ==...`     n
    ##                                        <lgl> <int>
    ## 1                                      FALSE  2368
    ## 2                                       TRUE  7632

The count shows us that the probability of rolling at least one 2 is .7632.

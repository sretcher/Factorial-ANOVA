## Factorial Analysis of Variance

A vegetation height of greater than 30 centimeters on a highway right-of-way is genereally considered a safety hazard to drivers. In the Landscape Ecology Journal, a study was conducted to find the effects of mowing frequency and mowing height on vegetation height along highway right-of-ways. A sample of 36 plots of land along a highway right-of-way were selected for the study and each were given a random mowing frequency/height treatment. Mowing frequency was set at three levels: once, twice, or three times per year and mowing height of equipment was also set at three levels: 5, 10, or 20 centimeters. At the end of the year, the vegetation height was recorded for each plot. We will conduct a 3x3 Factorial Anova to determine the effects of our two factors on the response variable and whether an interaction exists between our factors. 

The following code loads the libraries and our data. When loading the data, our independent variables mowing height (`MowHT`) and mowing frequency (`MowFreq`) are parsed as continous variables. We need these variables to be factors since factorial anova requires one continous variable and two or more categorical variables. Using `col_types`, we make sure `readr` converts these variables to the correct type.
```
library(tidyverse)
library(gplots)

mow <- read_csv(file = "MOW.csv",col_names = TRUE, col_type=cols(
  MowHT = col_factor(),
  MowFreq = col_factor()
))
```

When looking at our data, notice that `readr` automatically places our data in a tibble and our independent variables have the correct type. We also see that our data has 36 observations (plots of land) and the values of our independent variables and our response variable, vegetation height (`VegHT`), are recorded for each observation. 
```
mow
# A tibble: 36 x 3
#   MowHT MowFreq VegHT
#   <fct> <fct>   <dbl>
# 1   5     1        19.3
# 2   5     1        17.3
# 3   5     1        16.7
# 4   5     1        15  
# 5   10    1        16  
# 6   10    1        15.6
# 7   10    1        16.9
# 8   10    1        15  
# 9   20    1        16.7
# 10  20    1        17.9
# ... with 26 more rows
```

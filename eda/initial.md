---
title: "Initial EDA"
author: "Devi Annanda"
date: "8/4/2021"
output: 
  html_document:
    keep_md: TRUE
---



## Load Libraries


```r
# load libraries

# data wrangling
library(tidyverse)
library(here)
library(glue)
```


## Load the data


```r
# load product and districts data
products <- read_csv(here("data", "products_info.csv"))
districts <- read_csv(here("data", "districts_info.csv"))

# load engagement data

# read csv with filename as column
filename <- function(x) read_csv(x, col_types = cols(.default = "c")) %>% 
  mutate(district_id = gsub(".csv", "", basename(x)))

# load engagement as one dataframe
engagement <-
    list.files(path = here("data/engagement_data"), 
               pattern = "*.csv",
               full.names = TRUE) %>% 
  map_df(filename)

## reference:
## https://stackoverflow.com/questions/44462494/include-csv-filename-when-reading-data-into-r-using-list-files
```








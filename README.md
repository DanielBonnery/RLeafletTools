---
title: "`RLeafletTools`"
author: "dbonnery"
date: "2021-02-03"
output: 
  html_document:
    keep_md: true
always_allow_html: yes
---

# `RLeafletTools` 

## Install

```r
devtools::install_github("DanielBonnery/RLeafletTools")
```

## Demonstration

```r
library(RLeafletTools)
library(leaflet)
library(dplyr)
data("breweries91",package="leaflet")
breweries91$goodbeer<-sample(as.factor(c("terrific","marvelous","culparterretaping")),nrow(breweries91),replace=T)
lf<-leaflet(breweries91)%>%
  addTiles()%>%addpiechartclustermarkers2(.data=breweries91,.colors=c("red","green","blue"),group="goodbeer")
lf
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-1-1.png)


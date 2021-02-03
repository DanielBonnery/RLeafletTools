`RLeafletTools`
================
Daniel Bonnéry
2021-02-03

`RLeafletTools`
===============

Install
-------

``` r
devtools::install_github("DanielBonnery/RLeafletTools")
```

Main function.
--------------

The function `addpiechartclustermarkers2` creates pie chart cluster markers in leaflet as in <https://danielbonnery.github.io/RLeafletTools/>.

Demonstration
-------------

``` r
library(RLeafletTools)
library(leaflet)
library(dplyr)
data("breweries91",package="leaflet")
breweries91$goodbeer<-sample(as.factor(c("terrific","marvelous","culparterretaping")),nrow(breweries91),replace=T)
lf<-leaflet(breweries91)%>%
  addTiles()%>%addpiechartclustermarkers2(.data=breweries91,.colors=c("red","green","blue"),group="goodbeer")
lf
```

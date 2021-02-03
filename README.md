---
output: github_document
---

# Tile

`RLeafletTools` 

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

```
## PhantomJS not found. You can install it with webshot::install_phantomjs(). If it is installed, please make sure the phantomjs executable can be found via the PATH variable.
```

```
## Warning in normalizePath(f2): path[1]="webshot239e744898e1.png": Lo fichièr o lo
## repertòri existís pas
```

```
## Warning in file(con, "rb"): cannot open file 'webshot239e744898e1.png': Lo fichièr
## o lo repertòri existís pas
```

```
## Error in file(con, "rb"): cannot open the connection
```


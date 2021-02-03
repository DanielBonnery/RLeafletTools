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

<!--html_preserve--><div id="htmlwidget-31a267b86573708cebcb" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-31a267b86573708cebcb">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["//{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":1,"detectRetina":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addAwesomeMarkers","args":[[49.71979,49.884051,49.502098,49.274716,49.861905,49.794334,49.701477,49.067436,49.070292,49.77994,49.060542,49.561804,49.595108,49.602554,49.72581,49.7202,49.644533,49.645651,49.615866,49.50683,48.900742,49.707329,49.884229,49.677827,49.450083,49.710838,49.276265,49.554706,49.882777,49.727998,49.737703,49.755953],[10.889217,11.228988,10.416021,10.928096,11.291932,11.509409,11.163238,10.34418,10.316987,11.186931,10.965571,11.368508,11.009011,11.005049,11.059662,11.056749,11.252699,11.248618,10.630027,11.428338,11.029479,10.806113,11.267583,11.252911,11.308721,11.172792,10.685605,11.22997,11.129541,11.202701,11.223148,11.175664],{"icon":"ios-close","markerColor":["red","green","blue","green","green","red","green","blue","green","green","blue","blue","blue","red","green","red","red","green","red","blue","blue","blue","red","red","red","blue","blue","green","blue","blue","red","red"],"iconColor":"black","spin":false,"squareMarker":false,"iconRotate":0,"font":"monospace","prefix":"ion"},null,"goodbeer",{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},null,null,{"showCoverageOnHover":true,"zoomToBoundsOnClick":true,"spiderfyOnMaxZoom":true,"removeOutsideVisibleBounds":true,"spiderLegPolylineOptions":{"weight":1.5,"color":"#222","opacity":0.5},"freezeAtZoom":false,"iconCreateFunction":"function(cluster) {\n      const groups= ['culparterretaping','marvelous','terrific'];\n      const colors= {\n      groups: ['red','green','blue'],\n      center:'#ddd',\n      text:'black'\n      };\n      const markers= cluster.getAllChildMarkers();\n      \n      const proportions= groups.map(group => markers.filter(marker => marker.options.label === group).length / markers.length);\n      function sum(arr, first= 0, last) {\n      return arr.slice(first, last).reduce((total, curr) => total+curr, 0);\n      }\n      const cumulativeProportions= proportions.map((val, i, arr) => sum(arr, 0, i+1));\n      cumulativeProportions.unshift(0);\n      \n      const widthgm = 2*Math.sqrt(markers.length);\n      const radiusgm= 15+widthgm/2;\n      const width = 2*Math.min(Math.sqrt(markers.length),5);\n      const radius= 15+1.2*Math.log(markers.length)/Math.log(10)+width/2;\n      \n      const arcs= cumulativeProportions.map((prop, i) => { return {\n      x   :  radius*Math.sin(2*Math.PI*prop),\n      y   : -radius*Math.cos(2*Math.PI*prop),\n      long: proportions[i-1] >.5 ? 1 : 0\n      }});\n      const paths= proportions.map((prop, i) => {\n      if (prop === 0) return '';\n      else if (prop === 1) return `<circle cx='0' cy='0' r='${radius}' fill='none' stroke='${colors.groups[i]}' stroke-width='${width}' stroke-alignment='center' stroke-linecap='butt' />`;\n      else return `<path d='M ${arcs[i].x} ${arcs[i].y} A ${radius} ${radius} 0 ${arcs[i+1].long} 1 ${arcs[i+1].x} ${arcs[i+1].y}' fill='none' stroke='${colors.groups[i]}' stroke-width='${width}' stroke-alignment='center' stroke-linecap='butt' />`\n      });\n      \n      return new L.DivIcon({\n      html: `\n      <svg width='60' height='60' viewBox='-30 -30 60 60' style='width: 60px; height: 60px; position: relative; top: -24px; left: -24px;' >\n      <circle cx='0' cy='0' r='${radius}' stroke='none' fill='${colors.center}' />\n      <text x='0' y='0' dominant-baseline='central' text-anchor='middle' fill='${colors.text}' font-size='15'>${markers.length}<\/text>\n      ${paths.join('')}\n      <\/svg>\n      `,\n      className: 'marker-cluster'\n      });\n}"},["toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto"],["culparterretaping","marvelous","terrific","marvelous","marvelous","culparterretaping","marvelous","terrific","marvelous","marvelous","terrific","terrific","terrific","culparterretaping","marvelous","culparterretaping","culparterretaping","marvelous","culparterretaping","terrific","terrific","terrific","culparterretaping","culparterretaping","culparterretaping","terrific","terrific","marvelous","terrific","terrific","culparterretaping","culparterretaping"],{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]}],"limits":{"lat":[48.900742,49.884229],"lng":[10.316987,11.509409]}},"evals":["calls.1.args.8.iconCreateFunction"],"jsHooks":[]}</script><!--/html_preserve-->


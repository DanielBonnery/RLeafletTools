---
title: "`RLeafletTools`"
author: "dbonnery"
date: "2021-02-03"
output: 
  html_document:
    keep_md: true
always_allow_html: yes
---


 <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">

<!-- Begin Jekyll SEO tag v2.7.1 -->
<title>RLeafletTools</title>
<meta name="generator" content="Jekyll v3.9.0" />
<meta property="og:title" content="RLeafletTools" />


		
	<!-- Require Leaflet -->
	<!-- Load leaflet for R-->

<script src="https://rstudio.github.io/leaflet/libs/jquery/jquery.min.js"></script>
<meta name="viewport" content="width=device-width, initial-scale=1" />
<link href="https://rstudio.github.io/leaflet/libs/bootstrap/css/flatly.min.css" rel="stylesheet" />
<script src="https://rstudio.github.io/leaflet/libs/bootstrap/js/bootstrap.min.js"></script>
<script src="https://rstudio.github.io/leaflet/libs/bootstrap/shim/html5shiv.min.js"></script>
<script src="https://rstudio.github.io/leaflet/libs/bootstrap/shim/respond.min.js"></script>
<script src="https://rstudio.github.io/leaflet/libs/navigation/tabsets.js"></script>
<link href="https://rstudio.github.io/leaflet/libs/highlightjs/default.css" rel="stylesheet" />
<script src="https://rstudio.github.io/leaflet/libs/highlightjs/highlight.js"></script>
<script src="https://rstudio.github.io/leaflet/libs/htmlwidgets/htmlwidgets.js"></script>
<link href="https://rstudio.github.io/leaflet/libs/leaflet/leaflet.css" rel="stylesheet" />
<script src="https://rstudio.github.io/leaflet/libs/leaflet/leaflet.js"></script>
<link href="https://rstudio.github.io/leaflet/libs/leafletfix/leafletfix.css" rel="stylesheet" />
<script src="https://rstudio.github.io/leaflet/libs/Proj4Leaflet/proj4-compressed.js"></script>
<script src="https://rstudio.github.io/leaflet/libs/Proj4Leaflet/proj4leaflet.js"></script>
<link href="https://rstudio.github.io/leaflet/libs/rstudio_leaflet/rstudio_leaflet.css" rel="stylesheet" />
<script src="https://rstudio.github.io/leaflet/libs/leaflet-binding/leaflet.js"></script>
<link href="https://rstudio.github.io/leaflet/libs/leaflet-awesomemarkers/leaflet.awesome-markers.css" rel="stylesheet" />
<script src="https://rstudio.github.io/leaflet/libs/leaflet-awesomemarkers/leaflet.awesome-markers.min.js"></script>
<link href="https://rstudio.github.io/leaflet/libs/ionicons/ionicons.min.css" rel="stylesheet" />
<link href="https://rstudio.github.io/leaflet/libs/leaflet-markercluster/MarkerCluster.css" rel="stylesheet" />
<link href="https://rstudio.github.io/leaflet/libs/leaflet-markercluster/MarkerCluster.Default.css" rel="stylesheet" />
<script src="https://rstudio.github.io/leaflet/libs/leaflet-markercluster/leaflet.markercluster.js"></script>
<script src="https://rstudio.github.io/leaflet/libs/leaflet-markercluster/leaflet.markercluster.freezable.js"></script>
<script src="https://rstudio.github.io/leaflet/libs/leaflet-markercluster/leaflet.markercluster.layersupport.js"></script>

<style type="text/css">code{white-space: pre;}</style>
<style type="text/css">
  pre:not([class]) {
    background-color: white;
  }
</style>
<script type="text/javascript">
if (window.hljs) {
  hljs.configure({languages: []});
  hljs.initHighlightingOnLoad();
  if (document.readyState && document.readyState === "complete") {
    window.setTimeout(function() { hljs.initHighlighting(); }, 0);
  }
}
</script>

	<!-- End Leaflet -->



<meta name="author" content="dbonnery" />
<meta property="og:locale" content="en_US" />
<link rel="canonical" href="https://danielbonnery.github.io/RLeafletTools/" />
<meta property="og:url" content="https://danielbonnery.github.io/RLeafletTools/" />
<meta property="og:site_name" content="RLeafletTools" />
<meta property="og:type" content="article" />
<meta property="article:published_time" content="2021-02-03T00:00:00+00:00" />
<meta name="twitter:card" content="summary" />
<meta property="twitter:title" content="RLeafletTools" />
<script type="application/ld+json">
{"@type":"WebSite","author":{"@type":"Person","name":"dbonnery"},"headline":"RLeafletTools","dateModified":"2021-02-03T00:00:00+00:00","datePublished":"2021-02-03T00:00:00+00:00","url":"https://danielbonnery.github.io/RLeafletTools/","name":"RLeafletTools","@context":"https://schema.org"}</script>
<!-- End Jekyll SEO tag -->

    <link rel="stylesheet" href="/RLeafletTools/assets/css/style.css?v=edbc163417a80253e0aa82c22bd089aea0ec0ee1">
    <script src="https://code.jquery.com/jquery-1.12.4.min.js" integrity="sha256-ZosEbRLbNQzLpnKIkEdrPv7lOy9C27hHQ+Xp8a4MxAQ=" crossorigin="anonymous"></script>
    <script src="/RLeafletTools/assets/js/respond.js"></script>
    <!--[if lt IE 9]>
      <script src="//html5shiv.googlecode.com/svn/trunk/html5.js"></script>
    <![endif]-->
    <!--[if lt IE 8]>
    <link rel="stylesheet" href="/RLeafletTools/assets/css/ie.css">
    <![endif]-->
    <meta name="viewport" content="width=device-width, initial-scale=1, user-scalable=no">

  </head>


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

<!--html_preserve--><div id="htmlwidget-da5b53b7fb451fc3848d" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-da5b53b7fb451fc3848d">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["//{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":1,"detectRetina":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addAwesomeMarkers","args":[[49.71979,49.884051,49.502098,49.274716,49.861905,49.794334,49.701477,49.067436,49.070292,49.77994,49.060542,49.561804,49.595108,49.602554,49.72581,49.7202,49.644533,49.645651,49.615866,49.50683,48.900742,49.707329,49.884229,49.677827,49.450083,49.710838,49.276265,49.554706,49.882777,49.727998,49.737703,49.755953],[10.889217,11.228988,10.416021,10.928096,11.291932,11.509409,11.163238,10.34418,10.316987,11.186931,10.965571,11.368508,11.009011,11.005049,11.059662,11.056749,11.252699,11.248618,10.630027,11.428338,11.029479,10.806113,11.267583,11.252911,11.308721,11.172792,10.685605,11.22997,11.129541,11.202701,11.223148,11.175664],{"icon":"ios-close","markerColor":["red","red","blue","green","blue","blue","red","blue","green","blue","green","red","green","blue","red","green","red","green","red","red","red","green","green","blue","blue","green","green","green","green","red","green","red"],"iconColor":"black","spin":false,"squareMarker":false,"iconRotate":0,"font":"monospace","prefix":"ion"},null,"goodbeer",{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},null,null,{"showCoverageOnHover":true,"zoomToBoundsOnClick":true,"spiderfyOnMaxZoom":true,"removeOutsideVisibleBounds":true,"spiderLegPolylineOptions":{"weight":1.5,"color":"#222","opacity":0.5},"freezeAtZoom":false,"iconCreateFunction":"function(cluster) {\n      const groups= ['culparterretaping','marvelous','terrific'];\n      const colors= {\n      groups: ['red','green','blue'],\n      center:'#ddd',\n      text:'black'\n      };\n      const markers= cluster.getAllChildMarkers();\n      \n      const proportions= groups.map(group => markers.filter(marker => marker.options.label === group).length / markers.length);\n      function sum(arr, first= 0, last) {\n      return arr.slice(first, last).reduce((total, curr) => total+curr, 0);\n      }\n      const cumulativeProportions= proportions.map((val, i, arr) => sum(arr, 0, i+1));\n      cumulativeProportions.unshift(0);\n      \n      const widthgm = 2*Math.sqrt(markers.length);\n      const radiusgm= 15+widthgm/2;\n      const width = 2*Math.min(Math.sqrt(markers.length),5);\n      const radius= 15+1.2*Math.log(markers.length)/Math.log(10)+width/2;\n      \n      const arcs= cumulativeProportions.map((prop, i) => { return {\n      x   :  radius*Math.sin(2*Math.PI*prop),\n      y   : -radius*Math.cos(2*Math.PI*prop),\n      long: proportions[i-1] >.5 ? 1 : 0\n      }});\n      const paths= proportions.map((prop, i) => {\n      if (prop === 0) return '';\n      else if (prop === 1) return `<circle cx='0' cy='0' r='${radius}' fill='none' stroke='${colors.groups[i]}' stroke-width='${width}' stroke-alignment='center' stroke-linecap='butt' />`;\n      else return `<path d='M ${arcs[i].x} ${arcs[i].y} A ${radius} ${radius} 0 ${arcs[i+1].long} 1 ${arcs[i+1].x} ${arcs[i+1].y}' fill='none' stroke='${colors.groups[i]}' stroke-width='${width}' stroke-alignment='center' stroke-linecap='butt' />`\n      });\n      \n      return new L.DivIcon({\n      html: `\n      <svg width='60' height='60' viewBox='-30 -30 60 60' style='width: 60px; height: 60px; position: relative; top: -24px; left: -24px;' >\n      <circle cx='0' cy='0' r='${radius}' stroke='none' fill='${colors.center}' />\n      <text x='0' y='0' dominant-baseline='central' text-anchor='middle' fill='${colors.text}' font-size='15'>${markers.length}<\/text>\n      ${paths.join('')}\n      <\/svg>\n      `,\n      className: 'marker-cluster'\n      });\n}"},["toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto"],["culparterretaping","culparterretaping","terrific","marvelous","terrific","terrific","culparterretaping","terrific","marvelous","terrific","marvelous","culparterretaping","marvelous","terrific","culparterretaping","marvelous","culparterretaping","marvelous","culparterretaping","culparterretaping","culparterretaping","marvelous","marvelous","terrific","terrific","marvelous","marvelous","marvelous","marvelous","culparterretaping","marvelous","culparterretaping"],{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]}],"limits":{"lat":[48.900742,49.884229],"lng":[10.316987,11.509409]}},"evals":["calls.1.args.8.iconCreateFunction"],"jsHooks":[]}</script><!--/html_preserve-->


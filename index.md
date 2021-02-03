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
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
      
    {% capture title %}
    {%- if page.share-title -%}
    {{ page.share-title | strip_html | xml_escape }}
    {%- elsif page.title -%}
    {{ page.title | strip_html | xml_escape  }}
    {%- else -%}
    {{ site.title | strip_html | xml_escape }}
    {%- endif -%}
    {% endcapture %}
    
    {% capture description %}
    {%- if page.share-description -%}
    {{ page.share-description | strip_html | xml_escape }}
    {%- elsif page.subtitle -%}
    {{ page.subtitle | strip_html | xml_escape }}
    {%- else -%}
    {%- assign excerpt_length = site.excerpt_length | default: 50 -%}
    {{ page.content | strip_html | xml_escape | truncatewords: excerpt_length | strip }}
    {%- endif -%}
    {% endcapture %}
    
    <title>{{ title }}</title>
      
    {% if site.author %}
    <meta name="author" content="{{ site.author }}">
    {% endif %}
    
    <meta name="description" content="{{ description }}">
      
    {% if site.mobile-theme-col %}
    <meta name="theme-color" content="{{ site.mobile-theme-col }}">
    {% endif %}
    
    {% if site.keywords %}
    <meta name="keywords" content="{{ site.keywords }}">
    {% endif %}
    
    <link rel="alternate" type="application/rss+xml" title="{{ site.title }}" href="{{ '/feed.xml' | absolute_url }}">
      
    {% include gtag.html %}
    {% include gtm_head.html %}
    {% include google_analytics.html %}
    
    {% if layout.common-ext-css %}
    {% for css in layout.common-ext-css %}
    {% include ext-css.html css=css %}
    {% endfor %}
    {% endif %}
    
    {% if layout.common-css %}
    {% for css in layout.common-css %}
    <link rel="stylesheet" href="{{ css | relative_url }}">
    {% endfor %}
    {% endif %}
    
    {% if site.site-css %}
    {% for css in site.site-css %}
    <link rel="stylesheet" href="{{ css | relative_url }}">
    {% endfor %}
    {% endif %}
    
    {% if page.ext-css %}
    {% for css in page.ext-css %}
    {% include ext-css.html css=css %}
    {% endfor %}
    {% endif %}
    
    {% if page.css %}
    {% for css in page.css %}
    <link rel="stylesheet" href="{{ css | relative_url }}">
    {% endfor %}
    {% endif %}
    
    {% if site.fb_app_id %}
    <meta property="fb:app_id" content="{{ site.fb_app_id }}">
    {% endif %}
    
    {% if site.title %}
    <meta property="og:site_name" content="{{ site.title }}">
    {% endif %}
    
    {%- capture img -%}
    {%- if page.share-img -%}
    {{ page.share-img }}
    {%- elsif page.cover-img -%}
    {%- if page.cover-img.first -%}
    {{ page.cover-img[0].first.first }}
    {%- else -%}
    {{ page.cover-img }}
    {%- endif -%}
    {%- elsif page.thumbnail-img -%}
    {{ page.thumbnail-img }}
    {%- elsif site.avatar -%}
    {{ site.avatar }}
    {% endif %}
    {%- endcapture -%}
    {%- assign img=img | strip -%}
    
    <meta property="og:title" content="{{ title }}">
      <meta property="og:description" content="{{ description }}">
        
      {% if img != "" %}
      <meta property="og:image" content="{{ img | absolute_url }}">
      {% endif %}
      
      {% if page.id %}
      <meta property="og:type" content="article">
        <meta property="og:article:author" content="{{ site.author }}">
          <meta property="og:article:published_time" content="{{ page.date | date_to_xmlschema }}">
            <meta property="og:url" content="{{ page.url | absolute_url }}">
              <link rel="canonical" href="{{ page.url | absolute_url }}">
              {% else %}
              <meta property="og:type" content="website">
                <meta property="og:url" content="{{ page.url | absolute_url | strip_index }}">
                  <link rel="canonical" href="{{ page.url | absolute_url | strip_index }}">
                  {% endif %}
                  
                  {% if img != "" and img != site.avatar %}
                  <meta name="twitter:card" content="summary_large_image">
                  {% else %}
                  <meta name="twitter:card" content="summary">
                  {% endif %}
                  <meta name="twitter:site" content="@{{ site.social-network-links.twitter }}">
                    <meta name="twitter:creator" content="@{{ site.social-network-links.twitter }}">
                      
                      <meta property="twitter:title" content="{{ title }}">
                        <meta property="twitter:description" content="{{ description }}">
                          
                        {% if img != "" %}
                        <meta name="twitter:image" content="{{ img | absolute_url }}">
                        {% endif %}
                        
                        {% include matomo.html %}
                        
                        {% if page.comments and site.staticman.repository and site.staticman.branch %}
                        <link rel="stylesheet" href="{{ "/assets/css/staticman.css" | relative_url }}">
                        {% endif %}
                        
                        {% if page.head-extra %}
                        {% for file in page.head-extra %}
                        {% include {{ file }} %}
                        {% endfor %}
                        {% endif %}
                        
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

<!--html_preserve--><div id="htmlwidget-6b32f2107518c275b7fa" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-6b32f2107518c275b7fa">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["//{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":1,"detectRetina":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addAwesomeMarkers","args":[[49.71979,49.884051,49.502098,49.274716,49.861905,49.794334,49.701477,49.067436,49.070292,49.77994,49.060542,49.561804,49.595108,49.602554,49.72581,49.7202,49.644533,49.645651,49.615866,49.50683,48.900742,49.707329,49.884229,49.677827,49.450083,49.710838,49.276265,49.554706,49.882777,49.727998,49.737703,49.755953],[10.889217,11.228988,10.416021,10.928096,11.291932,11.509409,11.163238,10.34418,10.316987,11.186931,10.965571,11.368508,11.009011,11.005049,11.059662,11.056749,11.252699,11.248618,10.630027,11.428338,11.029479,10.806113,11.267583,11.252911,11.308721,11.172792,10.685605,11.22997,11.129541,11.202701,11.223148,11.175664],{"icon":"ios-close","markerColor":["red","red","blue","red","red","green","red","red","green","blue","red","blue","red","blue","blue","blue","red","red","red","blue","green","red","blue","green","blue","red","blue","red","green","blue","green","red"],"iconColor":"black","spin":false,"squareMarker":false,"iconRotate":0,"font":"monospace","prefix":"ion"},null,"goodbeer",{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},null,null,{"showCoverageOnHover":true,"zoomToBoundsOnClick":true,"spiderfyOnMaxZoom":true,"removeOutsideVisibleBounds":true,"spiderLegPolylineOptions":{"weight":1.5,"color":"#222","opacity":0.5},"freezeAtZoom":false,"iconCreateFunction":"function(cluster) {\n      const groups= ['culparterretaping','marvelous','terrific'];\n      const colors= {\n      groups: ['red','green','blue'],\n      center:'#ddd',\n      text:'black'\n      };\n      const markers= cluster.getAllChildMarkers();\n      \n      const proportions= groups.map(group => markers.filter(marker => marker.options.label === group).length / markers.length);\n      function sum(arr, first= 0, last) {\n      return arr.slice(first, last).reduce((total, curr) => total+curr, 0);\n      }\n      const cumulativeProportions= proportions.map((val, i, arr) => sum(arr, 0, i+1));\n      cumulativeProportions.unshift(0);\n      \n      const widthgm = 2*Math.sqrt(markers.length);\n      const radiusgm= 15+widthgm/2;\n      const width = 2*Math.min(Math.sqrt(markers.length),5);\n      const radius= 15+1.2*Math.log(markers.length)/Math.log(10)+width/2;\n      \n      const arcs= cumulativeProportions.map((prop, i) => { return {\n      x   :  radius*Math.sin(2*Math.PI*prop),\n      y   : -radius*Math.cos(2*Math.PI*prop),\n      long: proportions[i-1] >.5 ? 1 : 0\n      }});\n      const paths= proportions.map((prop, i) => {\n      if (prop === 0) return '';\n      else if (prop === 1) return `<circle cx='0' cy='0' r='${radius}' fill='none' stroke='${colors.groups[i]}' stroke-width='${width}' stroke-alignment='center' stroke-linecap='butt' />`;\n      else return `<path d='M ${arcs[i].x} ${arcs[i].y} A ${radius} ${radius} 0 ${arcs[i+1].long} 1 ${arcs[i+1].x} ${arcs[i+1].y}' fill='none' stroke='${colors.groups[i]}' stroke-width='${width}' stroke-alignment='center' stroke-linecap='butt' />`\n      });\n      \n      return new L.DivIcon({\n      html: `\n      <svg width='60' height='60' viewBox='-30 -30 60 60' style='width: 60px; height: 60px; position: relative; top: -24px; left: -24px;' >\n      <circle cx='0' cy='0' r='${radius}' stroke='none' fill='${colors.center}' />\n      <text x='0' y='0' dominant-baseline='central' text-anchor='middle' fill='${colors.text}' font-size='15'>${markers.length}<\/text>\n      ${paths.join('')}\n      <\/svg>\n      `,\n      className: 'marker-cluster'\n      });\n}"},["toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto","toto"],["culparterretaping","culparterretaping","terrific","culparterretaping","culparterretaping","marvelous","culparterretaping","culparterretaping","marvelous","terrific","culparterretaping","terrific","culparterretaping","terrific","terrific","terrific","culparterretaping","culparterretaping","culparterretaping","terrific","marvelous","culparterretaping","terrific","marvelous","terrific","culparterretaping","terrific","culparterretaping","marvelous","terrific","marvelous","culparterretaping"],{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]}],"limits":{"lat":[48.900742,49.884229],"lng":[10.316987,11.509409]}},"evals":["calls.1.args.8.iconCreateFunction"],"jsHooks":[]}</script><!--/html_preserve-->


---
title       : Project-ddp2014
subtitle    : Project presentation of Unit conversion dynamic UI
author      : Alok Juneja
job         : Presentation made on Fri Jun 20 01:12:40 2014
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [bootstrap,mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

<!-- Limit image width and height -->
<style type='text/css'>
img {
    max-height: 500px;
    max-width: 960px;
}
</style>

## Why Unit conversion?

A system of measurement is a set of units of measurement which we use in our daily life to quantify the things that we use/consume.

There are several systems of measurements used in different countries and in different fields of science depending on the requirements. To name few..

1. Metric system
2. Imperial and US customary units
3. Natural units
4. Non-standard units
5. Units of currency

--- .outfont #id 

## Temperature / Length / Volume Conversions

As a demonstration, a simple unit converter is implemented in shiny. Following conversions have been used.

Temperature conversion

$^{\circ}\mathrm{C} = (^{\circ}\mathrm{F} - 32) * 5/9$

$^{\circ}\mathrm{F} = (^{\circ}\mathrm{C} * 9/5) + 32$ 

$K = ^{\circ}\mathrm{C} + 273.15$ 

Length conversion

$Mile = Km * 0.62137$

$Yard = Km * 1093.6$

Volume conversion

$mL = US oz * 29.5735$

--- .codefont #id

## Examples used in daily life
We do conversions from one unit to another in our daily life. Few examples..

```r
#Q1. What is the human body temperature (37 degree celsius) in degree Fahrenheit?
bd_cel=37
(bd_cel*9/5)+32
```

```
## [1] 98.6
```

```r
#Q2. How many meters is equivalent to 1 mile in US?
dis_mile=1
dis_mile*1609.344
```

```
## [1] 1609
```

```r
#Q3. How much ml in 12.004 US oz coke can in US? 
can_oz=12.004
can_oz * 29.5735
```

```
## [1] 355
```

--- .class #id 

## Application and shiny source code

Shiny source code:

https://gist.github.com/junejaalok/9dfe302679c032a80c47

Application on shinapps.io

https://junejaalok.shinyapps.io/project-ddp2014/

In case the DESCRIPTION  and README.md does not show you the full GUI on web browser, try to resize your web browser otherwise please use the following link... 

https://junejaalok.shinyapps.io/project-ddp2014/?showcase=0

--- &carousel .span12

## Carousel

*** {class: active, img: "assets/img/convert-temperature.png"}

Convert Temperature

*** {img: "assets/img/convert-length.png"}

Convert Length

*** {img: "assets/img/convert-volume.png"}

Convert Volume

--- .class #id

## References 

Following web-pages helped me to get better insight of making shiny application and slidify presentation

http://slidify.org/samples/intro/index.html#1

http://stackoverflow.com/questions/23747704/font-size-and-line-spacing-r-slidify

https://gist.github.com/wch/9609200

https://gist.github.com/wch/9689441

https://github.com/ramnathv/slidify/issues/158

https://gist.github.com/jeromyanglim/2716336

https://github.com/rstudio/shinyapps/blob/master/guide/guide.md

https://github.com/ramnathv/carouselLayout

http://stackoverflow.com/questions/16904054/slidify-how-to-position-an-image




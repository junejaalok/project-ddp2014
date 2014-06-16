---
title       : Project-ddp2014
subtitle    : Project presentation of Unit conversion dynamic UI
author      : Alok Juneja
job         : Presentation made on Mon Jun 16 18:06:24 2014
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Why Unit conversion?

A system of measurement is a set of units of measurement which we use in our daily life to quantify the things that we use/consume.

There are several systems of measurements used in different countries and in different fields of science depending on the requirements. To name few..

1. Metric system
2. Imperial and US customary units
3. Natural units
4. Non-standard units
5. Units of currency

--- .class #id 

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

$Ml = US oz * 29.5735$

--- .class #id font-size: 8px

## Examples used in daily life


```r
#Q1. What is the human body temperature (37 degree celsius) in degree Fahrenheit?
bd_cel=37
(bd_cel*9/5)+32
```

```
## [1] 98.6
```

```r
#Q2. How many kilometers is equivalent to 1 mile in US?
dis_mile=1
dis_mile*1609.344/1000
```

```
## [1] 1.609
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

In case 

https://junejaalok.shinyapps.io/project-ddp2014/?showcase=0

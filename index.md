---
title       : Project-ddp2014
subtitle    : Project presentation of Unit conversion dynamic UI
author      : Alok Juneja
job         : Presentation made on Sun Jun 15 18:09:13 2014
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Why Unit conversion?

A system of measurement is a set of units of measurement which we use in our daily life to quantify the things that we use/consume.

System of measurement

1. Metric system:

    evolved since the adoption of the first well-defined system in France in 1795

    in the early metric system there were two fundamental or base units, the metre for length and the gram for mass.

2. Imperial and US customary units:
    
--- .class #id 

## Different systems

Length conversion

$^{\circ}\mathrm{C} = (^{\circ}\mathrm{F} - 32)/1.8$ 

--- .class #id 

## R code and shiny (ui.R)


```r
library(shiny)

shinyUI(fluidPage(
  headerPanel("Unit converter"),
  fluidRow(column(10,
    fluidRow(column(4,
      radioButtons("id1", "Choose option",
                   c("Temperature" = "Temperature",
                     "Length" = "Length")),

      # This outputs the dynamic UI component based on the option above
	    uiOutput("ui1"),
      textInput('val1',"Enter the value"),
	    uiOutput("ui2")

    ),
    column(6,
    mainPanel(
        verbatimTextOutput("typ"),
        verbatimTextOutput("ans")
  )))
))))
```

--- .class #id

## R code and shiny (server.R)


```r
library(shiny)

converter <- function(id,from,to,val) {
  switch(id,
  	"Temperature"={
			switch(from,
				"Celsius"={
					switch(to,
						"Celsius" = round(val,digits=6),
						"Fahrenheit" = round((val * 9/5) + 32,digits=6),
						"Kelvin" = round(val + 273.15,digits=6))
				},
				"Fahrenheit"={
					switch(to,
						"Celsius" = round((val - 32 ) * 5/9,digits=6),
						"Fahrenheit" = round(val,digits=6),
						"Kelvin" = round(((val - 32 ) * 5/9) + 273.15,digits=6))
				},
				"Kelvin"={
					switch(to,
					"Celsius" = round(val - 273.15,digits=6),
					"Fahrenheit" = round(((val - 273.15) * 9/5) + 32,digits=6),
					"Kelvin" = round(val,digits=6))
				}
			)
		},
		"Length" = {
			switch(from,
				"Kilometers" = {
					switch(to,
						"Kilometers" = round(val,digits=6),
						"Miles" = round(val * 0.62137,digits=6),
						"Yards" = round(val * 1093.6,digits=6))
				},
				"Miles" = {
					switch(to,
						"Kilometers" = round(val * 1.609344,digits=6),
						"Miles" = round(val,digits=6),
						"Yards" = round(val * 1760,digits=6))
				},
				"Yards" = {
					switch(to,
						"Kilometers" = round(val * 0.00091,digits=6),
						"Miles" = round(val * 0.00056818,digits=6),
						"Yards" = round(val,digits=6))
				}
			)
		}
	)
} 

shinyServer(
  function(input, output) {
	# Depending on input$id1, generate a different conversion units
	# UI component and send it to the client.
  
	output$ui1 <- renderUI({
	  if (is.null(input$id1))
	    return()
    
 		switch(input$id1,
  		"Temperature" = selectInput("from", "From", c("Celsius", "Fahrenheit", "Kelvin")),
  		"Length" = selectInput("from", "From", c("Kilometers", "Miles","Yards")))
  		})

	output$ui2 <- renderUI({
	  if (is.null(input$id1))
	    return()
	  
    switch(input$id1,
  		"Temperature" = selectInput("to", "To", c("Celsius", "Fahrenheit", "Kelvin")),
  		"Length" = selectInput("to", "To", c("Kilometers", "Miles","Yards")))
  		})

  
  output$typ <- renderText({paste("Convert", input$id1 )})	
  output$ans <- renderText({paste(input$val1, input$from, "=",converter(toString(input$id1),toString(input$from),toString(input$to),as.double(input$val1)),input$to)})
  }
)
```

---
description: Creating and Updating Figures with Plotly's R graphing library
display_as: file_settings
language: r
layout: base
name: Creating and Updating Figures
order: 2
output:
  html_document:
    keep_md: true
page_type: example_index
permalink: r/creating-and-updating-figures/
thumbnail: thumbnail/creating-and-updating-figures.png
---

The `plotly` R package exists to create, manipulate and [render](https://plotly.com/r/getting-started/#rendering-charts) graphical figures (i.e. charts, plots, maps and diagrams) represented by data structures also referred to as figures. The rendering process uses the [Plotly.js JavaScript library](https://plotly.com/javascript/) under the hood although R developers using this module very rarely need to interact with the Javascript library directly, if ever. Figures can be represented in R either as lists or as instances of the Plotly Figures, and are serialized as text in [JavaScript Object Notation (JSON)](https://json.org/) before being passed to Plotly.js.

### Figures As Lists

Figures can be represented as Lists and displayed using `plotly_build` function. The `fig` list in the example below describes a figure. It contains a single `bar` trace and a title.


```r
library(plotly)
fig = list(
  data = list(
    list(
      x = c(1, 2, 3),
      y = c(1, 3, 2),
      type = 'bar'
    )
  ),
  layout = list(
    title = 'A Figure Specified By R List',
    plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff')
  )
)
# To display the figure defined by this list, use the plotly_build function
plotly_build(fig)
```

<div id="htmlwidget-c0ef1437c6b0fcb2bdf9" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c0ef1437c6b0fcb2bdf9">{"x":{"data":[{"x":[1,2,3],"y":[1,3,2],"type":"bar","xaxis":"x","yaxis":"y","frame":null}],"layout":{"title":"A Figure Specified By R List","plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff"},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff"},"hovermode":"closest","showlegend":false},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly","attrs":[]},"evals":[],"jsHooks":[]}</script>

### Plotly Figures 

The `plot_ly` function provides an automatically-generated hierarchy of classes that may be used to represent figures.

`plot_ly` figures have several benefits compared to plain R Lists.

1. `plot_ly` figures provide precise data validation. If you provide an invalid property name or an invalid property value as the key to a Plotly Figure, an exception will be raised with a helpful error message describing the problem. This is not the case if you use plain R lists to build your figures.
2. `plot_ly` figures contain descriptions of each valid property as R docstrings. You can use these docstrings in the development environment of your choice to learn about the available properties as an alternative to consulting the online [Full Reference](https://plotly.com/r/reference/).
3. Properties of `plot_ly` figures can be accessed using both dictionary-style key lookup (e.g. `fig$x`).
4. `plot_ly` figures support higher-level convenience functions for making updates to already constructed figures (`.layout()`, `.add_trace()` etc).
5. `plot_ly` figures support attached rendering and exporting functions that automatically invoke the appropriate functions.

Below you can find an example of one way that the figure in the example above could be specified using a `plot_ly` figure instead of a list.


```r
library(plotly) 
 
fig <- plot_ly(x = c(1, 2, 3), y = c(1, 3, 2), type = 'bar')%>% 
  layout(title = 'A Plotly Figure',
         plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff')) 
fig
```

<div id="htmlwidget-6ee41cc4cf61d611a82f" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-6ee41cc4cf61d611a82f">{"x":{"visdat":{"30f259340ae2":["function () ","plotlyVisDat"]},"cur_data":"30f259340ae2","attrs":{"30f259340ae2":{"x":[1,2,3],"y":[1,3,2],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"A Plotly Figure","plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3],"y":[1,3,2],"type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Converting plot_ly figures To Lists and JSON

`plot_ly` figures can be turned into their R List representation. You can also retrieve the JSON string representation of a plotly figure using the `fig.to_JSON()` method.


```r
library(plotly) 
library(jsonlite)
fig <- plot_ly(x = c(1, 2, 3), y = c(1, 3, 2), type = 'bar')
plotly_json <- function(p, ...) {
    plotly:::to_JSON(plotly_build(p), ...)
  }
jfig <- plotly_json(fig, pretty = TRUE)

cat("List Representation of a plot_ly figure:")
```

```{style="max-height: 200px;"}
## List Representation of a plot_ly figure:
```

```r
str(fig, max.level = 2)
```

```{style="max-height: 200px;"}
## List of 8
##  $ x            :List of 6
##   ..$ visdat  :List of 1
##   ..$ cur_data: chr "30f2411f047d"
##   ..$ attrs   :List of 1
##   ..$ layout  :List of 3
##   ..$ source  : chr "A"
##   ..$ config  :List of 2
##   ..- attr(*, "TOJSON_FUNC")=function (x, ...)  
##  $ width        : NULL
##  $ height       : NULL
##  $ sizingPolicy :List of 6
##   ..$ defaultWidth : chr "100%"
##   ..$ defaultHeight: num 400
##   ..$ padding      : num 0
##   ..$ viewer       :List of 6
##   ..$ browser      :List of 5
##   ..$ knitr        :List of 3
##  $ dependencies :List of 5
##   ..$ :List of 10
##   .. ..- attr(*, "class")= chr "html_dependency"
##   ..$ :List of 10
##   .. ..- attr(*, "class")= chr "html_dependency"
##   ..$ :List of 10
##   .. ..- attr(*, "class")= chr "html_dependency"
##   ..$ :List of 10
##   .. ..- attr(*, "class")= chr "html_dependency"
##   ..$ :List of 10
##   .. ..- attr(*, "class")= chr "html_dependency"
##  $ elementId    : NULL
##  $ preRenderHook:function (p, registerFrames = TRUE)  
##  $ jsHooks      : list()
##  - attr(*, "class")= chr [1:2] "plotly" "htmlwidget"
##  - attr(*, "package")= chr "plotly"
```

```r
cat("JSON Representation of a plot_ly figure:", jfig, sep = "\n\n")
```

```{style="max-height: 200px;"}
## JSON Representation of a plot_ly figure:
## 
## {
##   "x": {
##     "visdat": {
##       "30f2411f047d": ["function () ", "plotlyVisDat"]
##     },
##     "cur_data": "30f2411f047d",
##     "attrs": {
##       "30f2411f047d": {
##         "x": [1, 2, 3],
##         "y": [1, 3, 2],
##         "alpha_stroke": 1,
##         "sizes": [10, 100],
##         "spans": [1, 20],
##         "type": "bar"
##       }
##     },
##     "layout": {
##       "margin": {
##         "b": 40,
##         "l": 60,
##         "t": 25,
##         "r": 10
##       },
##       "xaxis": {
##         "domain": [0, 1],
##         "automargin": true,
##         "title": []
##       },
##       "yaxis": {
##         "domain": [0, 1],
##         "automargin": true,
##         "title": []
##       },
##       "hovermode": "closest",
##       "showlegend": false
##     },
##     "source": "A",
##     "config": {
##       "modeBarButtonsToAdd": ["hoverclosest", "hovercompare"],
##       "showSendToCloud": false
##     },
##     "data": [
##       {
##         "x": [1, 2, 3],
##         "y": [1, 3, 2],
##         "type": "bar",
##         "marker": {
##           "color": "rgba(31,119,180,1)",
##           "line": {
##             "color": "rgba(31,119,180,1)"
##           }
##         },
##         "error_y": {
##           "color": "rgba(31,119,180,1)"
##         },
##         "error_x": {
##           "color": "rgba(31,119,180,1)"
##         },
##         "xaxis": "x",
##         "yaxis": "y",
##         "frame": null
##       }
##     ],
##     "highlight": {
##       "on": "plotly_click",
##       "persistent": false,
##       "dynamic": false,
##       "selectize": false,
##       "opacityDim": 0.2,
##       "selected": {
##         "opacity": 1
##       },
##       "debounce": 0
##     },
##     "shinyEvents": ["plotly_hover", "plotly_click", "plotly_selected", "plotly_relayout", "plotly_brushed", "plotly_brushing", "plotly_clickannotation", "plotly_doubleclick", "plotly_deselect", "plotly_afterplot", "plotly_sunburstclick"],
##     "base_url": "https://plot.ly"
##   },
##   "width": null,
##   "height": null,
##   "sizingPolicy": {
##     "defaultWidth": "100%",
##     "defaultHeight": 400,
##     "padding": 0,
##     "viewer": {
##       "defaultWidth": null,
##       "defaultHeight": null,
##       "padding": null,
##       "fill": true,
##       "suppress": false,
##       "paneHeight": null
##     },
##     "browser": {
##       "defaultWidth": null,
##       "defaultHeight": null,
##       "padding": null,
##       "fill": true,
##       "external": false
##     },
##     "knitr": {
##       "defaultWidth": null,
##       "defaultHeight": null,
##       "figure": true
##     }
##   },
##   "dependencies": [
##     {
##       "name": "typedarray",
##       "version": "0.1",
##       "src": {
##         "file": "htmlwidgets/lib/typedarray"
##       },
##       "meta": null,
##       "script": "typedarray.min.js",
##       "stylesheet": null,
##       "head": null,
##       "attachment": null,
##       "package": "plotly",
##       "all_files": false
##     },
##     {
##       "name": "jquery",
##       "version": "3.5.1",
##       "src": {
##         "file": "lib/jquery"
##       },
##       "meta": null,
##       "script": "jquery.min.js",
##       "stylesheet": null,
##       "head": null,
##       "attachment": null,
##       "package": "crosstalk",
##       "all_files": true
##     },
##     {
##       "name": "crosstalk",
##       "version": "1.1.1",
##       "src": {
##         "file": "www"
##       },
##       "meta": null,
##       "script": "js/crosstalk.min.js",
##       "stylesheet": "css/crosstalk.css",
##       "head": null,
##       "attachment": null,
##       "package": "crosstalk",
##       "all_files": true
##     },
##     {
##       "name": "plotly-htmlwidgets-css",
##       "version": "2.5.1",
##       "src": {
##         "file": "htmlwidgets/lib/plotlyjs"
##       },
##       "meta": null,
##       "script": null,
##       "stylesheet": "plotly-htmlwidgets.css",
##       "head": null,
##       "attachment": null,
##       "package": "plotly",
##       "all_files": false
##     },
##     {
##       "name": "plotly-main",
##       "version": "2.5.1",
##       "src": {
##         "file": "htmlwidgets/lib/plotlyjs"
##       },
##       "meta": null,
##       "script": "plotly-latest.min.js",
##       "stylesheet": null,
##       "head": null,
##       "attachment": null,
##       "package": "plotly",
##       "all_files": false
##     }
##   ],
##   "elementId": null,
##   "preRenderHook": ["function (p, registerFrames = TRUE) ", "{", "    UseMethod(\"plotly_build\")", "}"],
##   "jsHooks": []
## }
```

### Representing Figures in Dash

[Dash for R](https://dashr.plotly.com/) is an open-source framework for building analytical applications, with no Javascript required, and it is tightly integrated with the Plotly graphing library. 
 
Learn about how to install Dash for R at https://dashr.plot.ly/installation. 
 
Everywhere in this page that you see fig, you can display the same figure in a Dash for R application by passing it to the figure argument.


```r
library(dash)
library(dashCoreComponents)
library(dashHtmlComponents)
library(plotly)

fig <- plot_ly() %>%
  add_lines(x = c("a","b","c"), y = c(1,3,2))%>%
  layout(title="sample figure")

app <- Dash$new()

app$layout(
  htmlDiv(
    list(
      dccGraph(id = 'graph', figure=fig),
      htmlPre(
        id='structure',
        style = list(border = 'thin lightgrey solid',
                     overflowY = 'scroll',
                     height = '275px')
      )
    )
  )
)
app$callback(
  output(id = 'structure', property='children'),
  params=list(input(id='graph', property='figure')),
  function(fig_json) {
    plotly_json <- function(p, ...) {
      plotly:::to_JSON(plotly_build(p), ...)
    }
    jfig <- plotly_json(fig, pretty = TRUE)
    return(jfig)
  })
#app$run_server()
```

Use `app$run_server()` to run the dash app.

### Creating Figures

This section summarizes several ways to create new `plot_ly` figures with the `plotly` graphing library.

#### Plotly Scatter Plot


```r
library(plotly)
data(iris)

fig <- plot_ly(data = iris, x = ~Sepal.Width, y = ~Sepal.Length, color = ~Species, 
               type = "scatter", mode = "markers")%>%
  layout(title="A Plotly Figure", legend=list(title=list(text='species')),
         plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))
fig
```

<div id="htmlwidget-30c21567bd6a77cb0cd7" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-30c21567bd6a77cb0cd7">{"x":{"visdat":{"30f274451de4":["function () ","plotlyVisDat"]},"cur_data":"30f274451de4","attrs":{"30f274451de4":{"x":{},"y":{},"mode":"markers","color":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"A Plotly Figure","legend":{"title":{"text":"species"}},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":"Sepal.Width"},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":"Sepal.Length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[3.5,3,3.2,3.1,3.6,3.9,3.4,3.4,2.9,3.1,3.7,3.4,3,3,4,4.4,3.9,3.5,3.8,3.8,3.4,3.7,3.6,3.3,3.4,3,3.4,3.5,3.4,3.2,3.1,3.4,4.1,4.2,3.1,3.2,3.5,3.6,3,3.4,3.5,2.3,3.2,3.5,3.8,3,3.8,3.2,3.7,3.3],"y":[5.1,4.9,4.7,4.6,5,5.4,4.6,5,4.4,4.9,5.4,4.8,4.8,4.3,5.8,5.7,5.4,5.1,5.7,5.1,5.4,5.1,4.6,5.1,4.8,5,5,5.2,5.2,4.7,4.8,5.4,5.2,5.5,4.9,5,5.5,4.9,4.4,5.1,5,4.5,4.4,5,5.1,4.8,5.1,4.6,5.3,5],"mode":"markers","type":"scatter","name":"setosa","marker":{"color":"rgba(102,194,165,1)","line":{"color":"rgba(102,194,165,1)"}},"textfont":{"color":"rgba(102,194,165,1)"},"error_y":{"color":"rgba(102,194,165,1)"},"error_x":{"color":"rgba(102,194,165,1)"},"line":{"color":"rgba(102,194,165,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[3.2,3.2,3.1,2.3,2.8,2.8,3.3,2.4,2.9,2.7,2,3,2.2,2.9,2.9,3.1,3,2.7,2.2,2.5,3.2,2.8,2.5,2.8,2.9,3,2.8,3,2.9,2.6,2.4,2.4,2.7,2.7,3,3.4,3.1,2.3,3,2.5,2.6,3,2.6,2.3,2.7,3,2.9,2.9,2.5,2.8],"y":[7,6.4,6.9,5.5,6.5,5.7,6.3,4.9,6.6,5.2,5,5.9,6,6.1,5.6,6.7,5.6,5.8,6.2,5.6,5.9,6.1,6.3,6.1,6.4,6.6,6.8,6.7,6,5.7,5.5,5.5,5.8,6,5.4,6,6.7,6.3,5.6,5.5,5.5,6.1,5.8,5,5.6,5.7,5.7,6.2,5.1,5.7],"mode":"markers","type":"scatter","name":"versicolor","marker":{"color":"rgba(252,141,98,1)","line":{"color":"rgba(252,141,98,1)"}},"textfont":{"color":"rgba(252,141,98,1)"},"error_y":{"color":"rgba(252,141,98,1)"},"error_x":{"color":"rgba(252,141,98,1)"},"line":{"color":"rgba(252,141,98,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[3.3,2.7,3,2.9,3,3,2.5,2.9,2.5,3.6,3.2,2.7,3,2.5,2.8,3.2,3,3.8,2.6,2.2,3.2,2.8,2.8,2.7,3.3,3.2,2.8,3,2.8,3,2.8,3.8,2.8,2.8,2.6,3,3.4,3.1,3,3.1,3.1,3.1,2.7,3.2,3.3,3,2.5,3,3.4,3],"y":[6.3,5.8,7.1,6.3,6.5,7.6,4.9,7.3,6.7,7.2,6.5,6.4,6.8,5.7,5.8,6.4,6.5,7.7,7.7,6,6.9,5.6,7.7,6.3,6.7,7.2,6.2,6.1,6.4,7.2,7.4,7.9,6.4,6.3,6.1,7.7,6.3,6.4,6,6.9,6.7,6.9,5.8,6.8,6.7,6.7,6.3,6.5,6.2,5.9],"mode":"markers","type":"scatter","name":"virginica","marker":{"color":"rgba(141,160,203,1)","line":{"color":"rgba(141,160,203,1)"}},"textfont":{"color":"rgba(141,160,203,1)"},"error_y":{"color":"rgba(141,160,203,1)"},"error_x":{"color":"rgba(141,160,203,1)"},"line":{"color":"rgba(141,160,203,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Make Subplots

The `subplots()` function produces a `plot_ly` figure that is preconfigured with a grid of subplots that traces can be added to. 


```r
library(plotly)

fig1 <- plot_ly(y = c(4, 2, 1), type = "scatter", mode = "lines") %>%
  layout(plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))
fig2 <- plot_ly(y = c(2, 1, 3), type = "bar") %>%
  layout(plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))

fig <- subplot(fig1, fig2)
fig
```

<div id="htmlwidget-f8ce168d67e1d9780d23" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-f8ce168d67e1d9780d23">{"x":{"data":[{"y":[4,2,1],"mode":"lines","type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null},{"y":[2,1,3],"type":"bar","marker":{"color":"rgba(255,127,14,1)","line":{"color":"rgba(255,127,14,1)"}},"error_y":{"color":"rgba(255,127,14,1)"},"error_x":{"color":"rgba(255,127,14,1)"},"xaxis":"x2","yaxis":"y2","frame":null}],"layout":{"xaxis":{"domain":[0,0.48],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"y"},"xaxis2":{"domain":[0.52,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"y2"},"yaxis2":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"x2"},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"x"},"annotations":[],"shapes":[],"images":[],"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","hovermode":"closest","showlegend":true},"attrs":{"30f277d9740f":{"y":[4,2,1],"mode":"lines","alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"},"30f23a9fbbf6":{"y":[2,1,3],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"subplot":true,"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Updating Figures

Regardless of how a `plot_ly` figure was constructed, it can be updated by adding additional traces to it and modifying its properties.

#### Adding Traces

New traces can be added to a `plot_ly` figure using the `add_trace()` method. This method accepts a `plot_ly` figure trace and adds it to the figure. This allows you to start with an empty figure, and add traces to it sequentially. 


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 2), type = 'bar') %>%
  layout(plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))
fig
```

<div id="htmlwidget-9a02c655962fe1b8ac0a" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-9a02c655962fe1b8ac0a">{"x":{"visdat":{"30f25bda40ef":["function () ","plotlyVisDat"]},"cur_data":"30f25bda40ef","attrs":{"30f25bda40ef":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,2],"type":"bar","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3],"y":[1,3,2],"type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


```r
library(plotly)
data(iris)

fig <- plot_ly()%>%
  add_trace(data = iris, x = ~Sepal.Width, y = ~Sepal.Length, color = ~Species, 
               type = "scatter", mode = "markers")%>%
  layout(title="Using The add_trace() method With A Plotly Figure",  legend=list(title=list(text='species')),
         plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))%>%
  add_trace(x = c(2, 4), y = c(4, 8), type = "scatter", mode = "lines", line = list(color = 'grey')
            , showlegend = FALSE)
fig
```

<div id="htmlwidget-b7432503ee7785ce1c1b" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-b7432503ee7785ce1c1b">{"x":{"visdat":{"30f265b62bae":["function () ","plotlyVisDat"],"30f25972276d":["function () ","data"]},"cur_data":"30f25972276d","attrs":{"30f25972276d":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":{},"y":{},"color":{},"type":"scatter","mode":"markers","inherit":true},"30f25972276d.1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[2,4],"y":[4,8],"type":"scatter","mode":"lines","line":{"color":"grey"},"showlegend":false,"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Using The add_trace() method With A Plotly Figure","legend":{"title":{"text":"species"}},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":"Sepal.Width"},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":"Sepal.Length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[3.5,3,3.2,3.1,3.6,3.9,3.4,3.4,2.9,3.1,3.7,3.4,3,3,4,4.4,3.9,3.5,3.8,3.8,3.4,3.7,3.6,3.3,3.4,3,3.4,3.5,3.4,3.2,3.1,3.4,4.1,4.2,3.1,3.2,3.5,3.6,3,3.4,3.5,2.3,3.2,3.5,3.8,3,3.8,3.2,3.7,3.3],"y":[5.1,4.9,4.7,4.6,5,5.4,4.6,5,4.4,4.9,5.4,4.8,4.8,4.3,5.8,5.7,5.4,5.1,5.7,5.1,5.4,5.1,4.6,5.1,4.8,5,5,5.2,5.2,4.7,4.8,5.4,5.2,5.5,4.9,5,5.5,4.9,4.4,5.1,5,4.5,4.4,5,5.1,4.8,5.1,4.6,5.3,5],"type":"scatter","mode":"markers","name":"setosa","marker":{"color":"rgba(102,194,165,1)","line":{"color":"rgba(102,194,165,1)"}},"textfont":{"color":"rgba(102,194,165,1)"},"error_y":{"color":"rgba(102,194,165,1)"},"error_x":{"color":"rgba(102,194,165,1)"},"line":{"color":"rgba(102,194,165,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[3.2,3.2,3.1,2.3,2.8,2.8,3.3,2.4,2.9,2.7,2,3,2.2,2.9,2.9,3.1,3,2.7,2.2,2.5,3.2,2.8,2.5,2.8,2.9,3,2.8,3,2.9,2.6,2.4,2.4,2.7,2.7,3,3.4,3.1,2.3,3,2.5,2.6,3,2.6,2.3,2.7,3,2.9,2.9,2.5,2.8],"y":[7,6.4,6.9,5.5,6.5,5.7,6.3,4.9,6.6,5.2,5,5.9,6,6.1,5.6,6.7,5.6,5.8,6.2,5.6,5.9,6.1,6.3,6.1,6.4,6.6,6.8,6.7,6,5.7,5.5,5.5,5.8,6,5.4,6,6.7,6.3,5.6,5.5,5.5,6.1,5.8,5,5.6,5.7,5.7,6.2,5.1,5.7],"type":"scatter","mode":"markers","name":"versicolor","marker":{"color":"rgba(252,141,98,1)","line":{"color":"rgba(252,141,98,1)"}},"textfont":{"color":"rgba(252,141,98,1)"},"error_y":{"color":"rgba(252,141,98,1)"},"error_x":{"color":"rgba(252,141,98,1)"},"line":{"color":"rgba(252,141,98,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[3.3,2.7,3,2.9,3,3,2.5,2.9,2.5,3.6,3.2,2.7,3,2.5,2.8,3.2,3,3.8,2.6,2.2,3.2,2.8,2.8,2.7,3.3,3.2,2.8,3,2.8,3,2.8,3.8,2.8,2.8,2.6,3,3.4,3.1,3,3.1,3.1,3.1,2.7,3.2,3.3,3,2.5,3,3.4,3],"y":[6.3,5.8,7.1,6.3,6.5,7.6,4.9,7.3,6.7,7.2,6.5,6.4,6.8,5.7,5.8,6.4,6.5,7.7,7.7,6,6.9,5.6,7.7,6.3,6.7,7.2,6.2,6.1,6.4,7.2,7.4,7.9,6.4,6.3,6.1,7.7,6.3,6.4,6,6.9,6.7,6.9,5.8,6.8,6.7,6.7,6.3,6.5,6.2,5.9],"type":"scatter","mode":"markers","name":"virginica","marker":{"color":"rgba(141,160,203,1)","line":{"color":"rgba(141,160,203,1)"}},"textfont":{"color":"rgba(141,160,203,1)"},"error_y":{"color":"rgba(141,160,203,1)"},"error_x":{"color":"rgba(141,160,203,1)"},"line":{"color":"rgba(141,160,203,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[2,4],"y":[4,8],"type":"scatter","mode":"lines","line":{"color":"grey"},"showlegend":false,"marker":{"color":"rgba(214,39,40,1)","line":{"color":"rgba(214,39,40,1)"}},"error_y":{"color":"rgba(214,39,40,1)"},"error_x":{"color":"rgba(214,39,40,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Updating Figure Layouts

`plot_ly` figures support an `style()` method that may be used to update multiple nested properties of a figure's layout.

Here is an example of updating the font size of a figure's title using `style()`.


```r
library(plotly)

fig <- plot_ly(x = c(1, 2, 3), y = c(1, 3, 2), type = 'bar')%>%
  layout(title = list(text ='Using layout() With Plotly Figures', font = list(size = 17)),
         plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))
fig
```

<div id="htmlwidget-ef50dd24a58ebc721cfc" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-ef50dd24a58ebc721cfc">{"x":{"visdat":{"30f22be7c300":["function () ","plotlyVisDat"]},"cur_data":"30f22be7c300","attrs":{"30f22be7c300":{"x":[1,2,3],"y":[1,3,2],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":{"text":"Using layout() With Plotly Figures","font":{"size":17}},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3],"y":[1,3,2],"type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


#### Updating Traces

`plot_ly` figures support an `style()` method that may be used to update multiple nested properties of one or more of a figure's traces.

To show some examples, we will start with a figure that contains `bar` and `scatter` traces across two subplots.


```r
library(plotly)

fig1 <-  plot_ly(x = c(0,1, 2), y = c(2, 1, 3), type = 'bar', name = 'b', color = I("red")) %>%
  add_trace(x = c(0,1, 2), y = c(4, 2, 3.5), type = 'scatter', mode = 'markers', name = 'a',
            marker = list(size = 20, color = 'rgb(51, 204, 51)')) %>%
  layout(plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))

fig2 <-  plot_ly(x = c(0,1, 2), y = c(1, 3, 2), type = 'bar', name = 'c', color = I("#33cc33")) %>%
  add_trace(x = c(0,1, 2), y = c(2, 3.5, 4), type = 'scatter', mode = 'markers', name = 'd',
            marker = list(size = 20, color = 'rgb(255, 0, 0)')) %>%
  layout(plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))

fig <- subplot(fig1, fig2)
fig
```

<div id="htmlwidget-ab2da3ad3398f9fbeae2" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-ab2da3ad3398f9fbeae2">{"x":{"data":[{"x":[0,1,2],"y":[2,1,3],"name":"b","type":"bar","marker":{"color":"rgba(255,0,0,1)","line":{"color":"rgba(255,0,0,1)"}},"textfont":{"color":"rgba(255,0,0,1)"},"error_y":{"color":"rgba(255,0,0,1)"},"error_x":{"color":"rgba(255,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[0,1,2],"y":[4,2,3.5],"name":"a","type":"scatter","mode":"markers","marker":{"color":"rgb(51, 204, 51)","size":20,"line":{"color":"rgba(255,0,0,1)"}},"textfont":{"color":"rgba(255,0,0,1)"},"error_y":{"color":"rgba(255,0,0,1)"},"error_x":{"color":"rgba(255,0,0,1)"},"line":{"color":"rgba(255,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[0,1,2],"y":[1,3,2],"name":"c","type":"bar","marker":{"color":"rgba(51,204,51,1)","line":{"color":"rgba(51,204,51,1)"}},"textfont":{"color":"rgba(51,204,51,1)"},"error_y":{"color":"rgba(51,204,51,1)"},"error_x":{"color":"rgba(51,204,51,1)"},"xaxis":"x2","yaxis":"y2","frame":null},{"x":[0,1,2],"y":[2,3.5,4],"name":"d","type":"scatter","mode":"markers","marker":{"color":"rgb(255, 0, 0)","size":20,"line":{"color":"rgba(51,204,51,1)"}},"textfont":{"color":"rgba(51,204,51,1)"},"error_y":{"color":"rgba(51,204,51,1)"},"error_x":{"color":"rgba(51,204,51,1)"},"line":{"color":"rgba(51,204,51,1)"},"xaxis":"x2","yaxis":"y2","frame":null}],"layout":{"xaxis":{"domain":[0,0.48],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"y"},"xaxis2":{"domain":[0.52,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"y2"},"yaxis2":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"x2"},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"x"},"annotations":[],"shapes":[],"images":[],"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","hovermode":"closest","showlegend":true},"attrs":{"30f263bf6686":{"x":[0,1,2],"y":[2,1,3],"name":"b","color":["red"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"},"30f263bf6686.1":{"x":[0,1,2],"y":[4,2,3.5],"name":"a","color":["red"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"markers","marker":{"size":20,"color":"rgb(51, 204, 51)"},"inherit":true},"30f246abfc39":{"x":[0,1,2],"y":[1,3,2],"name":"c","color":["#33cc33"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"},"30f246abfc39.1":{"x":[0,1,2],"y":[2,3.5,4],"name":"d","color":["#33cc33"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"markers","marker":{"size":20,"color":"rgb(255, 0, 0)"},"inherit":true}},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"subplot":true,"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

Note that both `scatter` and `bar` traces have a `marker.color` property to control their coloring. Here is an example of using `style()` to modify the color of all traces.


```r
library(plotly)

fig1 <-  plot_ly(x = c(0,1, 2), y = c(2, 1, 3), type = 'bar', name = 'b', color = I("red")) %>%
  add_trace(x = c(0,1, 2), y = c(4, 2, 3.5), type = 'scatter', mode = 'markers', name = 'a',
            marker = list(size = 20, color = 'rgb(51, 204, 51)')) %>%
  layout(plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))

fig1 <- style(fig1, marker = list(size = 20, color = "blue"))

fig2 <-  plot_ly(x = c(0,1, 2), y = c(1, 3, 2), type = 'bar', name = 'c', color = I("#33cc33")) %>%
  add_trace(x = c(0,1, 2), y = c(2, 3.5, 4), type = 'scatter', mode = 'markers', name = 'd',
            marker = list(size = 20, color = 'rgb(255, 0, 0)')) %>%
  layout(plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))

fig2 <- style(fig1, marker = list(size = 20, color = "blue"))

fig <- subplot(fig1, fig2)
fig
```

<div id="htmlwidget-9b540baa354f782363a7" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-9b540baa354f782363a7">{"x":{"data":[{"x":[0,1,2],"y":[2,1,3],"name":"b","type":"bar","marker":{"size":20,"color":"blue"},"textfont":{"color":"rgba(255,0,0,1)"},"error_y":{"color":"rgba(255,0,0,1)"},"error_x":{"color":"rgba(255,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[0,1,2],"y":[4,2,3.5],"name":"a","type":"scatter","mode":"markers","marker":{"size":20,"color":"blue"},"textfont":{"color":"rgba(255,0,0,1)"},"error_y":{"color":"rgba(255,0,0,1)"},"error_x":{"color":"rgba(255,0,0,1)"},"line":{"color":"rgba(255,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[0,1,2],"y":[2,1,3],"name":"b","type":"bar","marker":{"size":20,"color":"blue"},"textfont":{"color":"rgba(255,0,0,1)"},"error_y":{"color":"rgba(255,0,0,1)"},"error_x":{"color":"rgba(255,0,0,1)"},"xaxis":"x2","yaxis":"y2","frame":null},{"x":[0,1,2],"y":[4,2,3.5],"name":"a","type":"scatter","mode":"markers","marker":{"size":20,"color":"blue"},"textfont":{"color":"rgba(255,0,0,1)"},"error_y":{"color":"rgba(255,0,0,1)"},"error_x":{"color":"rgba(255,0,0,1)"},"line":{"color":"rgba(255,0,0,1)"},"xaxis":"x2","yaxis":"y2","frame":null}],"layout":{"xaxis":{"domain":[0,0.48],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"y"},"xaxis2":{"domain":[0.52,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"y2"},"yaxis2":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"x2"},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"x"},"annotations":[],"shapes":[],"images":[],"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","hovermode":"closest","showlegend":true},"attrs":{"30f265814f24":{"x":[0,1,2],"y":[2,1,3],"name":"b","color":["red"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"},"30f265814f24.1":{"x":[0,1,2],"y":[4,2,3.5],"name":"a","color":["red"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"markers","marker":{"size":20,"color":"rgb(51, 204, 51)"},"inherit":true},"30f265814f24.2":{"x":[0,1,2],"y":[2,1,3],"name":"b","color":["red"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"},"30f265814f24.3":{"x":[0,1,2],"y":[4,2,3.5],"name":"a","color":["red"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"markers","marker":{"size":20,"color":"rgb(51, 204, 51)"},"inherit":true}},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"subplot":true,"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

The `style()` method supports a `traces` argument to control which traces should be updated. Only traces given  will be updated. Here is an example of using a traces to only update the color of the `bar` traces.


```r
library(plotly)

fig1 <-  plot_ly(x = c(0,1, 2), y = c(2, 1, 3), type = 'bar', name = 'b', color = I("red")) %>%
  add_trace(x = c(0,1, 2), y = c(4, 2, 3.5), type = 'scatter', mode = 'markers', name = 'a',
            marker = list(size = 20, color = 'rgb(51, 204, 51)')) %>%
  layout(plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))

fig1 <- style(fig1, marker = list(color = "blue"), traces = c(1))

fig2 <-  plot_ly(x = c(0,1, 2), y = c(1, 3, 2), type = 'bar', name = 'c', color = I("#33cc33")) %>%
  add_trace(x = c(0,1, 2), y = c(2, 3.5, 4), type = 'scatter', mode = 'markers', name = 'd',
            marker = list(size = 20, color = 'rgb(255, 80, 80)')) %>%
  layout(plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))

fig2 <- style(fig2, marker = list(color = "blue"), traces = c(1))

fig <- subplot(fig1, fig2)
fig
```

<div id="htmlwidget-43f5307e8bf121168e18" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-43f5307e8bf121168e18">{"x":{"data":[{"x":[0,1,2],"y":[2,1,3],"name":"b","type":"bar","marker":{"color":"blue"},"textfont":{"color":"rgba(255,0,0,1)"},"error_y":{"color":"rgba(255,0,0,1)"},"error_x":{"color":"rgba(255,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[0,1,2],"y":[4,2,3.5],"name":"a","type":"scatter","mode":"markers","marker":{"color":"rgb(51, 204, 51)","size":20,"line":{"color":"rgba(255,0,0,1)"}},"textfont":{"color":"rgba(255,0,0,1)"},"error_y":{"color":"rgba(255,0,0,1)"},"error_x":{"color":"rgba(255,0,0,1)"},"line":{"color":"rgba(255,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[0,1,2],"y":[1,3,2],"name":"c","type":"bar","marker":{"color":"blue"},"textfont":{"color":"rgba(51,204,51,1)"},"error_y":{"color":"rgba(51,204,51,1)"},"error_x":{"color":"rgba(51,204,51,1)"},"xaxis":"x2","yaxis":"y2","frame":null},{"x":[0,1,2],"y":[2,3.5,4],"name":"d","type":"scatter","mode":"markers","marker":{"color":"rgb(255, 80, 80)","size":20,"line":{"color":"rgba(51,204,51,1)"}},"textfont":{"color":"rgba(51,204,51,1)"},"error_y":{"color":"rgba(51,204,51,1)"},"error_x":{"color":"rgba(51,204,51,1)"},"line":{"color":"rgba(51,204,51,1)"},"xaxis":"x2","yaxis":"y2","frame":null}],"layout":{"xaxis":{"domain":[0,0.48],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"y"},"xaxis2":{"domain":[0.52,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"y2"},"yaxis2":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"x2"},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","anchor":"x"},"annotations":[],"shapes":[],"images":[],"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","hovermode":"closest","showlegend":true},"attrs":{"30f2484d8f00":{"x":[0,1,2],"y":[2,1,3],"name":"b","color":["red"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"},"30f2484d8f00.1":{"x":[0,1,2],"y":[4,2,3.5],"name":"a","color":["red"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"markers","marker":{"size":20,"color":"rgb(51, 204, 51)"},"inherit":true},"30f2422293f3":{"x":[0,1,2],"y":[1,3,2],"name":"c","color":["#33cc33"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"},"30f2422293f3.1":{"x":[0,1,2],"y":[2,3.5,4],"name":"d","color":["#33cc33"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"markers","marker":{"size":20,"color":"rgb(255, 80, 80)"},"inherit":true}},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"subplot":true,"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Overwrite Existing Properties When Using Update Methods

`style()` will overwrite the prior value of existing properties, with the provided value.

In the example below, the red color of markers is overwritten when updating `marker` in `style()`.


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 2), type = 'bar', marker = list(color = 'red')) %>%
  layout(plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))

style(fig, marker = list(opacity = 0.4))
```

<div id="htmlwidget-e951bb8aca86934d67c8" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e951bb8aca86934d67c8">{"x":{"visdat":{"30f25dbcf683":["function () ","plotlyVisDat"]},"cur_data":"30f25dbcf683","attrs":{"30f25dbcf683":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,2],"type":"bar","marker":{"color":"red"},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3],"y":[1,3,2],"type":"bar","marker":{"opacity":0.4},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Updating Figure Axes

Plotly figures support `layout` method that may be used to update multiple nested properties of one or more of a figure's axes. Here is an example of using `layout` to disable the vertical grid lines across all subplots in a figure produced by Plotly.


```r
library(plotly)
data(iris)

fig <- iris%>%
  group_by(Species) %>%
  do(p=plot_ly(., x = ~Sepal.Width, y = ~Sepal.Length, color = ~Species, type = "scatter", mode = "markers")) %>%
  subplot(nrows = 1, shareX = TRUE, shareY = TRUE)
fig <- fig%>%
  layout(title = "Updating x axis in a Plotly Figure", legend=list(title=list(text='species')),
         xaxis = list(showgrid = F), 
         xaxis2 = list(showgrid = F), 
         xaxis3 = list(showgrid = F),
         annotations = list(  
           list(  
             x = 0.16,   
             y = 0.95,   
             font = list(size = 10),   
             text = "species=setosa",   
             xref = "paper",   
             yref = "paper",   
             xanchor = "center",   
             yanchor = "bottom",   
             showarrow = FALSE  
           ),   
           list(  
             x = 0.5,   
             y = 0.95,   
             font = list(size = 10),   
             text = "species=versicolor",   
             xref = "paper",   
             yref = "paper",   
             xanchor = "center",   
             yanchor = "bottom",   
             showarrow = FALSE  
           ),   
           list(  
             x = 0.85,   
             y = 0.95,   
             font = list(size = 10),   
             text = "species=virginica",   
             xref = "paper",   
             yref = "paper",   
             xanchor = "center",   
             yanchor = "bottom",   
             showarrow = FALSE  
           )),
         plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))

fig
```

<div id="htmlwidget-28a5ca5c5f3f0cad12c4" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-28a5ca5c5f3f0cad12c4">{"x":{"data":[{"x":[3.5,3,3.2,3.1,3.6,3.9,3.4,3.4,2.9,3.1,3.7,3.4,3,3,4,4.4,3.9,3.5,3.8,3.8,3.4,3.7,3.6,3.3,3.4,3,3.4,3.5,3.4,3.2,3.1,3.4,4.1,4.2,3.1,3.2,3.5,3.6,3,3.4,3.5,2.3,3.2,3.5,3.8,3,3.8,3.2,3.7,3.3],"y":[5.1,4.9,4.7,4.6,5,5.4,4.6,5,4.4,4.9,5.4,4.8,4.8,4.3,5.8,5.7,5.4,5.1,5.7,5.1,5.4,5.1,4.6,5.1,4.8,5,5,5.2,5.2,4.7,4.8,5.4,5.2,5.5,4.9,5,5.5,4.9,4.4,5.1,5,4.5,4.4,5,5.1,4.8,5.1,4.6,5.3,5],"mode":"markers","type":"scatter","name":"setosa","marker":{"color":"rgba(102,194,165,1)","line":{"color":"rgba(102,194,165,1)"}},"textfont":{"color":"rgba(102,194,165,1)"},"error_y":{"color":"rgba(102,194,165,1)"},"error_x":{"color":"rgba(102,194,165,1)"},"line":{"color":"rgba(102,194,165,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[3.2,3.2,3.1,2.3,2.8,2.8,3.3,2.4,2.9,2.7,2,3,2.2,2.9,2.9,3.1,3,2.7,2.2,2.5,3.2,2.8,2.5,2.8,2.9,3,2.8,3,2.9,2.6,2.4,2.4,2.7,2.7,3,3.4,3.1,2.3,3,2.5,2.6,3,2.6,2.3,2.7,3,2.9,2.9,2.5,2.8],"y":[7,6.4,6.9,5.5,6.5,5.7,6.3,4.9,6.6,5.2,5,5.9,6,6.1,5.6,6.7,5.6,5.8,6.2,5.6,5.9,6.1,6.3,6.1,6.4,6.6,6.8,6.7,6,5.7,5.5,5.5,5.8,6,5.4,6,6.7,6.3,5.6,5.5,5.5,6.1,5.8,5,5.6,5.7,5.7,6.2,5.1,5.7],"mode":"markers","type":"scatter","name":"versicolor","marker":{"color":"rgba(252,141,98,1)","line":{"color":"rgba(252,141,98,1)"}},"textfont":{"color":"rgba(252,141,98,1)"},"error_y":{"color":"rgba(252,141,98,1)"},"error_x":{"color":"rgba(252,141,98,1)"},"line":{"color":"rgba(252,141,98,1)"},"xaxis":"x2","yaxis":"y","frame":null},{"x":[3.3,2.7,3,2.9,3,3,2.5,2.9,2.5,3.6,3.2,2.7,3,2.5,2.8,3.2,3,3.8,2.6,2.2,3.2,2.8,2.8,2.7,3.3,3.2,2.8,3,2.8,3,2.8,3.8,2.8,2.8,2.6,3,3.4,3.1,3,3.1,3.1,3.1,2.7,3.2,3.3,3,2.5,3,3.4,3],"y":[6.3,5.8,7.1,6.3,6.5,7.6,4.9,7.3,6.7,7.2,6.5,6.4,6.8,5.7,5.8,6.4,6.5,7.7,7.7,6,6.9,5.6,7.7,6.3,6.7,7.2,6.2,6.1,6.4,7.2,7.4,7.9,6.4,6.3,6.1,7.7,6.3,6.4,6,6.9,6.7,6.9,5.8,6.8,6.7,6.7,6.3,6.5,6.2,5.9],"mode":"markers","type":"scatter","name":"virginica","marker":{"color":"rgba(141,160,203,1)","line":{"color":"rgba(141,160,203,1)"}},"textfont":{"color":"rgba(141,160,203,1)"},"error_y":{"color":"rgba(141,160,203,1)"},"error_x":{"color":"rgba(141,160,203,1)"},"line":{"color":"rgba(141,160,203,1)"},"xaxis":"x3","yaxis":"y","frame":null}],"layout":{"xaxis":{"domain":[0,0.313333333333333],"automargin":true,"title":"Sepal.Width","anchor":"y","showgrid":false},"xaxis2":{"domain":[0.353333333333333,0.646666666666667],"automargin":true,"title":"Sepal.Width","anchor":"y","showgrid":false},"xaxis3":{"domain":[0.686666666666667,1],"automargin":true,"title":"Sepal.Width","anchor":"y","showgrid":false},"yaxis":{"domain":[0,1],"automargin":true,"title":"Sepal.Length","anchor":"x","zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff"},"annotations":[{"x":0.16,"y":0.95,"font":{"size":10},"text":"species=setosa","xref":"paper","yref":"paper","xanchor":"center","yanchor":"bottom","showarrow":false},{"x":0.5,"y":0.95,"font":{"size":10},"text":"species=versicolor","xref":"paper","yref":"paper","xanchor":"center","yanchor":"bottom","showarrow":false},{"x":0.85,"y":0.95,"font":{"size":10},"text":"species=virginica","xref":"paper","yref":"paper","xanchor":"center","yanchor":"bottom","showarrow":false}],"shapes":[],"images":[],"margin":{"b":40,"l":60,"t":25,"r":10},"hovermode":"closest","showlegend":true,"title":"Updating x axis in a Plotly Figure","legend":{"title":{"text":"species"}},"plot_bgcolor":"#e5ecf6"},"attrs":{"30f22dac5580":{"x":{},"y":{},"mode":"markers","color":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"},"30f27b9bdc34":{"x":{},"y":{},"mode":"markers","color":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"},"30f2652383da":{"x":{},"y":{},"mode":"markers","color":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"subplot":true,"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Other Update Methods

Figures created with the plotly graphing library also support:

  - the `images()` method in order to [update background layout images](https://plotly.com/r/displaying-images/),
  - `annotations()` in order to [update annotations](https://plotly.com/r/text-and-annotations/),
  - and `shapes()` in order to [update shapes](https://plotly.com/r/shapes/).

#### Chaining Figure Operations

All of the figure update operations described above are methods that return a reference to the figure being modified. This makes it possible to chain multiple figure modification operations together into a single expression.

Here is an example of a chained expression that:

  - sets the title font size using `layout.title.font.size`,
  - disables vertical grid lines using `layout.xaxis`,
  - updates the size and color of the markers and bar using `style()`,
  - and then displaying the figure.


```r
library(plotly) 

t <- list(size = 15)

fig <-  plot_ly(x = c(0,1, 2), y = c(2, 1, 3), type = 'bar', name = 'b', color = I("red")) %>% 
  add_trace(x = c(0,1, 2), y = c(4, 2, 3.5), type = 'scatter', mode = 'markers', name = 'a', 
            marker = list(size = 10, color = 'rgb(51, 204, 51)')) 
#updates the size and color of the markers and bar
fig <- style(fig, marker = list(size = 20, color = "blue")) 

fig <- style(fig, marker = list(color = "yellow"), traces = c(1)) 

fig <- style(fig, marker = list(color = "yellow", line = list(color = 'rgb(8,48,107)', 
                                                                width = 1.5)), traces = c(1)) 
fig <- fig %>%
  layout(title = list(text = "Chaining Multiple Figure Operations With A Plotly Figure",
#setting the title font size                      
                      font = t),
#disables vertical grid lines
         xaxis = list(showgrid = F),
plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))
#displaying the figure
fig 
```

<div id="htmlwidget-0a2b0ce9a6ba4a0a68e5" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-0a2b0ce9a6ba4a0a68e5">{"x":{"visdat":{"30f24892a6d2":["function () ","plotlyVisDat"]},"cur_data":"30f24892a6d2","attrs":{"30f24892a6d2":{"x":[0,1,2],"y":[2,1,3],"name":"b","color":["red"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"bar"},"30f24892a6d2.1":{"x":[0,1,2],"y":[4,2,3.5],"name":"a","color":["red"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter","mode":"markers","marker":{"size":10,"color":"rgb(51, 204, 51)"},"inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"title":[],"showgrid":false},"yaxis":{"domain":[0,1],"automargin":true,"title":[],"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff"},"hovermode":"closest","showlegend":true,"title":{"text":"Chaining Multiple Figure Operations With A Plotly Figure","font":{"size":15}},"plot_bgcolor":"#e5ecf6"},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[0,1,2],"y":[2,1,3],"name":"b","type":"bar","marker":{"color":"yellow","line":{"color":"rgb(8,48,107)","width":1.5}},"textfont":{"color":"rgba(255,0,0,1)"},"error_y":{"color":"rgba(255,0,0,1)"},"error_x":{"color":"rgba(255,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[0,1,2],"y":[4,2,3.5],"name":"a","type":"scatter","mode":"markers","marker":{"size":20,"color":"blue"},"textfont":{"color":"rgba(255,0,0,1)"},"error_y":{"color":"rgba(255,0,0,1)"},"error_x":{"color":"rgba(255,0,0,1)"},"line":{"color":"rgba(255,0,0,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#### Property Assignment

Trace and layout properties can be updated using property assignment syntax. Here is an example of setting the figure title using property assignment.


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 2), type = 'bar')%>%
  layout(title = 'Using Property Assignment Syntax With A Plotly Figure',
         plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))
fig <- style(fig,marker = list(line = list(color = 'lightblue', width = 0)))

fig
```

<div id="htmlwidget-50880edb20851716ed1b" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-50880edb20851716ed1b">{"x":{"visdat":{"30f26b89b959":["function () ","plotlyVisDat"]},"cur_data":"30f26b89b959","attrs":{"30f26b89b959":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,2],"type":"bar","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Using Property Assignment Syntax With A Plotly Figure","plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3],"y":[1,3,2],"type":"bar","marker":{"line":{"color":"lightblue","width":0}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

And here is an example of updating the bar outline using property assignment.


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 2), type = 'bar') %>%
  layout(plot_bgcolor='#e5ecf6', 
         xaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'), 
         yaxis = list( 
           zerolinecolor = '#ffff', 
           zerolinewidth = 2, 
           gridcolor = 'ffff'))
fig <- style(fig,marker = list(line = list(color = 'lightblue', width = 0)))
fig$x$data[[1]]$marker$line$color <- 'black'
fig$x$data[[1]]$marker$line$width <- 4

fig
```

<div id="htmlwidget-58b0a1e2294627ba54a5" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-58b0a1e2294627ba54a5">{"x":{"visdat":{"30f21a87a63b":["function () ","plotlyVisDat"]},"cur_data":"30f21a87a63b","attrs":{"30f21a87a63b":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,2],"type":"bar","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,2,3],"y":[1,3,2],"type":"bar","marker":{"line":{"color":"black","width":4}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### What About Dash?

[Dash for R](https://dashr.plot.ly/) is an open-source framework for building analytical applications, with no Javascript required, and it is tightly integrated with the Plotly graphing library. 

Learn about how to install Dash for R at https://dashr.plot.ly/installation.

Everywhere in this page that you see `fig`, you can display the same figure in a Dash for R application by passing it to the `figure` argument of the [`Graph` component](https://dashr.plot.ly/dash-core-components/graph) from the built-in `dashCoreComponents` package like this:


```r
library(plotly)

fig <- plot_ly() 
# fig <- fig %>% add_trace( ... )
# fig <- fig %>% layout( ... ) 

library(dash)
library(dashCoreComponents)
library(dashHtmlComponents)

app <- Dash$new()
app$layout(
    htmlDiv(
        list(
            dccGraph(figure=fig) 
        )
     )
)

app$run_server(debug=TRUE, dev_tools_hot_reload=FALSE)
```
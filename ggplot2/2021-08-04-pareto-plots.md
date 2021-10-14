---
description: How to make Pareto Plots in ggplot2 with Plotly.
name: Pareto Plots
permalink: ggplot2/pareto-plots/
thumnail_github: pareto-plots.png
layout: base
language: ggplot2
display_as: financial
page_type: u-guide
order: 9
output:
  html_document:
    keep_md: true
---



## Default pareto plot



```r
library(plotly)
require(ggQC)
require(ggplot2)

df <- data.frame(
                  x = letters[1:10],
                  y = as.integer(runif(n = 10, min = 0, max=100))
                 )

p <- ggplot(df, aes(x=x, y=y)) +
 stat_pareto(point.color = "red",
             point.size = 3,
             line.color = "black",
             #size.line = 1,
             bars.fill = c("blue", "orange"),
 )

ggplotly(p)
```

<div id="htmlwidget-368775cf5e08c4063ab2" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-368775cf5e08c4063ab2">{"x":{"data":[{"orientation":"v","width":0.9,"base":0,"x":[1],"y":[99],"text":"x: j<br />y: 99","type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(0,0,255,1)","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","mode":"","frame":null},{"orientation":"v","width":0.9,"base":0,"x":[2],"y":[81],"text":"x: i<br />y: 81","type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(28,18,226,1)","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","mode":"","frame":null},{"orientation":"v","width":0.9,"base":0,"x":[3],"y":[80],"text":"x: g<br />y: 80","type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(56,36,198,1)","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","mode":"","frame":null},{"orientation":"v","width":0.9,"base":0,"x":[4],"y":[72],"text":"x: c<br />y: 72","type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(85,55,170,1)","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","mode":"","frame":null},{"orientation":"v","width":0.9,"base":0,"x":[5],"y":[63],"text":"x: h<br />y: 63","type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(113,73,141,1)","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","mode":"","frame":null},{"orientation":"v","width":0.9,"base":0,"x":[6],"y":[34],"text":"x: d<br />y: 34","type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(141,91,113,1)","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","mode":"","frame":null},{"orientation":"v","width":0.9,"base":0,"x":[7],"y":[29],"text":"x: b<br />y: 29","type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(170,110,85,1)","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","mode":"","frame":null},{"orientation":"v","width":0.899999999999999,"base":0,"x":[8],"y":[28],"text":"x: f<br />y: 28","type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(198,128,56,1)","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","mode":"","frame":null},{"orientation":"v","width":0.899999999999999,"base":0,"x":[9],"y":[22],"text":"x: e<br />y: 22","type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(226,146,28,1)","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","mode":"","frame":null},{"orientation":"v","width":0.899999999999999,"base":0,"x":[10],"y":[20],"text":"x: a<br />y: 20","type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(255,165,0,1)","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","mode":"","frame":null},{"x":[1,2,3,4,5,6,7,8,9,10],"y":[99,180,260,332,395,429,458,486,508,528],"text":["x: j<br />y: 99","x: i<br />y: 81","x: g<br />y: 80","x: c<br />y: 72","x: h<br />y: 63","x: d<br />y: 34","x: b<br />y: 29","x: f<br />y: 28","x: e<br />y: 22","x: a<br />y: 20"],"type":"scatter","mode":"lines+markers","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","marker":{"autocolorscale":false,"color":"rgba(255,0,0,1)","opacity":1,"size":11.3385826771654,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(255,0,0,1)"}},"frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":43.1050228310502},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,10.6],"tickmode":"array","ticktext":["j","i","g","c","h","d","b","f","e","a"],"tickvals":[1,2,3,4,5,6,7,8,9,10],"categoryorder":"array","categoryarray":["j","i","g","c","h","d","b","f","e","a"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"x","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-26.4,554.4],"tickmode":"array","ticktext":["0","200","400"],"tickvals":[0,200,400],"categoryorder":"array","categoryarray":["0","200","400"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"y","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"40d6434c0ec9":{"x":{},"y":{},"type":"bar"},"40d64062d849":{"x":{},"y":{}},"40d6d1853b8":{"x":{},"y":{}}},"cur_data":"40d6434c0ec9","visdat":{"40d6434c0ec9":["function (y) ","x"],"40d64062d849":["function (y) ","x"],"40d6d1853b8":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>



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

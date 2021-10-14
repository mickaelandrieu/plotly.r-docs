---
description: How to add Horizontal and Vertical Lines in ggplot2 with Plotly.
name: Horizontal and Vertical Lines
permalink: ggplot2/horizontal-vertical-shapes/
thumnail_github: horizontal-vertical-shapes.png
layout: base
language: ggplot2
display_as: file_settings
page_type: u-guide
order: 36
output:
  html_document:
    keep_md: true
---



## Add horizontal line

To do this, use `geom_vline()`:

```r
library(plotly)
library(ggplot2)

p <- ggplot(data=mtcars, aes(x=wt, y=mpg)) + geom_point() +
      geom_vline(xintercept = 3)

ggplotly(p)
```

<div id="htmlwidget-5b642e57ff83ee2d8c04" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-5b642e57ff83ee2d8c04">{"x":{"data":[{"x":[2.62,2.875,2.32,3.215,3.44,3.46,3.57,3.19,3.15,3.44,3.44,4.07,3.73,3.78,5.25,5.424,5.345,2.2,1.615,1.835,2.465,3.52,3.435,3.84,3.845,1.935,2.14,1.513,3.17,2.77,3.57,2.78],"y":[21,21,22.8,21.4,18.7,18.1,14.3,24.4,22.8,19.2,17.8,16.4,17.3,15.2,10.4,10.4,14.7,32.4,30.4,33.9,21.5,15.5,15.2,13.3,19.2,27.3,26,30.4,15.8,19.7,15,21.4],"text":["wt: 2.620<br />mpg: 21.0","wt: 2.875<br />mpg: 21.0","wt: 2.320<br />mpg: 22.8","wt: 3.215<br />mpg: 21.4","wt: 3.440<br />mpg: 18.7","wt: 3.460<br />mpg: 18.1","wt: 3.570<br />mpg: 14.3","wt: 3.190<br />mpg: 24.4","wt: 3.150<br />mpg: 22.8","wt: 3.440<br />mpg: 19.2","wt: 3.440<br />mpg: 17.8","wt: 4.070<br />mpg: 16.4","wt: 3.730<br />mpg: 17.3","wt: 3.780<br />mpg: 15.2","wt: 5.250<br />mpg: 10.4","wt: 5.424<br />mpg: 10.4","wt: 5.345<br />mpg: 14.7","wt: 2.200<br />mpg: 32.4","wt: 1.615<br />mpg: 30.4","wt: 1.835<br />mpg: 33.9","wt: 2.465<br />mpg: 21.5","wt: 3.520<br />mpg: 15.5","wt: 3.435<br />mpg: 15.2","wt: 3.840<br />mpg: 13.3","wt: 3.845<br />mpg: 19.2","wt: 1.935<br />mpg: 27.3","wt: 2.140<br />mpg: 26.0","wt: 1.513<br />mpg: 30.4","wt: 3.170<br />mpg: 15.8","wt: 2.770<br />mpg: 19.7","wt: 3.570<br />mpg: 15.0","wt: 2.780<br />mpg: 21.4"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[3,3],"y":[9.225,35.075],"text":"xintercept: 3","type":"scatter","mode":"lines","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":37.2602739726027},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[1.31745,5.61955],"tickmode":"array","ticktext":["2","3","4","5"],"tickvals":[2,3,4,5],"categoryorder":"array","categoryarray":["2","3","4","5"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"wt","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[9.225,35.075],"tickmode":"array","ticktext":["10","15","20","25","30","35"],"tickvals":[10,15,20,25,30,35],"categoryorder":"array","categoryarray":["10","15","20","25","30","35"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"mpg","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"3d7b3d189138":{"x":{},"y":{},"type":"scatter"},"3d7b3e0db82e":{"xintercept":{}}},"cur_data":"3d7b3d189138","visdat":{"3d7b3d189138":["function (y) ","x"],"3d7b3e0db82e":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


## Add vertical line

To do this, use `geom_hline()`:

```r
library(plotly)
library(ggplot2)

p <- ggplot(data=mtcars, aes(x=wt, y=mpg)) + 
      geom_point() +
      geom_hline(yintercept=20)

ggplotly(p)
```

<div id="htmlwidget-c473ecc7cf99e4888ef1" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c473ecc7cf99e4888ef1">{"x":{"data":[{"x":[2.62,2.875,2.32,3.215,3.44,3.46,3.57,3.19,3.15,3.44,3.44,4.07,3.73,3.78,5.25,5.424,5.345,2.2,1.615,1.835,2.465,3.52,3.435,3.84,3.845,1.935,2.14,1.513,3.17,2.77,3.57,2.78],"y":[21,21,22.8,21.4,18.7,18.1,14.3,24.4,22.8,19.2,17.8,16.4,17.3,15.2,10.4,10.4,14.7,32.4,30.4,33.9,21.5,15.5,15.2,13.3,19.2,27.3,26,30.4,15.8,19.7,15,21.4],"text":["wt: 2.620<br />mpg: 21.0","wt: 2.875<br />mpg: 21.0","wt: 2.320<br />mpg: 22.8","wt: 3.215<br />mpg: 21.4","wt: 3.440<br />mpg: 18.7","wt: 3.460<br />mpg: 18.1","wt: 3.570<br />mpg: 14.3","wt: 3.190<br />mpg: 24.4","wt: 3.150<br />mpg: 22.8","wt: 3.440<br />mpg: 19.2","wt: 3.440<br />mpg: 17.8","wt: 4.070<br />mpg: 16.4","wt: 3.730<br />mpg: 17.3","wt: 3.780<br />mpg: 15.2","wt: 5.250<br />mpg: 10.4","wt: 5.424<br />mpg: 10.4","wt: 5.345<br />mpg: 14.7","wt: 2.200<br />mpg: 32.4","wt: 1.615<br />mpg: 30.4","wt: 1.835<br />mpg: 33.9","wt: 2.465<br />mpg: 21.5","wt: 3.520<br />mpg: 15.5","wt: 3.435<br />mpg: 15.2","wt: 3.840<br />mpg: 13.3","wt: 3.845<br />mpg: 19.2","wt: 1.935<br />mpg: 27.3","wt: 2.140<br />mpg: 26.0","wt: 1.513<br />mpg: 30.4","wt: 3.170<br />mpg: 15.8","wt: 2.770<br />mpg: 19.7","wt: 3.570<br />mpg: 15.0","wt: 2.780<br />mpg: 21.4"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1.31745,5.61955],"y":[20,20],"text":"yintercept: 20","type":"scatter","mode":"lines","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":37.2602739726027},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[1.31745,5.61955],"tickmode":"array","ticktext":["2","3","4","5"],"tickvals":[2,3,4,5],"categoryorder":"array","categoryarray":["2","3","4","5"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"wt","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[9.225,35.075],"tickmode":"array","ticktext":["10","15","20","25","30","35"],"tickvals":[10,15,20,25,30,35],"categoryorder":"array","categoryarray":["10","15","20","25","30","35"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"mpg","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"3d7b3369e096":{"x":{},"y":{},"type":"scatter"},"3d7b74356b4d":{"yintercept":{}}},"cur_data":"3d7b3369e096","visdat":{"3d7b3369e096":["function (y) ","x"],"3d7b74356b4d":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>



## Change line type



```r
library(plotly)
library(ggplot2)

p <- ggplot(data=mtcars, aes(x=wt, y=mpg)) + 
      geom_point() +
      geom_vline(xintercept = 3, linetype="dotted", 
                color = "blue", size=1.5)

ggplotly(p)
```

<div id="htmlwidget-6d008f0eb9b17791d160" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-6d008f0eb9b17791d160">{"x":{"data":[{"x":[2.62,2.875,2.32,3.215,3.44,3.46,3.57,3.19,3.15,3.44,3.44,4.07,3.73,3.78,5.25,5.424,5.345,2.2,1.615,1.835,2.465,3.52,3.435,3.84,3.845,1.935,2.14,1.513,3.17,2.77,3.57,2.78],"y":[21,21,22.8,21.4,18.7,18.1,14.3,24.4,22.8,19.2,17.8,16.4,17.3,15.2,10.4,10.4,14.7,32.4,30.4,33.9,21.5,15.5,15.2,13.3,19.2,27.3,26,30.4,15.8,19.7,15,21.4],"text":["wt: 2.620<br />mpg: 21.0","wt: 2.875<br />mpg: 21.0","wt: 2.320<br />mpg: 22.8","wt: 3.215<br />mpg: 21.4","wt: 3.440<br />mpg: 18.7","wt: 3.460<br />mpg: 18.1","wt: 3.570<br />mpg: 14.3","wt: 3.190<br />mpg: 24.4","wt: 3.150<br />mpg: 22.8","wt: 3.440<br />mpg: 19.2","wt: 3.440<br />mpg: 17.8","wt: 4.070<br />mpg: 16.4","wt: 3.730<br />mpg: 17.3","wt: 3.780<br />mpg: 15.2","wt: 5.250<br />mpg: 10.4","wt: 5.424<br />mpg: 10.4","wt: 5.345<br />mpg: 14.7","wt: 2.200<br />mpg: 32.4","wt: 1.615<br />mpg: 30.4","wt: 1.835<br />mpg: 33.9","wt: 2.465<br />mpg: 21.5","wt: 3.520<br />mpg: 15.5","wt: 3.435<br />mpg: 15.2","wt: 3.840<br />mpg: 13.3","wt: 3.845<br />mpg: 19.2","wt: 1.935<br />mpg: 27.3","wt: 2.140<br />mpg: 26.0","wt: 1.513<br />mpg: 30.4","wt: 3.170<br />mpg: 15.8","wt: 2.770<br />mpg: 19.7","wt: 3.570<br />mpg: 15.0","wt: 2.780<br />mpg: 21.4"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[3,3],"y":[9.225,35.075],"text":"xintercept: 3","type":"scatter","mode":"lines","line":{"width":5.66929133858268,"color":"rgba(0,0,255,1)","dash":"dot"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":37.2602739726027},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[1.31745,5.61955],"tickmode":"array","ticktext":["2","3","4","5"],"tickvals":[2,3,4,5],"categoryorder":"array","categoryarray":["2","3","4","5"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"wt","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[9.225,35.075],"tickmode":"array","ticktext":["10","15","20","25","30","35"],"tickvals":[10,15,20,25,30,35],"categoryorder":"array","categoryarray":["10","15","20","25","30","35"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"mpg","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"3d7b9f7a224":{"x":{},"y":{},"type":"scatter"},"3d7b3655b66a":{"xintercept":{}}},"cur_data":"3d7b9f7a224","visdat":{"3d7b9f7a224":["function (y) ","x"],"3d7b3655b66a":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>




```r
library(plotly)
library(ggplot2)

p <- ggplot(data=mtcars, aes(x=wt, y=mpg)) + 
      geom_point() +
      geom_hline(yintercept=20, linetype="dashed", 
              color = "green", size=4)

ggplotly(p)
```

<div id="htmlwidget-f1e5ae3558d5c210af8f" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-f1e5ae3558d5c210af8f">{"x":{"data":[{"x":[2.62,2.875,2.32,3.215,3.44,3.46,3.57,3.19,3.15,3.44,3.44,4.07,3.73,3.78,5.25,5.424,5.345,2.2,1.615,1.835,2.465,3.52,3.435,3.84,3.845,1.935,2.14,1.513,3.17,2.77,3.57,2.78],"y":[21,21,22.8,21.4,18.7,18.1,14.3,24.4,22.8,19.2,17.8,16.4,17.3,15.2,10.4,10.4,14.7,32.4,30.4,33.9,21.5,15.5,15.2,13.3,19.2,27.3,26,30.4,15.8,19.7,15,21.4],"text":["wt: 2.620<br />mpg: 21.0","wt: 2.875<br />mpg: 21.0","wt: 2.320<br />mpg: 22.8","wt: 3.215<br />mpg: 21.4","wt: 3.440<br />mpg: 18.7","wt: 3.460<br />mpg: 18.1","wt: 3.570<br />mpg: 14.3","wt: 3.190<br />mpg: 24.4","wt: 3.150<br />mpg: 22.8","wt: 3.440<br />mpg: 19.2","wt: 3.440<br />mpg: 17.8","wt: 4.070<br />mpg: 16.4","wt: 3.730<br />mpg: 17.3","wt: 3.780<br />mpg: 15.2","wt: 5.250<br />mpg: 10.4","wt: 5.424<br />mpg: 10.4","wt: 5.345<br />mpg: 14.7","wt: 2.200<br />mpg: 32.4","wt: 1.615<br />mpg: 30.4","wt: 1.835<br />mpg: 33.9","wt: 2.465<br />mpg: 21.5","wt: 3.520<br />mpg: 15.5","wt: 3.435<br />mpg: 15.2","wt: 3.840<br />mpg: 13.3","wt: 3.845<br />mpg: 19.2","wt: 1.935<br />mpg: 27.3","wt: 2.140<br />mpg: 26.0","wt: 1.513<br />mpg: 30.4","wt: 3.170<br />mpg: 15.8","wt: 2.770<br />mpg: 19.7","wt: 3.570<br />mpg: 15.0","wt: 2.780<br />mpg: 21.4"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1.31745,5.61955],"y":[20,20],"text":"yintercept: 20","type":"scatter","mode":"lines","line":{"width":15.1181102362205,"color":"rgba(0,255,0,1)","dash":"dash"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":37.2602739726027},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[1.31745,5.61955],"tickmode":"array","ticktext":["2","3","4","5"],"tickvals":[2,3,4,5],"categoryorder":"array","categoryarray":["2","3","4","5"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"wt","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[9.225,35.075],"tickmode":"array","ticktext":["10","15","20","25","30","35"],"tickvals":[10,15,20,25,30,35],"categoryorder":"array","categoryarray":["10","15","20","25","30","35"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"mpg","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"3d7b5e7f9b97":{"x":{},"y":{},"type":"scatter"},"3d7b75dee512":{"yintercept":{}}},"cur_data":"3d7b5e7f9b97","visdat":{"3d7b5e7f9b97":["function (y) ","x"],"3d7b75dee512":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>



## Add a segment line

If you do not wish to add line that goes across the whole plot, use `geom_segment()`:

```r
library(plotly)
library(ggplot2)

p <- ggplot(data=mtcars, aes(x=wt, y=mpg)) + 
      geom_point() +
      geom_segment(aes(x = 4, y = 15, xend = 4, yend = 27))

ggplotly(p)
```

<div id="htmlwidget-c3ce77642260ba89fd82" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c3ce77642260ba89fd82">{"x":{"data":[{"x":[2.62,2.875,2.32,3.215,3.44,3.46,3.57,3.19,3.15,3.44,3.44,4.07,3.73,3.78,5.25,5.424,5.345,2.2,1.615,1.835,2.465,3.52,3.435,3.84,3.845,1.935,2.14,1.513,3.17,2.77,3.57,2.78],"y":[21,21,22.8,21.4,18.7,18.1,14.3,24.4,22.8,19.2,17.8,16.4,17.3,15.2,10.4,10.4,14.7,32.4,30.4,33.9,21.5,15.5,15.2,13.3,19.2,27.3,26,30.4,15.8,19.7,15,21.4],"text":["wt: 2.620<br />mpg: 21.0","wt: 2.875<br />mpg: 21.0","wt: 2.320<br />mpg: 22.8","wt: 3.215<br />mpg: 21.4","wt: 3.440<br />mpg: 18.7","wt: 3.460<br />mpg: 18.1","wt: 3.570<br />mpg: 14.3","wt: 3.190<br />mpg: 24.4","wt: 3.150<br />mpg: 22.8","wt: 3.440<br />mpg: 19.2","wt: 3.440<br />mpg: 17.8","wt: 4.070<br />mpg: 16.4","wt: 3.730<br />mpg: 17.3","wt: 3.780<br />mpg: 15.2","wt: 5.250<br />mpg: 10.4","wt: 5.424<br />mpg: 10.4","wt: 5.345<br />mpg: 14.7","wt: 2.200<br />mpg: 32.4","wt: 1.615<br />mpg: 30.4","wt: 1.835<br />mpg: 33.9","wt: 2.465<br />mpg: 21.5","wt: 3.520<br />mpg: 15.5","wt: 3.435<br />mpg: 15.2","wt: 3.840<br />mpg: 13.3","wt: 3.845<br />mpg: 19.2","wt: 1.935<br />mpg: 27.3","wt: 2.140<br />mpg: 26.0","wt: 1.513<br />mpg: 30.4","wt: 3.170<br />mpg: 15.8","wt: 2.770<br />mpg: 19.7","wt: 3.570<br />mpg: 15.0","wt: 2.780<br />mpg: 21.4"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4,null,4,4],"y":[15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27,null,15,27],"text":"x: 4<br />y: 15<br />xend: 4<br />yend: 27","type":"scatter","mode":"lines","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":37.2602739726027},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[1.31745,5.61955],"tickmode":"array","ticktext":["2","3","4","5"],"tickvals":[2,3,4,5],"categoryorder":"array","categoryarray":["2","3","4","5"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"wt","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[9.225,35.075],"tickmode":"array","ticktext":["10","15","20","25","30","35"],"tickvals":[10,15,20,25,30,35],"categoryorder":"array","categoryarray":["10","15","20","25","30","35"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"mpg","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"3d7b229c9c9d":{"x":{},"y":{},"type":"scatter"},"3d7b77b5b6ba":{"x":{},"y":{},"xend":{},"yend":{}}},"cur_data":"3d7b229c9c9d","visdat":{"3d7b229c9c9d":["function (y) ","x"],"3d7b77b5b6ba":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>



## Adding regression line



```r
library(plotly)
library(ggplot2)
require(stats)

reg <- lm(mpg ~ wt, data = mtcars)
coeff = coefficients(reg)

eq = paste0("y = ", round(coeff[2],1), "*x + ", round(coeff[1],1))

p <- ggplot(data=mtcars, aes(x=wt, y=mpg)) + geom_point() +
      geom_abline(intercept = 37, slope = -5, color="red", 
                 linetype="dashed", size=1.5)+
      ggtitle(eq)

ggplotly(p)
```

<div id="htmlwidget-6590db029f00884ab081" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-6590db029f00884ab081">{"x":{"data":[{"x":[2.62,2.875,2.32,3.215,3.44,3.46,3.57,3.19,3.15,3.44,3.44,4.07,3.73,3.78,5.25,5.424,5.345,2.2,1.615,1.835,2.465,3.52,3.435,3.84,3.845,1.935,2.14,1.513,3.17,2.77,3.57,2.78],"y":[21,21,22.8,21.4,18.7,18.1,14.3,24.4,22.8,19.2,17.8,16.4,17.3,15.2,10.4,10.4,14.7,32.4,30.4,33.9,21.5,15.5,15.2,13.3,19.2,27.3,26,30.4,15.8,19.7,15,21.4],"text":["wt: 2.620<br />mpg: 21.0","wt: 2.875<br />mpg: 21.0","wt: 2.320<br />mpg: 22.8","wt: 3.215<br />mpg: 21.4","wt: 3.440<br />mpg: 18.7","wt: 3.460<br />mpg: 18.1","wt: 3.570<br />mpg: 14.3","wt: 3.190<br />mpg: 24.4","wt: 3.150<br />mpg: 22.8","wt: 3.440<br />mpg: 19.2","wt: 3.440<br />mpg: 17.8","wt: 4.070<br />mpg: 16.4","wt: 3.730<br />mpg: 17.3","wt: 3.780<br />mpg: 15.2","wt: 5.250<br />mpg: 10.4","wt: 5.424<br />mpg: 10.4","wt: 5.345<br />mpg: 14.7","wt: 2.200<br />mpg: 32.4","wt: 1.615<br />mpg: 30.4","wt: 1.835<br />mpg: 33.9","wt: 2.465<br />mpg: 21.5","wt: 3.520<br />mpg: 15.5","wt: 3.435<br />mpg: 15.2","wt: 3.840<br />mpg: 13.3","wt: 3.845<br />mpg: 19.2","wt: 1.935<br />mpg: 27.3","wt: 2.140<br />mpg: 26.0","wt: 1.513<br />mpg: 30.4","wt: 3.170<br />mpg: 15.8","wt: 2.770<br />mpg: 19.7","wt: 3.570<br />mpg: 15.0","wt: 2.780<br />mpg: 21.4"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1.31745,5.61955],"y":[30.41275,8.90225],"text":"intercept: 37<br />slope: -5","type":"scatter","mode":"lines","line":{"width":5.66929133858268,"color":"rgba(255,0,0,1)","dash":"dash"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":37.2602739726027},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":{"text":"y = -5.3*x + 37.3","font":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"x":0,"xref":"paper"},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[1.31745,5.61955],"tickmode":"array","ticktext":["2","3","4","5"],"tickvals":[2,3,4,5],"categoryorder":"array","categoryarray":["2","3","4","5"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"wt","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[9.225,35.075],"tickmode":"array","ticktext":["10","15","20","25","30","35"],"tickvals":[10,15,20,25,30,35],"categoryorder":"array","categoryarray":["10","15","20","25","30","35"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"mpg","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"3d7b3c2c6c0f":{"x":{},"y":{},"type":"scatter"},"3d7b7227f6b7":{"intercept":{},"slope":{}}},"cur_data":"3d7b3c2c6c0f","visdat":{"3d7b3c2c6c0f":["function (y) ","x"],"3d7b7227f6b7":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>




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

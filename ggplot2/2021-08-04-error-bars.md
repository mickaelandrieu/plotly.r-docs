---
name: Error Bars
permalink: ggplot2/error-bars/
description: How to make Error Plots in ggplot2 with Plotly.
layout: base
thumnail_github: error-bars.png
language: ggplot2
page_type: u-guide
display_as: statistical
order: 1
output:
  html_document:
    keep_md: true
---


### Basic Error Bar


```r
library(plotly)

df <- data.frame(x = 1:10,
                 y = 1:10,
                 ymin = (1:10) - runif(10),
                 ymax = (1:10) + runif(10),
                 xmin = (1:10) - runif(10),
                 xmax = (1:10) + runif(10))

p <- ggplot(data = df,aes(x = x,y = y)) + 
    geom_point() + 
    geom_errorbar(aes(ymin = ymin,ymax = ymax)) + 
    geom_errorbarh(aes(xmin = xmin,xmax = xmax))

ggplotly(p)
```

<div id="htmlwidget-354dae0fe28ae7ff111e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-354dae0fe28ae7ff111e">{"x":{"data":[{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["x:  1<br />y:  1","x:  2<br />y:  2","x:  3<br />y:  3","x:  4<br />y:  4","x:  5<br />y:  5","x:  6<br />y:  6","x:  7<br />y:  7","x:  8<br />y:  8","x:  9<br />y:  9","x: 10<br />y: 10"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["x:  1<br />y:  1<br />ymin: 0.3896931<br />ymax:  1.377029","x:  2<br />y:  2<br />ymin: 1.4744963<br />ymax:  2.931911","x:  3<br />y:  3<br />ymin: 2.3216634<br />ymax:  3.616880","x:  4<br />y:  4<br />ymin: 3.3234176<br />ymax:  4.612293","x:  5<br />y:  5<br />ymin: 4.8536372<br />ymax:  5.204000","x:  6<br />y:  6<br />ymin: 5.3964759<br />ymax:  6.868879","x:  7<br />y:  7<br />ymin: 6.7983516<br />ymax:  7.082701","x:  8<br />y:  8<br />ymin: 7.0600632<br />ymax:  8.411480","x:  9<br />y:  9<br />ymin: 8.2532156<br />ymax:  9.168643","x: 10<br />y: 10<br />ymin: 9.6392839<br />ymax: 10.664508"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_y":{"array":[0.37702873791568,0.931911423802376,0.616880260640755,0.61229345202446,0.203999989200383,0.868878640467301,0.0827014483511448,0.411480247043073,0.168643156066537,0.664508118759841],"arrayminus":[0.610306879039854,0.525503735523671,0.678336607525125,0.676582439336926,0.146362804807723,0.603524090256542,0.201648358255625,0.939936845796183,0.746784368297085,0.360716080991551],"type":"data","width":17.6876741037653,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1,2,3,4,5,6,7,8,9,10],"y":[1,2,3,4,5,6,7,8,9,10],"text":["x:  1<br />y:  1<br />xmin: 0.08839303<br />xmax:  1.227229","x:  2<br />y:  2<br />xmin: 1.50158645<br />xmax:  2.389783","x:  3<br />y:  3<br />xmin: 2.26364865<br />xmax:  3.924547","x:  4<br />y:  4<br />xmin: 3.74458767<br />xmax:  4.596915","x:  5<br />y:  5<br />xmin: 4.28271203<br />xmax:  5.350305","x:  6<br />y:  6<br />xmin: 5.96766458<br />xmax:  6.682591","x:  7<br />y:  7<br />xmin: 6.90210959<br />xmax:  7.728327","x:  8<br />y:  8<br />xmin: 7.66850069<br />xmax:  8.763372","x:  9<br />y:  9<br />xmin: 8.48125417<br />xmax:  9.664494","x: 10<br />y: 10<br />xmin: 9.12459135<br />xmax: 10.230749"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_x":{"array":[0.227228995878249,0.389782707206905,0.924547031987458,0.596914724446833,0.350305147469044,0.682591478573158,0.728326573735103,0.763371856883168,0.66449438338168,0.230748878559098],"arrayminus":[0.911606969777495,0.498413550434634,0.736351348925382,0.255412334343418,0.717287965584546,0.0323354243300855,0.0978904059156775,0.33149931114167,0.518745834939182,0.875408652704209],"type":"data","width":12.7407735260561,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":31.4155251141553},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-0.429687318266369,10.9680803484889],"tickmode":"array","ticktext":["0.0","2.5","5.0","7.5","10.0"],"tickvals":[5.55111512312578e-17,2.5,5,7.5,10],"categoryorder":"array","categoryarray":["0.0","2.5","5.0","7.5","10.0"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"x","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-0.124047628929839,11.1782488686498],"tickmode":"array","ticktext":["0","3","6","9"],"tickvals":[1.38777878078145e-17,3,6,9],"categoryorder":"array","categoryarray":["0","3","6","9"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"y","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"3ae920645b17":{"x":{},"y":{},"type":"scatter"},"3ae964b3377a":{"x":{},"y":{},"ymin":{},"ymax":{}},"3ae971d83875":{"x":{},"y":{},"xmin":{},"xmax":{}}},"cur_data":"3ae920645b17","visdat":{"3ae920645b17":["function (y) ","x"],"3ae964b3377a":["function (y) ","x"],"3ae971d83875":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Margin Error Bar


```r
library(plotly)

population <- data.frame(Year=seq(1790, 1970, length.out=length(uspop)), 
                         Population=uspop, 
                         Error=rnorm(length(uspop), 5))

library(ggplot2)
p <- ggplot(population, aes(x=Year, y=Population, 
                       ymin=Population-Error, ymax=Population+Error))+
  geom_line()+
  geom_point(pch=2)+
  geom_errorbar(width=0.9)

ggplotly(p)
```

<div id="htmlwidget-eb12ed26afa300cdd29e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-eb12ed26afa300cdd29e">{"x":{"data":[{"x":[1790,1800,1810,1820,1830,1840,1850,1860,1870,1880,1890,1900,1910,1920,1930,1940,1950,1960,1970],"y":[3.93,5.31,7.24,9.64,12.9,17.1,23.2,31.4,39.8,50.2,62.9,76,92,105.7,122.8,131.7,151.3,179.3,203.2],"text":["Year: 1790<br />Population:   3.93<br />Population - Error:  -0.8349199<br />Population + Error:   8.694920","Year: 1800<br />Population:   5.31<br />Population - Error:   1.1040065<br />Population + Error:   9.515994","Year: 1810<br />Population:   7.24<br />Population - Error:   2.5909079<br />Population + Error:  11.889092","Year: 1820<br />Population:   9.64<br />Population - Error:   5.2672517<br />Population + Error:  14.012748","Year: 1830<br />Population:  12.90<br />Population - Error:   6.5067279<br />Population + Error:  19.293272","Year: 1840<br />Population:  17.10<br />Population - Error:  11.0411811<br />Population + Error:  23.158819","Year: 1850<br />Population:  23.20<br />Population - Error:  19.4525387<br />Population + Error:  26.947461","Year: 1860<br />Population:  31.40<br />Population - Error:  26.0222091<br />Population + Error:  36.777791","Year: 1870<br />Population:  39.80<br />Population - Error:  34.9970756<br />Population + Error:  44.602924","Year: 1880<br />Population:  50.20<br />Population - Error:  44.5996331<br />Population + Error:  55.800367","Year: 1890<br />Population:  62.90<br />Population - Error:  56.2737536<br />Population + Error:  69.526246","Year: 1900<br />Population:  76.00<br />Population - Error:  71.2156833<br />Population + Error:  80.784317","Year: 1910<br />Population:  92.00<br />Population - Error:  88.4072146<br />Population + Error:  95.592785","Year: 1920<br />Population: 105.70<br />Population - Error: 100.2324846<br />Population + Error: 111.167515","Year: 1930<br />Population: 122.80<br />Population - Error: 118.4037276<br />Population + Error: 127.196272","Year: 1940<br />Population: 131.70<br />Population - Error: 128.2919094<br />Population + Error: 135.108091","Year: 1950<br />Population: 151.30<br />Population - Error: 146.1628104<br />Population + Error: 156.437190","Year: 1960<br />Population: 179.30<br />Population - Error: 173.4983040<br />Population + Error: 185.101696","Year: 1970<br />Population: 203.20<br />Population - Error: 197.6313895<br />Population + Error: 208.768610"],"type":"scatter","mode":"lines+markers","line":{"width":1.88976377952756,"color":"transparent","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":5.66929133858268,"symbol":"triangle-up-open","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"opacity":1,"error_y":{"array":[4.76491994761573,4.20599351716465,4.64909213332387,4.37274833504982,6.39327213481661,6.05881887272403,3.74746128574442,5.37779086286982,4.80292438158067,5.60036691714709,6.62624637658042,4.78431671838054,3.59278543607434,5.46751539216469,4.39627235234737,3.40809057867529,5.13718961318338,5.80169598046044,5.56861049946806],"arrayminus":[4.76491994761573,4.20599351716465,4.64909213332387,4.37274833504982,6.39327213481661,6.05881887272403,3.74746128574442,5.37779086286982,4.80292438158067,5.60036691714709,6.62624637658042,4.78431671838054,3.59278543607434,5.46751539216469,4.39627235234737,3.40809057867529,5.13718961318338,5.80169598046044,5.56861049946806],"type":"data","width":1.01311623699693,"symmetric":false,"color":"rgba(0,0,0,1)"},"frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":43.1050228310502},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[1780.505,1979.495],"tickmode":"array","ticktext":["1800","1850","1900","1950"],"tickvals":[1800,1850,1900,1950],"categoryorder":"array","categoryarray":["1800","1850","1900","1950"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"Year","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-11.3150964699699,219.248787021822],"tickmode":"array","ticktext":["0","50","100","150","200"],"tickvals":[0,50,100,150,200],"categoryorder":"array","categoryarray":["0","50","100","150","200"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"Population","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"3ae9874378b":{"x":{},"y":{},"ymin":{},"ymax":{},"type":"scatter"},"3ae974d3ff82":{"x":{},"y":{},"ymin":{},"ymax":{}},"3ae913678e4":{"x":{},"y":{},"ymin":{},"ymax":{}}},"cur_data":"3ae9874378b","visdat":{"3ae9874378b":["function (y) ","x"],"3ae974d3ff82":["function (y) ","x"],"3ae913678e4":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

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

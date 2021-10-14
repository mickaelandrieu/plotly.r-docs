---
description: How to make network graphs in R with Plotly.
display_as: scientific
language: r
layout: base
name: Network Graph
order: 4
output:
  html_document:
    keep_md: true
page_type: example_index
permalink: r/network-graphs/
thumbnail: thumbnail/net.jpg
---


### Read Graph File
We are using the well-known social network of `Zachary's karate club`. GML format file can be collected from [here](https://gist.github.com/pravj/9168fe52823c1702a07b).


```r
library(plotly)
library(igraph)
library(igraphdata)

data(karate, package="igraphdata")
G <- upgrade_graph(karate)
L <- layout.circle(G)
```

### Create Vertices and Edges

```r
vs <- V(G)
es <- as.data.frame(get.edgelist(G))

Nv <- length(vs)
Ne <- length(es[1]$V1)
```

### Create Nodes

```r
library(plotly)

Xn <- L[,1]
Yn <- L[,2]

network <- plot_ly(x = ~Xn, y = ~Yn, mode = "markers", text = vs$label, hoverinfo = "text")
```

### Creates Edges

```r
edge_shapes <- list()
for(i in 1:Ne) {
  v0 <- es[i,]$V1
  v1 <- es[i,]$V2

  edge_shape = list(
    type = "line",
    line = list(color = "#030303", width = 0.3),
    x0 = Xn[v0],
    y0 = Yn[v0],
    x1 = Xn[v1],
    y1 = Yn[v1]
  )

  edge_shapes[[i]] <- edge_shape
}
```

### Create Network

```r
axis <- list(title = "", showgrid = FALSE, showticklabels = FALSE, zeroline = FALSE)

fig <- layout(
  network,
  title = 'Karate Network',
  shapes = edge_shapes,
  xaxis = axis,
  yaxis = axis
)

fig
```

<div id="htmlwidget-3943bc3d243a8b6acf33" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-3943bc3d243a8b6acf33">{"x":{"visdat":{"1c183e8d55f":["function () ","plotlyVisDat"]},"cur_data":"1c183e8d55f","attrs":{"1c183e8d55f":{"x":{},"y":{},"mode":"markers","text":["H","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","A"],"hoverinfo":"text","alpha_stroke":1,"sizes":[10,100],"spans":[1,20]}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Karate Network","shapes":[{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null},{"type":"line","line":{"color":"#030303","width":0.3},"x0":null,"y0":null,"x1":null,"y1":null}],"xaxis":{"domain":[0,1],"automargin":true,"title":"","showgrid":false,"showticklabels":false,"zeroline":false},"yaxis":{"domain":[0,1],"automargin":true,"title":"","showgrid":false,"showticklabels":false,"zeroline":false},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[1,0.982973099683902,0.932472229404356,0.850217135729614,0.739008917220659,0.602634636379256,0.445738355776538,0.273662990072083,0.092268359463302,-0.0922683594633019,-0.273662990072083,-0.445738355776538,-0.602634636379256,-0.739008917220659,-0.850217135729614,-0.932472229404356,-0.982973099683902,-1,-0.982973099683902,-0.932472229404356,-0.850217135729614,-0.739008917220659,-0.602634636379257,-0.445738355776538,-0.273662990072083,-0.0922683594633019,0.0922683594633015,0.273662990072083,0.445738355776539,0.602634636379256,0.739008917220659,0.850217135729614,0.932472229404356,0.982973099683902],"y":[0,0.18374951781657,0.361241666187153,0.526432162877356,0.673695643646557,0.798017227280239,0.895163291355062,0.961825643172819,0.995734176295034,0.995734176295035,0.961825643172819,0.895163291355062,0.79801722728024,0.673695643646557,0.526432162877356,0.361241666187153,0.18374951781657,1.22464679914735e-16,-0.18374951781657,-0.361241666187153,-0.526432162877356,-0.673695643646557,-0.798017227280239,-0.895163291355062,-0.961825643172819,-0.995734176295035,-0.995734176295035,-0.961825643172819,-0.895163291355062,-0.79801722728024,-0.673695643646557,-0.526432162877356,-0.361241666187153,-0.18374951781657],"mode":"markers","text":["H","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22","23","24","25","26","27","28","29","30","31","32","33","A"],"hoverinfo":["text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text","text"],"type":"scatter","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Reference
See [https://plotly.com/python/reference/#scatter](https://plotly.com/python/reference/#scatter) for more information and chart attribute options!
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

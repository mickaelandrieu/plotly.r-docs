---
description: How to make interactive 3D mesh plots in R.
display_as: 3d_charts
language: r
layout: base
name: 3D Mesh Plots
order: 4
output:
  html_document:
    keep_md: true
page_type: example_index
permalink: r/3d-mesh/
redirect_from: r/3d-mesh-plots/
thumbnail: thumbnail/3d-mesh.jpg
---


### Basic 3D Mesh Plot


```r
library(plotly)

x <- runif(50, 0, 1)
y <- runif(50, 0, 1)
z <- runif(50, 0, 1)

fig <- plot_ly(x = ~x, y = ~y, z = ~z, type = 'mesh3d')

fig
```

<div id="htmlwidget-e9d16c9e32a2a8f025fb" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e9d16c9e32a2a8f025fb">{"x":{"visdat":{"1de41f127995":["function () ","plotlyVisDat"]},"cur_data":"1de41f127995","attrs":{"1de41f127995":{"x":{},"y":{},"z":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"mesh3d"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"xaxis":{"title":"x"},"yaxis":{"title":"y"},"zaxis":{"title":"z"}},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5}},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"colorbar":{"title":"z","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":[["0","rgba(68,1,84,1)"],["0.0416666666666667","rgba(70,19,97,1)"],["0.0833333333333333","rgba(72,32,111,1)"],["0.125","rgba(71,45,122,1)"],["0.166666666666667","rgba(68,58,128,1)"],["0.208333333333333","rgba(64,70,135,1)"],["0.25","rgba(60,82,138,1)"],["0.291666666666667","rgba(56,93,140,1)"],["0.333333333333333","rgba(49,104,142,1)"],["0.375","rgba(46,114,142,1)"],["0.416666666666667","rgba(42,123,142,1)"],["0.458333333333333","rgba(38,133,141,1)"],["0.5","rgba(37,144,140,1)"],["0.541666666666667","rgba(33,154,138,1)"],["0.583333333333333","rgba(39,164,133,1)"],["0.625","rgba(47,174,127,1)"],["0.666666666666667","rgba(53,183,121,1)"],["0.708333333333333","rgba(79,191,110,1)"],["0.75","rgba(98,199,98,1)"],["0.791666666666667","rgba(119,207,85,1)"],["0.833333333333333","rgba(147,214,70,1)"],["0.875","rgba(172,220,52,1)"],["0.916666666666667","rgba(199,225,42,1)"],["0.958333333333333","rgba(226,228,40,1)"],["1","rgba(253,231,37,1)"]],"showscale":true,"x":[0.393977283500135,0.569465592736378,0.696712989360094,0.11639717570506,0.599265713943169,0.556169468443841,0.0672445471864194,0.823641273425892,0.0486498451791704,0.320321494946256,0.722376664634794,0.36421636887826,0.0406957229133695,0.750861193286255,0.813785756472498,0.253401907393709,0.0189470427576452,0.492905491031706,0.977301317965612,0.441626857500523,0.89129601418972,0.736490371637046,0.508732882328331,0.619401704519987,0.869442819617689,0.805693222675472,0.815233314409852,0.488676292356104,0.750846832990646,0.713311774423346,0.537201171042398,0.852098882896826,0.0293477182276547,0.629896336235106,0.111332623520866,0.0151265871245414,0.274184312671423,0.332491929410025,0.69486878439784,0.639164302730933,0.00234969472512603,0.268417839659378,0.298424325184897,0.117354818386957,0.504481693729758,0.1174809304066,0.239435685565695,0.483303190674633,0.292706351727247,0.901579637080431],"y":[0.768869092687964,0.308255913900211,0.0951168816536665,0.628655178938061,0.332995436387137,0.855716347461566,0.681387185119092,0.70700269495137,0.914926173398271,0.463376010302454,0.2055554240942,0.0190569388214499,0.142958770738915,0.144904497312382,0.035452940966934,0.853051461279392,0.45158973056823,0.064985686680302,0.267383293947205,0.181238021701574,0.81135526439175,0.60241093323566,0.0156625863164663,0.690908091841266,0.428943345788866,0.676832494325936,0.546186051797122,0.51825692714192,0.573355334810913,0.0193235208280385,0.81754698837176,0.0834879139438272,0.603278333088383,0.223891504108906,0.904467294923961,0.0114795882254839,0.498244823422283,0.246202822774649,0.922001539729536,0.538010026095435,0.334189113928005,0.685017708223313,0.23299756529741,0.30594892706722,0.337100949138403,0.527378082508221,0.84099282650277,0.99334223032929,0.728901195572689,0.543229636037722],"z":[0.505359531845897,0.84963526413776,0.387047342723235,0.180302835768089,0.0962684620171785,0.0108176267240196,0.931665484793484,0.2740383814089,0.690764707280323,0.249994597164914,0.53636492183432,0.786781510571018,0.206995399901643,0.604069959139451,0.776300061726943,0.77674898901023,0.139256455469877,0.371011250652373,0.829648243263364,0.160098587861285,0.286154120694846,0.831020419020206,0.968583014095202,0.336698359809816,0.726089117350057,0.775529052596539,0.973519546445459,0.969317742157727,0.566667765844613,0.66809004242532,0.911566506139934,0.539039205992594,0.241144786821678,0.249567468650639,0.379054016899318,0.653103904798627,0.892992260400206,0.529288953868672,0.528844421962276,0.777912096353248,0.24463226320222,0.870836368994787,0.164692816324532,0.0185603264253587,0.574336793273687,0.558323509758338,0.370860120281577,0.1781205823645,0.226731901522726,0.346868295688182],"type":"mesh3d","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Tetrahedron Mesh Plot


```r
library(plotly)

fig <- plot_ly(type = 'mesh3d',
  x = c(0, 1, 2, 0),
  y = c(0, 0, 1, 2),
  z = c(0, 2, 0, 1),
  i = c(0, 0, 0, 1),
  j = c(1, 2, 3, 2),
  k = c(2, 3, 1, 3),
  intensity = c(0, 0.33, 0.66, 1),
  color = c(0, 0.33, 0.66, 1),
  colors = colorRamp(c("red", "green", "blue"))
)

fig
```

<div id="htmlwidget-040a9d05c3728a09e012" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-040a9d05c3728a09e012">{"x":{"visdat":{"1de415f0463e":["function () ","plotlyVisDat"]},"cur_data":"1de415f0463e","attrs":{"1de415f0463e":{"x":[0,1,2,0],"y":[0,0,1,2],"z":[0,2,0,1],"i":[0,0,0,1],"j":[1,2,3,2],"k":[2,3,1,3],"intensity":[0,0.33,0.66,1],"color":[0,0.33,0.66,1],"colors":["function (x) ","roundcolor(cbind(palette[[1L]](x), palette[[2L]](x), palette[[3L]](x), ","    if (alpha) palette[[4L]](x))) * 255"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"mesh3d"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"xaxis":{"title":[]},"yaxis":{"title":[]},"zaxis":{"title":[]}},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5}},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"colorbar":{"title":"","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(234,21,0,1)"],["0.0833333333333333","rgba(212,42,0,1)"],["0.125","rgba(191,64,0,1)"],["0.166666666666667","rgba(170,85,0,1)"],["0.208333333333333","rgba(149,106,0,1)"],["0.25","rgba(128,128,0,1)"],["0.291666666666667","rgba(106,149,0,1)"],["0.333333333333333","rgba(85,170,0,1)"],["0.375","rgba(64,191,0,1)"],["0.416666666666667","rgba(43,212,0,1)"],["0.458333333333333","rgba(21,234,0,1)"],["0.5","rgba(0,255,0,1)"],["0.541666666666667","rgba(0,234,21,1)"],["0.583333333333333","rgba(0,213,42,1)"],["0.625","rgba(0,191,64,1)"],["0.666666666666667","rgba(0,170,85,1)"],["0.708333333333333","rgba(0,149,106,1)"],["0.75","rgba(0,128,128,1)"],["0.791666666666667","rgba(0,106,149,1)"],["0.833333333333333","rgba(0,85,170,1)"],["0.875","rgba(0,64,191,1)"],["0.916666666666667","rgba(0,43,212,1)"],["0.958333333333333","rgba(0,21,234,1)"],["1","rgba(0,0,255,1)"]],"showscale":true,"x":[0,1,2,0],"y":[0,0,1,2],"z":[0,2,0,1],"i":[0,0,0,1],"j":[1,2,3,2],"k":[2,3,1,3],"intensity":[0,0.33,0.66,1],"type":"mesh3d","marker":{"line":{"colorbar":{"title":"","ticklen":2},"cmin":0,"cmax":1,"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(234,21,0,1)"],["0.0833333333333333","rgba(212,42,0,1)"],["0.125","rgba(191,64,0,1)"],["0.166666666666667","rgba(170,85,0,1)"],["0.208333333333333","rgba(149,106,0,1)"],["0.25","rgba(128,128,0,1)"],["0.291666666666667","rgba(106,149,0,1)"],["0.333333333333333","rgba(85,170,0,1)"],["0.375","rgba(64,191,0,1)"],["0.416666666666667","rgba(43,212,0,1)"],["0.458333333333333","rgba(21,234,0,1)"],["0.5","rgba(0,255,0,1)"],["0.541666666666667","rgba(0,234,21,1)"],["0.583333333333333","rgba(0,213,42,1)"],["0.625","rgba(0,191,64,1)"],["0.666666666666667","rgba(0,170,85,1)"],["0.708333333333333","rgba(0,149,106,1)"],["0.75","rgba(0,128,128,1)"],["0.791666666666667","rgba(0,106,149,1)"],["0.833333333333333","rgba(0,85,170,1)"],["0.875","rgba(0,64,191,1)"],["0.916666666666667","rgba(0,43,212,1)"],["0.958333333333333","rgba(0,21,234,1)"],["1","rgba(0,0,255,1)"]],"showscale":false,"color":[0,0.33,0.66,1]}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Cube Mesh Plot


```r
library(plotly)

fig <- plot_ly(type = 'mesh3d',
  x = c(0, 0, 1, 1, 0, 0, 1, 1),
  y = c(0, 1, 1, 0, 0, 1, 1, 0),
  z = c(0, 0, 0, 0, 1, 1, 1, 1),
  i = c(7, 0, 0, 0, 4, 4, 6, 6, 4, 0, 3, 2),
  j = c(3, 4, 1, 2, 5, 6, 5, 2, 0, 1, 6, 3),
  k = c(0, 7, 2, 3, 6, 7, 1, 1, 5, 5, 7, 6),
  intensity = seq(0, 1, length = 8),
  color = seq(0, 1, length = 8),
  colors = colorRamp(rainbow(8))
)

fig
```

<div id="htmlwidget-d36ac8017de72126d45e" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-d36ac8017de72126d45e">{"x":{"visdat":{"1de4bdcec56":["function () ","plotlyVisDat"]},"cur_data":"1de4bdcec56","attrs":{"1de4bdcec56":{"x":[0,0,1,1,0,0,1,1],"y":[0,1,1,0,0,1,1,0],"z":[0,0,0,0,1,1,1,1],"i":[7,0,0,0,4,4,6,6,4,0,3,2],"j":[3,4,1,2,5,6,5,2,0,1,6,3],"k":[0,7,2,3,6,7,1,1,5,5,7,6],"intensity":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1],"color":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1],"colors":["function (x) ","roundcolor(cbind(palette[[1L]](x), palette[[2L]](x), palette[[3L]](x), ","    if (alpha) palette[[4L]](x))) * 255"],"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"mesh3d"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"scene":{"xaxis":{"title":[]},"yaxis":{"title":[]},"zaxis":{"title":[]}},"hovermode":"closest","showlegend":false,"legend":{"yanchor":"top","y":0.5}},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"colorbar":{"title":"","ticklen":2,"len":0.5,"lenmode":"fraction","y":1,"yanchor":"top"},"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(255,56,0,1)"],["0.0833333333333333","rgba(255,111,0,1)"],["0.125","rgba(255,167,0,1)"],["0.166666666666667","rgba(234,202,0,1)"],["0.208333333333333","rgba(197,220,0,1)"],["0.25","rgba(160,239,0,1)"],["0.291666666666667","rgba(123,255,3,1)"],["0.333333333333333","rgba(85,255,21,1)"],["0.375","rgba(48,255,40,1)"],["0.416666666666667","rgba(11,255,59,1)"],["0.458333333333333","rgba(0,255,104,1)"],["0.5","rgba(0,255,160,1)"],["0.541666666666667","rgba(0,255,215,1)"],["0.583333333333333","rgba(0,239,255,1)"],["0.625","rgba(0,183,255,1)"],["0.666666666666667","rgba(0,128,255,1)"],["0.708333333333333","rgba(0,72,255,1)"],["0.75","rgba(32,48,255,1)"],["0.791666666666667","rgba(69,29,255,1)"],["0.833333333333333","rgba(107,11,255,1)"],["0.875","rgba(144,0,247,1)"],["0.916666666666667","rgba(181,0,228,1)"],["0.958333333333333","rgba(218,0,210,1)"],["1","rgba(255,0,191,1)"]],"showscale":true,"x":[0,0,1,1,0,0,1,1],"y":[0,1,1,0,0,1,1,0],"z":[0,0,0,0,1,1,1,1],"i":[7,0,0,0,4,4,6,6,4,0,3,2],"j":[3,4,1,2,5,6,5,2,0,1,6,3],"k":[0,7,2,3,6,7,1,1,5,5,7,6],"intensity":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1],"type":"mesh3d","marker":{"line":{"colorbar":{"title":"","ticklen":2},"cmin":0,"cmax":1,"colorscale":[["0","rgba(255,0,0,1)"],["0.0416666666666667","rgba(255,56,0,1)"],["0.0833333333333333","rgba(255,111,0,1)"],["0.125","rgba(255,167,0,1)"],["0.166666666666667","rgba(234,202,0,1)"],["0.208333333333333","rgba(197,220,0,1)"],["0.25","rgba(160,239,0,1)"],["0.291666666666667","rgba(123,255,3,1)"],["0.333333333333333","rgba(85,255,21,1)"],["0.375","rgba(48,255,40,1)"],["0.416666666666667","rgba(11,255,59,1)"],["0.458333333333333","rgba(0,255,104,1)"],["0.5","rgba(0,255,160,1)"],["0.541666666666667","rgba(0,255,215,1)"],["0.583333333333333","rgba(0,239,255,1)"],["0.625","rgba(0,183,255,1)"],["0.666666666666667","rgba(0,128,255,1)"],["0.708333333333333","rgba(0,72,255,1)"],["0.75","rgba(32,48,255,1)"],["0.791666666666667","rgba(69,29,255,1)"],["0.833333333333333","rgba(107,11,255,1)"],["0.875","rgba(144,0,247,1)"],["0.916666666666667","rgba(181,0,228,1)"],["0.958333333333333","rgba(218,0,210,1)"],["1","rgba(255,0,191,1)"]],"showscale":false,"color":[0,0.142857142857143,0.285714285714286,0.428571428571429,0.571428571428571,0.714285714285714,0.857142857142857,1]}},"frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

#Reference

See [https://plotly.com/r/reference/#mesh3d](https://plotly.com/r/reference/#mesh3d) for more information and chart attribute options!
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

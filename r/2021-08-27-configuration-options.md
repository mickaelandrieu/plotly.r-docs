---
description: How to set the configuration options of figures using the Plotly R graphing
  library.
display_as: file_settings
language: r
layout: base
name: Configuration
order: 5
output:
  html_document:
    keep_md: true
page_type: u-guide
permalink: r/configuration-options/
thumbnail: thumbnail/modebar-icons.png
---

## Configuration Options

The `config()` method sets the configuration options for your figure.

You can set the configuration options for your figure by passing a list to this parameter which contains the options you want to set.

If you don't set an option's value, it will automatically be set to the default value for that option.

For the complete list of configuration options and their defaults see: https://github.com/plotly/plotly.js/blob/master/src/plot_api/plot_config.js

### Enabling Scroll Zoom

This option allows users to zoom in and out of figures using the scroll wheel on their mouse and/or a two-finger scroll.


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 1), type = 'scatter', mode = 'lines+markers')
config(fig, scrollZoom = TRUE)%>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
```

<div id="htmlwidget-f04d3faa73edbf13f0c7" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-f04d3faa73edbf13f0c7">{"x":{"visdat":{"336843447704":["function () ","plotlyVisDat"]},"cur_data":"336843447704","attrs":{"336843447704":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false,"scrollZoom":true},"data":[{"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Turning Off Responsiveness

By default, figures you create with the `plotly` package are [responsive](https://en.wikipedia.org/wiki/Responsive_web_design). Responsive figures automatically change their height and width when the size of the window they are displayed in changes. This is true for figures which are displayed in web browsers on desktops and mobile, Jupyter Notebooks, and other rendering environments.

Try resizing your browser window to see this behavior in effect on this page.

If you would like to disable this default behavior and force your figures to always have the same height and width regardless of the window size, set the value of the `responsive` key to `FALSE` in your figure's configuration dictionary.


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 1), type = 'scatter', mode = 'lines+markers')
config(fig, responsive = FALSE)%>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
```

<div id="htmlwidget-a2b229f98e57650786a2" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-a2b229f98e57650786a2">{"x":{"visdat":{"336850af40eb":["function () ","plotlyVisDat"]},"cur_data":"336850af40eb","attrs":{"336850af40eb":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false,"responsive":false},"data":[{"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Making A Static Chart


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 1), type = 'scatter', mode = 'lines+markers')
config(fig, staticPlot = TRUE)%>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
```

<div id="htmlwidget-41f0a510281779398b33" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-41f0a510281779398b33">{"x":{"visdat":{"336874a47570":["function () ","plotlyVisDat"]},"cur_data":"336874a47570","attrs":{"336874a47570":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false,"staticPlot":true},"data":[{"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Forcing The Modebar to Always Be Visible

When users hover over a figure generated with `plotly`, a **modebar** appears in the top-right of the figure. This presents users with several options for interacting with the figure.

By default, the modebar is only visible while the user is hovering over the chart. If you would like the modebar to always be visible regardless of whether or not the user is currently hovering over the figure, set the displayModeBar attribute in the configuration of your figure to true.


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 1), type = 'scatter', mode = 'lines+markers')
config(fig, displayModeBar = TRUE)%>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
```

<div id="htmlwidget-10b40af32e3d0451eb67" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-10b40af32e3d0451eb67">{"x":{"visdat":{"336826313cf1":["function () ","plotlyVisDat"]},"cur_data":"336826313cf1","attrs":{"336826313cf1":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false,"displayModeBar":true},"data":[{"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Preventing the Modebar from Appearing

When users hover over a figure generated with `plotly`, a modebar appears in the top-right of the figure. This presents users with several options for interacting with the figure.

By default, the modebar is only visible while the user is hovering over the chart. If you would like the modebar to never be visible, then set the `displayModeBar` attribute in the config of your figure to FALSE.


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 1), type = 'scatter', mode = 'lines+markers')
config(fig, displayModeBar = FALSE)%>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
```

<div id="htmlwidget-8736f79002802026a4dc" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-8736f79002802026a4dc">{"x":{"visdat":{"33681339320f":["function () ","plotlyVisDat"]},"cur_data":"33681339320f","attrs":{"33681339320f":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false,"displayModeBar":false},"data":[{"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>


### Hiding the Plotly Logo on the Modebar


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 1), type = 'scatter', mode = 'lines+markers')
config(fig, displaylogo = FALSE)%>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
```

<div id="htmlwidget-619c66309f0e222667f4" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-619c66309f0e222667f4">{"x":{"visdat":{"33686fb0d549":["function () ","plotlyVisDat"]},"cur_data":"33686fb0d549","attrs":{"33686fb0d549":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false,"displaylogo":false},"data":[{"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Customizing Modebar "Download Plot" Button

The camera icon on the modebar causes a static version of the figure to be downloaded via the user's browser. The default behaviour is to download a PNG of size 700 by 450 pixels.

This behavior can be controlled via the `toImageButtonOptions` configuration key.


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 1), type = 'bar')
config(fig, toImageButtonOptions = list(format= 'svg', # one of png, svg, jpeg, webp
                                        filename= 'custom_image',
                                        height= 500,
                                        width= 700,
                                        scale= 1 ))%>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
```

<div id="htmlwidget-e7b44dc4d5030b773078" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-e7b44dc4d5030b773078">{"x":{"visdat":{"33684c0e8844":["function () ","plotlyVisDat"]},"cur_data":"33684c0e8844","attrs":{"33684c0e8844":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,1],"type":"bar","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false,"toImageButtonOptions":{"format":"svg","filename":"custom_image","height":500,"width":700,"scale":1}},"data":[{"x":[1,2,3],"y":[1,3,1],"type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

Figures can be set to download at the currently-rendered size by setting `height` and `width` to `NULL`:



```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 1), type = 'bar')
config(fig, toImageButtonOptions = list(height= NULL,
                                        width= NULL))%>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
```

<div id="htmlwidget-15e73987835adc50783a" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-15e73987835adc50783a">{"x":{"visdat":{"3368301a710a":["function () ","plotlyVisDat"]},"cur_data":"3368301a710a","attrs":{"3368301a710a":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,1],"type":"bar","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false,"toImageButtonOptions":{"height":null,"width":null}},"data":[{"x":[1,2,3],"y":[1,3,1],"type":"bar","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Removing Modebar Buttons

To delete buttons from the modebar, pass an array of strings containing the names of the buttons you want to remove to the `modeBarButtonsToRemove` attribute in the figure's configuration dictionary. Note that different chart types have different default modebars. The following is a list of all the modebar buttons and the chart types they are associated with:

  - **High-level**: `zoom`, `pan`, `select`, `zoomIn`, `zoomOut`, `autoScale`, `resetScale`
  - **2D**: `zoom2d`, `pan2d`, `select2d`, `lasso2d`, `zoomIn2d`, `zoomOut2d`, `autoScale2d`, `resetScale2d`
  - **2D Shape Drawing**: `drawline`, `drawopenpath`, `drawclosedpath`, `drawcircle`, `drawrect`, `eraseshape`
  - **3D**: `zoom3d`, `pan3d`, `orbitRotation`, `tableRotation`, `handleDrag3d`, `resetCameraDefault3d`, `resetCameraLastSave3d`, `hoverClosest3d`
  - **Cartesian**: `hoverClosestCartesian`, `hoverCompareCartesian`
  - **Geo**: `zoomInGeo`, `zoomOutGeo`, `resetGeo`, `hoverClosestGeo`
  - **Other**: `hoverClosestGl2d`, `hoverClosestPie`, `toggleHover`, `resetViews`, `toImage`, `sendDataToCloud`, `toggleSpikelines`, `resetViewMapbox`


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 1), type = 'scatter', mode = 'lines+markers')
config(fig, modeBarButtonsToRemove = c('zoom2d','pan2d'))%>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
```

<div id="htmlwidget-4fd130aea0d8a72709c2" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-4fd130aea0d8a72709c2">{"x":{"visdat":{"3368a63d1cf":["function () ","plotlyVisDat"]},"cur_data":"3368a63d1cf","attrs":{"3368a63d1cf":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false,"modeBarButtonsToRemove":["zoom2d","pan2d"]},"data":[{"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

You can also use a pipe instead of the approach used above:


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(x = c(1, 2, 3), y = c(1, 3, 1), type = 'scatter', mode = 'lines+markers')%>%
  config(modeBarButtonsToRemove = c('zoom2d','pan2d'))%>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
fig
```

<div id="htmlwidget-1ac26a4d1327e24a222a" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-1ac26a4d1327e24a222a">{"x":{"visdat":{"33684e942bbb":["function () ","plotlyVisDat"]},"cur_data":"33684e942bbb","attrs":{"33684e942bbb":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false,"modeBarButtonsToRemove":["zoom2d","pan2d"]},"data":[{"x":[1,2,3],"y":[1,3,1],"type":"scatter","mode":"lines+markers","marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"line":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Add optional shape-drawing buttons to modebar

Some modebar buttons of Cartesian plots are optional and have to be added explicitly, using the `modeBarButtonsToAdd` config attribute. These buttons are used for drawing or erasing shapes. See [the tutorial on shapes and shape drawing](https://plotly.com/r/shapes/#drawing-shapes-on-cartesian-plots) for more details.


```r
library(plotly) 
data(iris) 
 
fig <- plot_ly(data = iris, x = ~Petal.Width, y = ~Sepal.Length, color = ~Species,  
               type = "scatter", mode = "markers")%>% 
  layout(title="A Plotly Figure", legend=list(title=list(text='species'))) 
 
fig <- fig %>% layout(dragmode='drawopenpath', 
                      newshape=list(line = list(color='cyan')), 
                      title = 'Draw a path to separate versicolor and virginica') 
 
#Add modebar buttons 
config(fig,modeBarButtonsToAdd = list('drawline', 
                                 'drawopenpath', 
                                 'drawclosedpath', 
                                 'drawcircle', 
                                 'drawrect', 
                                 'eraseshape')) %>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
```

<div id="htmlwidget-9058ea5f90ac8852a94d" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-9058ea5f90ac8852a94d">{"x":{"visdat":{"33685e579e59":["function () ","plotlyVisDat"]},"cur_data":"33685e579e59","attrs":{"33685e579e59":{"x":{},"y":{},"mode":"markers","color":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Draw a path to separate versicolor and virginica","legend":{"title":{"text":"species"}},"dragmode":"drawopenpath","newshape":{"line":{"color":"cyan"}},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":"Petal.Width"},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":"Sepal.Length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["drawline","drawopenpath","drawclosedpath","drawcircle","drawrect","eraseshape","hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[0.2,0.2,0.2,0.2,0.2,0.4,0.3,0.2,0.2,0.1,0.2,0.2,0.1,0.1,0.2,0.4,0.4,0.3,0.3,0.3,0.2,0.4,0.2,0.5,0.2,0.2,0.4,0.2,0.2,0.2,0.2,0.4,0.1,0.2,0.2,0.2,0.2,0.1,0.2,0.2,0.3,0.3,0.2,0.6,0.4,0.3,0.2,0.2,0.2,0.2],"y":[5.1,4.9,4.7,4.6,5,5.4,4.6,5,4.4,4.9,5.4,4.8,4.8,4.3,5.8,5.7,5.4,5.1,5.7,5.1,5.4,5.1,4.6,5.1,4.8,5,5,5.2,5.2,4.7,4.8,5.4,5.2,5.5,4.9,5,5.5,4.9,4.4,5.1,5,4.5,4.4,5,5.1,4.8,5.1,4.6,5.3,5],"mode":"markers","type":"scatter","name":"setosa","marker":{"color":"rgba(102,194,165,1)","line":{"color":"rgba(102,194,165,1)"}},"textfont":{"color":"rgba(102,194,165,1)"},"error_y":{"color":"rgba(102,194,165,1)"},"error_x":{"color":"rgba(102,194,165,1)"},"line":{"color":"rgba(102,194,165,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[1.4,1.5,1.5,1.3,1.5,1.3,1.6,1,1.3,1.4,1,1.5,1,1.4,1.3,1.4,1.5,1,1.5,1.1,1.8,1.3,1.5,1.2,1.3,1.4,1.4,1.7,1.5,1,1.1,1,1.2,1.6,1.5,1.6,1.5,1.3,1.3,1.3,1.2,1.4,1.2,1,1.3,1.2,1.3,1.3,1.1,1.3],"y":[7,6.4,6.9,5.5,6.5,5.7,6.3,4.9,6.6,5.2,5,5.9,6,6.1,5.6,6.7,5.6,5.8,6.2,5.6,5.9,6.1,6.3,6.1,6.4,6.6,6.8,6.7,6,5.7,5.5,5.5,5.8,6,5.4,6,6.7,6.3,5.6,5.5,5.5,6.1,5.8,5,5.6,5.7,5.7,6.2,5.1,5.7],"mode":"markers","type":"scatter","name":"versicolor","marker":{"color":"rgba(252,141,98,1)","line":{"color":"rgba(252,141,98,1)"}},"textfont":{"color":"rgba(252,141,98,1)"},"error_y":{"color":"rgba(252,141,98,1)"},"error_x":{"color":"rgba(252,141,98,1)"},"line":{"color":"rgba(252,141,98,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[2.5,1.9,2.1,1.8,2.2,2.1,1.7,1.8,1.8,2.5,2,1.9,2.1,2,2.4,2.3,1.8,2.2,2.3,1.5,2.3,2,2,1.8,2.1,1.8,1.8,1.8,2.1,1.6,1.9,2,2.2,1.5,1.4,2.3,2.4,1.8,1.8,2.1,2.4,2.3,1.9,2.3,2.5,2.3,1.9,2,2.3,1.8],"y":[6.3,5.8,7.1,6.3,6.5,7.6,4.9,7.3,6.7,7.2,6.5,6.4,6.8,5.7,5.8,6.4,6.5,7.7,7.7,6,6.9,5.6,7.7,6.3,6.7,7.2,6.2,6.1,6.4,7.2,7.4,7.9,6.4,6.3,6.1,7.7,6.3,6.4,6,6.9,6.7,6.9,5.8,6.8,6.7,6.7,6.3,6.5,6.2,5.9],"mode":"markers","type":"scatter","name":"virginica","marker":{"color":"rgba(141,160,203,1)","line":{"color":"rgba(141,160,203,1)"}},"textfont":{"color":"rgba(141,160,203,1)"},"error_y":{"color":"rgba(141,160,203,1)"},"error_x":{"color":"rgba(141,160,203,1)"},"line":{"color":"rgba(141,160,203,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

You can also use a pipe instead of the approach used above:


```r
library(plotly) 
data(iris) 
 
fig <- plot_ly(data = iris, x = ~Petal.Width, y = ~Sepal.Length, color = ~Species,  
               type = "scatter", mode = "markers")%>% 
  layout(title="A Plotly Figure", legend=list(title=list(text='species'))) 
 
fig <- fig %>% layout(dragmode='drawopenpath', 
                      newshape=list(line = list(color='cyan')), 
                      title = 'Draw a path to separate versicolor and virginica') 
 
#Add modebar buttons 
fig <- fig %>%  
  config(modeBarButtonsToAdd = c('drawline', 
                                 'drawopenpath', 
                                 'drawclosedpath', 
                                 'drawcircle', 
                                 'drawrect', 
                                 'eraseshape')) %>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
 
fig
```

<div id="htmlwidget-f144715edc51900f23f3" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-f144715edc51900f23f3">{"x":{"visdat":{"33687f749dd9":["function () ","plotlyVisDat"]},"cur_data":"33687f749dd9","attrs":{"33687f749dd9":{"x":{},"y":{},"mode":"markers","color":{},"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"type":"scatter"}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"title":"Draw a path to separate versicolor and virginica","legend":{"title":{"text":"species"}},"dragmode":"drawopenpath","newshape":{"line":{"color":"cyan"}},"plot_bgcolor":"#e5ecf6","xaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":"Petal.Width"},"yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":"Sepal.Length"},"hovermode":"closest","showlegend":true},"source":"A","config":{"modeBarButtonsToAdd":["drawline","drawopenpath","drawclosedpath","drawcircle","drawrect","eraseshape","hoverclosest","hovercompare"],"showSendToCloud":false},"data":[{"x":[0.2,0.2,0.2,0.2,0.2,0.4,0.3,0.2,0.2,0.1,0.2,0.2,0.1,0.1,0.2,0.4,0.4,0.3,0.3,0.3,0.2,0.4,0.2,0.5,0.2,0.2,0.4,0.2,0.2,0.2,0.2,0.4,0.1,0.2,0.2,0.2,0.2,0.1,0.2,0.2,0.3,0.3,0.2,0.6,0.4,0.3,0.2,0.2,0.2,0.2],"y":[5.1,4.9,4.7,4.6,5,5.4,4.6,5,4.4,4.9,5.4,4.8,4.8,4.3,5.8,5.7,5.4,5.1,5.7,5.1,5.4,5.1,4.6,5.1,4.8,5,5,5.2,5.2,4.7,4.8,5.4,5.2,5.5,4.9,5,5.5,4.9,4.4,5.1,5,4.5,4.4,5,5.1,4.8,5.1,4.6,5.3,5],"mode":"markers","type":"scatter","name":"setosa","marker":{"color":"rgba(102,194,165,1)","line":{"color":"rgba(102,194,165,1)"}},"textfont":{"color":"rgba(102,194,165,1)"},"error_y":{"color":"rgba(102,194,165,1)"},"error_x":{"color":"rgba(102,194,165,1)"},"line":{"color":"rgba(102,194,165,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[1.4,1.5,1.5,1.3,1.5,1.3,1.6,1,1.3,1.4,1,1.5,1,1.4,1.3,1.4,1.5,1,1.5,1.1,1.8,1.3,1.5,1.2,1.3,1.4,1.4,1.7,1.5,1,1.1,1,1.2,1.6,1.5,1.6,1.5,1.3,1.3,1.3,1.2,1.4,1.2,1,1.3,1.2,1.3,1.3,1.1,1.3],"y":[7,6.4,6.9,5.5,6.5,5.7,6.3,4.9,6.6,5.2,5,5.9,6,6.1,5.6,6.7,5.6,5.8,6.2,5.6,5.9,6.1,6.3,6.1,6.4,6.6,6.8,6.7,6,5.7,5.5,5.5,5.8,6,5.4,6,6.7,6.3,5.6,5.5,5.5,6.1,5.8,5,5.6,5.7,5.7,6.2,5.1,5.7],"mode":"markers","type":"scatter","name":"versicolor","marker":{"color":"rgba(252,141,98,1)","line":{"color":"rgba(252,141,98,1)"}},"textfont":{"color":"rgba(252,141,98,1)"},"error_y":{"color":"rgba(252,141,98,1)"},"error_x":{"color":"rgba(252,141,98,1)"},"line":{"color":"rgba(252,141,98,1)"},"xaxis":"x","yaxis":"y","frame":null},{"x":[2.5,1.9,2.1,1.8,2.2,2.1,1.7,1.8,1.8,2.5,2,1.9,2.1,2,2.4,2.3,1.8,2.2,2.3,1.5,2.3,2,2,1.8,2.1,1.8,1.8,1.8,2.1,1.6,1.9,2,2.2,1.5,1.4,2.3,2.4,1.8,1.8,2.1,2.4,2.3,1.9,2.3,2.5,2.3,1.9,2,2.3,1.8],"y":[6.3,5.8,7.1,6.3,6.5,7.6,4.9,7.3,6.7,7.2,6.5,6.4,6.8,5.7,5.8,6.4,6.5,7.7,7.7,6,6.9,5.6,7.7,6.3,6.7,7.2,6.2,6.1,6.4,7.2,7.4,7.9,6.4,6.3,6.1,7.7,6.3,6.4,6,6.9,6.7,6.9,5.8,6.8,6.7,6.7,6.3,6.5,6.2,5.9],"mode":"markers","type":"scatter","name":"virginica","marker":{"color":"rgba(141,160,203,1)","line":{"color":"rgba(141,160,203,1)"}},"textfont":{"color":"rgba(141,160,203,1)"},"error_y":{"color":"rgba(141,160,203,1)"},"error_x":{"color":"rgba(141,160,203,1)"},"line":{"color":"rgba(141,160,203,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Double-Click Delay
Sets the maximum delay between two consecutive clicks to be interpreted as a double-click in milliseconds. This is the time interval between first mousedown and second mouseup. The default timing is 300 ms (less than half a second).
This setting propagates to all on-subplot double clicks (except for `geo` and `mapbox`).


```r
library(plotly) 

fig <- plot_ly()%>%
  add_trace(y = c(3, 5, 3, 2), x = c("2019-09-02", "2019-10-10", "2019-11-12", "2019-12-22"), 
            type = 'bar',
            texttemplate = "%{label}",
            textposition = "inside")%>%
  layout(xaxis = list(type = 'date'))

config(fig, doubleClickDelay= 1000)%>%layout(plot_bgcolor='#e5ecf6',
          xaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff'),
          yaxis = list(
            zerolinecolor = '#ffff',
            zerolinewidth = 2,
            gridcolor = 'ffff')
          )
```

<div id="htmlwidget-88f4c3c2792b33a13ba8" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-88f4c3c2792b33a13ba8">{"x":{"visdat":{"336846160c8f":["function () ","plotlyVisDat"]},"cur_data":"336846160c8f","attrs":{"336846160c8f":{"alpha_stroke":1,"sizes":[10,100],"spans":[1,20],"y":[3,5,3,2],"x":["2019-09-02","2019-10-10","2019-11-12","2019-12-22"],"type":"bar","texttemplate":"%{label}","textposition":"inside","inherit":true}},"layout":{"margin":{"b":40,"l":60,"t":25,"r":10},"xaxis":{"domain":[0,1],"automargin":true,"type":"date","zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[],"categoryorder":"array","categoryarray":["2019-09-02","2019-10-10","2019-11-12","2019-12-22"]},"plot_bgcolor":"#e5ecf6","yaxis":{"domain":[0,1],"automargin":true,"zerolinecolor":"#ffff","zerolinewidth":2,"gridcolor":"ffff","title":[]},"hovermode":"closest","showlegend":false},"source":"A","config":{"modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false,"doubleClickDelay":1000},"data":[{"y":[3,5,3,2],"x":["2019-09-02","2019-10-10","2019-11-12","2019-12-22"],"type":"bar","texttemplate":["%{label}","%{label}","%{label}","%{label}"],"textposition":["inside","inside","inside","inside"],"marker":{"color":"rgba(31,119,180,1)","line":{"color":"rgba(31,119,180,1)"}},"error_y":{"color":"rgba(31,119,180,1)"},"error_x":{"color":"rgba(31,119,180,1)"},"xaxis":"x","yaxis":"y","frame":null}],"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

### Configuring Figures in Dash Apps

The same configuration dictionary that you pass to the `config` parameter can also be passed to the [config property of a `dcc.Graph` component](https://dashr.plotly.com/dash-core-components/graph).

#### Reference

See config options at https://github.com/plotly/plotly.js/blob/master/src/plot_api/plot_config.js#L6

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
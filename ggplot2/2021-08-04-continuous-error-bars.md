---
description: How to make Continuous Error Bands in ggplot2 with Plotly.
name: Continuous Error Bands
permalink: ggplot2/continuous-error-bars/
thumnail_github: continuous-error-bars.png
layout: base
language: ggplot2
display_as: statistical
page_type: u-guide
order: 15
output:
  html_document:
    keep_md: true
---



## Default error bar plot

To create continuous errorbar plot we need to use `df.summary`.
To add lower and upper error bars, use `ymin = len-sd` and `ymax = len+sd`.


```r
library(plotly)
library(ggplot2)
library(dplyr)

df <- ToothGrowth
df$dose <- as.factor(df$dose)
df.summary <- df %>%
  group_by(dose) %>%
  summarise(
    sd = sd(len, na.rm = TRUE),
    len = mean(len)
  )

p <- ggplot(df.summary, aes(dose, len)) +
      geom_line(aes(group = 1)) +
      geom_errorbar( aes(ymin = len-sd, ymax = len+sd),width = 0.2) +
      geom_point(size = 2)

ggplotly(p)
```

<div id="htmlwidget-c0df5704d7321f2ddc29" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-c0df5704d7321f2ddc29">{"x":{"data":[{"x":[1,2,3],"y":[10.605,19.735,26.1],"text":["dose: 0.5<br />len: 10.605","dose: 1<br />len: 19.735","dose: 2<br />len: 26.100"],"type":"scatter","mode":"lines+markers","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":7.55905511811024,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"frame":null},{"x":[1,2,3],"y":[10.605,19.735,26.1],"text":["dose: 0.5<br />len: 10.605<br />len - sd:  6.105237<br />len + sd: 15.10476","dose: 1<br />len: 19.735<br />len - sd: 15.319564<br />len + sd: 24.15044","dose: 2<br />len: 26.100<br />len - sd: 22.325850<br />len + sd: 29.87415"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_y":{"array":[4.49976315166172,4.41543643905882,3.77415030520988],"arrayminus":[4.49976315166172,4.41543643905882,3.77415030520988],"type":"data","width":14,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":37.2602739726027},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,3.6],"tickmode":"array","ticktext":["0.5","1","2"],"tickvals":[1,2,3],"categoryorder":"array","categoryarray":["0.5","1","2"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"dose","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[4.9167911754947,31.0625959780535],"tickmode":"array","ticktext":["5","10","15","20","25","30"],"tickvals":[5,10,15,20,25,30],"categoryorder":"array","categoryarray":["5","10","15","20","25","30"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"len","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"373933a52abc":{"x":{},"y":{},"type":"scatter"},"3739932c848":{"x":{},"y":{},"ymin":{},"ymax":{}},"373938f17429":{"x":{},"y":{}}},"cur_data":"373933a52abc","visdat":{"373933a52abc":["function (y) ","x"],"3739932c848":["function (y) ","x"],"373938f17429":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>




## Add jitter



```r
library(plotly)
library(ggplot2)
library(dplyr)

df <- ToothGrowth
df$dose <- as.factor(df$dose)
df.summary <- df %>%
  group_by(dose) %>%
  summarise(
    sd = sd(len, na.rm = TRUE),
    len = mean(len)
  )

p <- ggplot(df, aes(dose, len)) +
  geom_jitter( position = position_jitter(0.2), color = "darkgray") + 
  geom_line(aes(group = 1), data = df.summary) +
  geom_errorbar(
    aes(ymin = len-sd, ymax = len+sd),
    data = df.summary, width = 0.2) +
  geom_point(data = df.summary, size = 2)
  
ggplotly(p)
```

<div id="htmlwidget-7169193001acf2c933a4" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-7169193001acf2c933a4">{"x":{"data":[{"x":[0.837151594273746,1.18422574745491,1.13781231464818,0.800074808578938,0.824404335580766,1.06428453465924,1.06157353324816,0.836202560272068,0.955395163130015,1.16744420155883,2.09420819282532,1.84657918689772,1.96684986287728,1.86165172895417,1.95541452616453,1.84279508003965,2.08795955535024,2.15172136733308,1.94251330420375,1.80539479302242,2.81118478095159,2.85047766119242,3.09367640288547,2.81357821859419,3.19783165520057,3.06451820051298,2.8643358306028,2.80828706659377,2.98868750957772,2.93610172495246,1.05161714088172,1.04753475589678,0.932570927031338,1.03809054912999,0.952672719955444,0.85881243608892,1.09282612418756,0.918857812695205,0.803989999555051,1.05220979023725,1.895152148325,2.01551067978144,2.0934194338508,2.16149341305718,2.12747835330665,2.16809436604381,2.00720970248803,2.07013534065336,2.03129385123029,1.90639350907877,3.10789039796218,3.18051245575771,3.10720420815051,2.83780472017825,2.80265250727534,3.0051368358545,2.92567747663707,3.19255411121994,3.08201769320294,2.9188810843043],"y":[4.18915051739663,11.5111103000678,7.32928077913821,5.7820151505433,6.38286603592336,10.0202060624026,11.1842354013212,11.1681514593028,5.18339858215302,6.98247150903568,16.4658898394741,16.5151789656654,15.2167040550895,17.2867645238712,22.5362179341353,17.2992919286899,13.6191736545227,14.535391790159,18.7917196978629,15.5101440825127,23.6018815872632,18.4794709662348,33.871850550808,25.4886226903833,26.3857310447656,32.4906241500191,26.6783966790698,21.5207348767295,23.3226691465452,29.4693057276122,15.1651253933087,21.4875089983456,17.5815039419755,9.69453821081668,14.4815196099691,9.99053852494806,8.16081627869978,9.43915508691222,16.4740819876082,9.66706630302593,19.7034983894601,23.3059040405415,23.5927140730433,26.4135325927846,19.9692023853399,25.1828674992546,25.8251214198023,21.204237185847,14.4772783749364,27.2903114508465,25.5303120565042,26.3673288017698,22.4061170940846,24.5078301219083,24.7753045757487,30.8602773115598,26.4098238175362,27.2944846500643,29.3859045294486,22.9646889878623],"text":["dose: 0.5<br />len:  4.2","dose: 0.5<br />len: 11.5","dose: 0.5<br />len:  7.3","dose: 0.5<br />len:  5.8","dose: 0.5<br />len:  6.4","dose: 0.5<br />len: 10.0","dose: 0.5<br />len: 11.2","dose: 0.5<br />len: 11.2","dose: 0.5<br />len:  5.2","dose: 0.5<br />len:  7.0","dose: 1<br />len: 16.5","dose: 1<br />len: 16.5","dose: 1<br />len: 15.2","dose: 1<br />len: 17.3","dose: 1<br />len: 22.5","dose: 1<br />len: 17.3","dose: 1<br />len: 13.6","dose: 1<br />len: 14.5","dose: 1<br />len: 18.8","dose: 1<br />len: 15.5","dose: 2<br />len: 23.6","dose: 2<br />len: 18.5","dose: 2<br />len: 33.9","dose: 2<br />len: 25.5","dose: 2<br />len: 26.4","dose: 2<br />len: 32.5","dose: 2<br />len: 26.7","dose: 2<br />len: 21.5","dose: 2<br />len: 23.3","dose: 2<br />len: 29.5","dose: 0.5<br />len: 15.2","dose: 0.5<br />len: 21.5","dose: 0.5<br />len: 17.6","dose: 0.5<br />len:  9.7","dose: 0.5<br />len: 14.5","dose: 0.5<br />len: 10.0","dose: 0.5<br />len:  8.2","dose: 0.5<br />len:  9.4","dose: 0.5<br />len: 16.5","dose: 0.5<br />len:  9.7","dose: 1<br />len: 19.7","dose: 1<br />len: 23.3","dose: 1<br />len: 23.6","dose: 1<br />len: 26.4","dose: 1<br />len: 20.0","dose: 1<br />len: 25.2","dose: 1<br />len: 25.8","dose: 1<br />len: 21.2","dose: 1<br />len: 14.5","dose: 1<br />len: 27.3","dose: 2<br />len: 25.5","dose: 2<br />len: 26.4","dose: 2<br />len: 22.4","dose: 2<br />len: 24.5","dose: 2<br />len: 24.8","dose: 2<br />len: 30.9","dose: 2<br />len: 26.4","dose: 2<br />len: 27.3","dose: 2<br />len: 29.4","dose: 2<br />len: 23.0"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(169,169,169,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(169,169,169,1)"}},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1,2,3],"y":[10.605,19.735,26.1],"text":["dose: 0.5<br />len: 10.605","dose: 1<br />len: 19.735","dose: 2<br />len: 26.100"],"type":"scatter","mode":"lines+markers","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)","dash":"solid"},"hoveron":"points","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","marker":{"autocolorscale":false,"color":"rgba(0,0,0,1)","opacity":1,"size":7.55905511811024,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)"}},"frame":null},{"x":[1,2,3],"y":[10.605,19.735,26.1],"text":["dose: 0.5<br />len: 10.605<br />len - sd:  6.105237<br />len + sd: 15.10476","dose: 1<br />len: 19.735<br />len - sd: 15.319564<br />len + sd: 24.15044","dose: 2<br />len: 26.100<br />len - sd: 22.325850<br />len + sd: 29.87415"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_y":{"array":[4.49976315166172,4.41543643905882,3.77415030520988],"arrayminus":[4.49976315166172,4.41543643905882,3.77415030520988],"type":"data","width":14,"symmetric":false,"color":"rgba(0,0,0,1)"},"showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":37.2602739726027},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,3.6],"tickmode":"array","ticktext":["0.5","1","2"],"tickvals":[1,2,3],"categoryorder":"array","categoryarray":["0.5","1","2"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"dose","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[2.70501551572606,35.3559855524786],"tickmode":"array","ticktext":["10","20","30"],"tickvals":[10,20,30],"categoryorder":"array","categoryarray":["10","20","30"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"len","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":false,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"37394d969e5f":{"x":{},"y":{},"type":"scatter"},"373927a5162b":{"x":{},"y":{}},"37397a0036b5":{"x":{},"y":{},"ymin":{},"ymax":{}},"37392921f226":{"x":{},"y":{}}},"cur_data":"37394d969e5f","visdat":{"37394d969e5f":["function (y) ","x"],"373927a5162b":["function (y) ","x"],"37397a0036b5":["function (y) ","x"],"37392921f226":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>



## Create groups

To make sure groups do not overlay, use `position_dodge()`


```r
library(plotly)
library(ggplot2)
library(dplyr)

df <- ToothGrowth
df$dose <- as.factor(df$dose)
df.summary <- df %>%
  group_by(dose, supp) %>%
  summarise(
    sd = sd(len),
    len = mean(len)
  )

p <- ggplot(df.summary, aes(dose, len)) +
        geom_errorbar(
          aes(ymin = len-sd, ymax = len+sd, color = supp),
          position = position_dodge(0.3), width = 0.2
          )+
        geom_point(aes(color = supp), position = position_dodge(0.3)) +
        scale_color_manual(values = c("#00AFBB", "#E7B800")) 

ggplotly(p)
```

<div id="htmlwidget-38a83c5ef3caf2993f91" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-38a83c5ef3caf2993f91">{"x":{"data":[{"x":[0.925,1.925,2.925],"y":[13.23,22.7,26.06],"text":["dose: 0.5<br />len: 13.23<br />len - sd:  8.770291<br />len + sd: 17.68971<br />supp: OJ","dose: 1<br />len: 22.70<br />len - sd: 18.789047<br />len + sd: 26.61095<br />supp: OJ","dose: 2<br />len: 26.06<br />len - sd: 23.404942<br />len + sd: 28.71506<br />supp: OJ"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_y":{"array":[4.45970851065403,3.91095327964367,2.65505806590615],"arrayminus":[4.45970851065403,3.91095327964367,2.65505806590615],"type":"data","width":7.00000000000001,"symmetric":false,"color":"rgba(0,175,187,1)"},"name":"OJ","legendgroup":"OJ","showlegend":true,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1.075,2.075,3.075],"y":[7.98,16.77,26.14],"text":["dose: 0.5<br />len:  7.98<br />len - sd:  5.233366<br />len + sd: 10.72663<br />supp: VC","dose: 1<br />len: 16.77<br />len - sd: 14.254691<br />len + sd: 19.28531<br />supp: VC","dose: 2<br />len: 26.14<br />len - sd: 21.342269<br />len + sd: 30.93773<br />supp: VC"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_y":{"array":[2.74663430401646,2.51530868439199,4.79773094516796],"arrayminus":[2.74663430401646,2.51530868439199,4.79773094516796],"type":"data","width":7.00000000000001,"symmetric":false,"color":"rgba(231,184,0,1)"},"name":"VC","legendgroup":"VC","showlegend":true,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[0.925,1.925,2.925],"y":[13.23,22.7,26.06],"text":["dose: 0.5<br />len: 13.23<br />supp: OJ","dose: 1<br />len: 22.70<br />supp: OJ","dose: 2<br />len: 26.06<br />supp: OJ"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,175,187,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,175,187,1)"}},"hoveron":"points","name":"OJ","legendgroup":"OJ","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1.075,2.075,3.075],"y":[7.98,16.77,26.14],"text":["dose: 0.5<br />len:  7.98<br />supp: VC","dose: 1<br />len: 16.77<br />supp: VC","dose: 2<br />len: 26.14<br />supp: VC"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(231,184,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(231,184,0,1)"}},"hoveron":"points","name":"VC","legendgroup":"VC","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":37.2602739726027},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,3.6],"tickmode":"array","ticktext":["0.5","1","2"],"tickvals":[1,2,3],"categoryorder":"array","categoryarray":["0.5","1","2"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"dose","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[3.94814743352432,32.2229492076272],"tickmode":"array","ticktext":["10","20","30"],"tickvals":[10,20,30],"categoryorder":"array","categoryarray":["10","20","30"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"len","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":true,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895},"title":{"text":"supp","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"37397b512921":{"x":{},"y":{},"ymin":{},"ymax":{},"colour":{},"type":"scatter"},"37394ee67529":{"x":{},"y":{},"colour":{}}},"cur_data":"37397b512921","visdat":{"37397b512921":["function (y) ","x"],"37394ee67529":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>

Add line with `geom_line()`, remember to apply `position_dodge()` to make sure groups do not overlay each other.


```r
library(plotly)
library(ggplot2)
library(dplyr)

df <- ToothGrowth
df$dose <- as.factor(df$dose)
df.summary <- df %>%
  group_by(dose, supp) %>%
  summarise(
    sd = sd(len),
    len = mean(len)
  )

p <- ggplot(df.summary, aes(dose, len)) +
      geom_line(aes(linetype = supp, group = supp), position = position_dodge(0.3))+
      geom_errorbar(
        aes(ymin = len-sd, ymax = len+sd, color = supp),
        position = position_dodge(0.3), width = 0.2
        )+
      geom_point(aes(color = supp), position = position_dodge(0.3)) +
      scale_color_manual(values = c("#00AFBB", "#E7B800")) 


ggplotly(p)
```

<div id="htmlwidget-eabd1b8c768a1df744c7" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-eabd1b8c768a1df744c7">{"x":{"data":[{"x":[0.925,1.925,2.925],"y":[13.23,22.7,26.06],"text":["dose: 0.5<br />len: 13.23<br />supp: OJ<br />supp: OJ","dose: 1<br />len: 22.70<br />supp: OJ<br />supp: OJ","dose: 2<br />len: 26.06<br />supp: OJ<br />supp: OJ"],"type":"scatter","mode":"lines","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)","dash":"solid"},"hoveron":"points","name":"(OJ,1)","legendgroup":"(OJ,1)","showlegend":true,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1.075,2.075,3.075],"y":[7.98,16.77,26.14],"text":["dose: 0.5<br />len:  7.98<br />supp: VC<br />supp: VC","dose: 1<br />len: 16.77<br />supp: VC<br />supp: VC","dose: 2<br />len: 26.14<br />supp: VC<br />supp: VC"],"type":"scatter","mode":"lines","line":{"width":1.88976377952756,"color":"rgba(0,0,0,1)","dash":"dash"},"hoveron":"points","name":"(VC,1)","legendgroup":"(VC,1)","showlegend":true,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[0.925,1.925,2.925],"y":[13.23,22.7,26.06],"text":["dose: 0.5<br />len: 13.23<br />len - sd:  8.770291<br />len + sd: 17.68971<br />supp: OJ","dose: 1<br />len: 22.70<br />len - sd: 18.789047<br />len + sd: 26.61095<br />supp: OJ","dose: 2<br />len: 26.06<br />len - sd: 23.404942<br />len + sd: 28.71506<br />supp: OJ"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_y":{"array":[4.45970851065403,3.91095327964367,2.65505806590615],"arrayminus":[4.45970851065403,3.91095327964367,2.65505806590615],"type":"data","width":7.00000000000001,"symmetric":false,"color":"rgba(0,175,187,1)"},"name":"(OJ,1)","legendgroup":"(OJ,1)","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1.075,2.075,3.075],"y":[7.98,16.77,26.14],"text":["dose: 0.5<br />len:  7.98<br />len - sd:  5.233366<br />len + sd: 10.72663<br />supp: VC","dose: 1<br />len: 16.77<br />len - sd: 14.254691<br />len + sd: 19.28531<br />supp: VC","dose: 2<br />len: 26.14<br />len - sd: 21.342269<br />len + sd: 30.93773<br />supp: VC"],"type":"scatter","mode":"lines","opacity":1,"line":{"color":"transparent"},"error_y":{"array":[2.74663430401646,2.51530868439199,4.79773094516796],"arrayminus":[2.74663430401646,2.51530868439199,4.79773094516796],"type":"data","width":7.00000000000001,"symmetric":false,"color":"rgba(231,184,0,1)"},"name":"(VC,1)","legendgroup":"(VC,1)","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[0.925,1.925,2.925],"y":[13.23,22.7,26.06],"text":["dose: 0.5<br />len: 13.23<br />supp: OJ","dose: 1<br />len: 22.70<br />supp: OJ","dose: 2<br />len: 26.06<br />supp: OJ"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(0,175,187,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(0,175,187,1)"}},"hoveron":"points","name":"(OJ,1)","legendgroup":"(OJ,1)","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"x":[1.075,2.075,3.075],"y":[7.98,16.77,26.14],"text":["dose: 0.5<br />len:  7.98<br />supp: VC","dose: 1<br />len: 16.77<br />supp: VC","dose: 2<br />len: 26.14<br />supp: VC"],"type":"scatter","mode":"markers","marker":{"autocolorscale":false,"color":"rgba(231,184,0,1)","opacity":1,"size":5.66929133858268,"symbol":"circle","line":{"width":1.88976377952756,"color":"rgba(231,184,0,1)"}},"hoveron":"points","name":"(VC,1)","legendgroup":"(VC,1)","showlegend":false,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":26.2283105022831,"r":7.30593607305936,"b":40.1826484018265,"l":37.2602739726027},"plot_bgcolor":"rgba(235,235,235,1)","paper_bgcolor":"rgba(255,255,255,1)","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,3.6],"tickmode":"array","ticktext":["0.5","1","2"],"tickvals":[1,2,3],"categoryorder":"array","categoryarray":["0.5","1","2"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"dose","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[3.94814743352432,32.2229492076272],"tickmode":"array","ticktext":["10","20","30"],"tickvals":[10,20,30],"categoryorder":"array","categoryarray":["10","20","30"],"nticks":null,"ticks":"outside","tickcolor":"rgba(51,51,51,1)","ticklen":3.65296803652968,"tickwidth":0.66417600664176,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(255,255,255,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"len","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":true,"legend":{"bgcolor":"rgba(255,255,255,1)","bordercolor":"transparent","borderwidth":1.88976377952756,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895},"title":{"text":"supp","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"3739408079d3":{"x":{},"y":{},"linetype":{},"type":"scatter"},"373973d6ea6a":{"x":{},"y":{},"ymin":{},"ymax":{},"colour":{}},"37397fe454c2":{"x":{},"y":{},"colour":{}}},"cur_data":"3739408079d3","visdat":{"3739408079d3":["function (y) ","x"],"373973d6ea6a":["function (y) ","x"],"37397fe454c2":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>



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

---
description: How to make Funnel Chart in ggplot2 with Plotly.
name: Funnel Chart
permalink: ggplot2/funnel-charts/
thumnail_github: funnel-charts.png
layout: base
language: ggplot2
display_as: financial
page_type: u-guide
order: 4
output:
  html_document:
    keep_md: true
---



## Funnel plot example



```r
library(plotly)
library(ggplot2)
library(tidyverse)

STAGE <- c('Stage 01: Browsers','Stage 02: Unbounced Users','Stage 03: Email Signups','Stage 04: Email Confirmed','Stage 05: Campaign-Email Opens','Stage 06: Campaign-Email Clickthroughs','Stage 07: Buy Button Page','Stage 08: Buy Button Clickers','Stage 09: Cart Confirmation Page','Stage 10: Address Verification Page','Stage 11: Submit Order Page','Stage 12: Payment','Stage 13: Payment Successful','Stage 14: 1st Successful Purchase','Stage 15: 2nd Purchase','Stage 16: 3rd Purchase','Stage 17: 4th Purchase','Stage 18: 5th Purchase','Stage 01: Browsers','Stage 02: Unbounced Users','Stage 03: Email Signups','Stage 04: Email Confirmed','Stage 05: Campaign-Email Opens','Stage 06: Campaign-Email Clickthroughs','Stage 07: Buy Button Page','Stage 08: Buy Button Clickers','Stage 09: Cart Confirmation Page','Stage 10: Address Verification Page','Stage 11: Submit Order Page','Stage 12: Payment','Stage 13: Payment Successful','Stage 14: 1st Successful Purchase','Stage 15: 2nd Purchase','Stage 16: 3rd Purchase','Stage 17: 4th Purchase','Stage 18: 5th Purchase')

GENDER <- c('Male','Male','Male','Male','Male','Male','Male','Male','Male','Male','Male','Male','Male','Male','Male','Male','Male','Male','Female','Female','Female','Female','Female','Female','Female','Female','Female','Female','Female','Female','Female','Female','Female','Female','Female','Female')

USERS <- c(-14927618.71,-12862663.41,-11361896.41,-9411708.103,-8074316.616,-6958512.218,-6045363.483,-5029954.214,-4008034.113,-3172555.225,-2484808.199,-1903727.481,-1490277.016,-1152003.965,-770748.0581,-434430.0282,-195031.8899,-58570.22156,14226434.29,12276042.59,10850385.59,8999931.897,7732693.384,6666393.782,5743259.517,4723254.786,3680878.887,3002640.775,2467804.801,1977277.519,1593649.984,1229651.035,828496.9419,486621.9718,227106.1101,73466.77844)


df <- data.frame(STAGE, GENDER, USERS)

brks <- c(seq(-15000000, 15000000, by = 5000000))
lbls = c(seq(15, 0, -5), seq(5, 15, 5))

p <- df %>% mutate(USERS = as.numeric(USERS)) %>%
              ggplot(aes(x = reorder(STAGE,abs(USERS)), y = USERS, fill = GENDER)) +
              geom_bar(stat = "identity", width = .6) +
              scale_y_continuous(breaks = brks, labels = lbls) +
              coord_flip() +
              theme_minimal() +
              labs(title="Email Campaign Funnel") +
              theme(plot.title = element_text(hjust = .5),
                                    axis.ticks = element_blank())

ggplotly(p)
```

<div id="htmlwidget-dbb87f4df739d7275b39" style="width:672px;height:480px;" class="plotly html-widget"></div>
<script type="application/json" data-for="htmlwidget-dbb87f4df739d7275b39">{"x":{"data":[{"orientation":"h","width":[0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.6,0.6,0.6,0.6,0.6,0.6,0.6],"base":[0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0],"x":[14226434.29,12276042.59,10850385.59,8999931.897,7732693.384,6666393.782,5743259.517,4723254.786,3680878.887,3002640.775,2467804.801,1977277.519,1593649.984,1229651.035,828496.9419,486621.9718,227106.1101,73466.77844],"y":[18,17,16,15,14,13,12,11,10,9,8,7,6,5,4,3,2,1],"text":["reorder(STAGE, abs(USERS)): Stage 01: Browsers<br />USERS: 14226434.29<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 02: Unbounced Users<br />USERS: 12276042.59<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 03: Email Signups<br />USERS: 10850385.59<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 04: Email Confirmed<br />USERS:  8999931.90<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 05: Campaign-Email Opens<br />USERS:  7732693.38<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 06: Campaign-Email Clickthroughs<br />USERS:  6666393.78<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 07: Buy Button Page<br />USERS:  5743259.52<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 08: Buy Button Clickers<br />USERS:  4723254.79<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 09: Cart Confirmation Page<br />USERS:  3680878.89<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 10: Address Verification Page<br />USERS:  3002640.77<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 11: Submit Order Page<br />USERS:  2467804.80<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 12: Payment<br />USERS:  1977277.52<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 13: Payment Successful<br />USERS:  1593649.98<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 14: 1st Successful Purchase<br />USERS:  1229651.03<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 15: 2nd Purchase<br />USERS:   828496.94<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 16: 3rd Purchase<br />USERS:   486621.97<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 17: 4th Purchase<br />USERS:   227106.11<br />GENDER: Female","reorder(STAGE, abs(USERS)): Stage 18: 5th Purchase<br />USERS:    73466.78<br />GENDER: Female"],"type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(248,118,109,1)","line":{"width":1.88976377952756,"color":"transparent"}},"name":"Female","legendgroup":"Female","showlegend":true,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null},{"orientation":"h","width":[0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.600000000000001,0.6,0.6,0.6,0.6,0.6,0.6,0.6],"base":[-14927618.71,-12862663.41,-11361896.41,-9411708.103,-8074316.616,-6958512.218,-6045363.483,-5029954.214,-4008034.113,-3172555.225,-2484808.199,-1903727.481,-1490277.016,-1152003.965,-770748.0581,-434430.0282,-195031.8899,-58570.22156],"x":[14927618.71,12862663.41,11361896.41,9411708.103,8074316.616,6958512.218,6045363.483,5029954.214,4008034.113,3172555.225,2484808.199,1903727.481,1490277.016,1152003.965,770748.0581,434430.0282,195031.8899,58570.22156],"y":[18,17,16,15,14,13,12,11,10,9,8,7,6,5,4,3,2,1],"text":["reorder(STAGE, abs(USERS)): Stage 01: Browsers<br />USERS: 14927618.71<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 02: Unbounced Users<br />USERS: 12862663.41<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 03: Email Signups<br />USERS: 11361896.41<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 04: Email Confirmed<br />USERS:  9411708.10<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 05: Campaign-Email Opens<br />USERS:  8074316.62<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 06: Campaign-Email Clickthroughs<br />USERS:  6958512.22<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 07: Buy Button Page<br />USERS:  6045363.48<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 08: Buy Button Clickers<br />USERS:  5029954.21<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 09: Cart Confirmation Page<br />USERS:  4008034.11<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 10: Address Verification Page<br />USERS:  3172555.23<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 11: Submit Order Page<br />USERS:  2484808.20<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 12: Payment<br />USERS:  1903727.48<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 13: Payment Successful<br />USERS:  1490277.02<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 14: 1st Successful Purchase<br />USERS:  1152003.97<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 15: 2nd Purchase<br />USERS:   770748.06<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 16: 3rd Purchase<br />USERS:   434430.03<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 17: 4th Purchase<br />USERS:   195031.89<br />GENDER: Male","reorder(STAGE, abs(USERS)): Stage 18: 5th Purchase<br />USERS:    58570.22<br />GENDER: Male"],"type":"bar","textposition":"none","marker":{"autocolorscale":false,"color":"rgba(0,191,196,1)","line":{"width":1.88976377952756,"color":"transparent"}},"name":"Male","legendgroup":"Male","showlegend":true,"xaxis":"x","yaxis":"y","hoverinfo":"text","frame":null}],"layout":{"margin":{"t":43.7625570776256,"r":7.30593607305936,"b":40.1826484018265,"l":247.671232876712},"font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187},"title":{"text":"Email Campaign Funnel","font":{"color":"rgba(0,0,0,1)","family":"","size":17.5342465753425},"x":0.5,"xref":"paper"},"xaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[-16385321.36,15684136.94],"tickmode":"array","ticktext":[15,10,5,0,5,10,15],"tickvals":[-15000000,-10000000,-5000000,1.86264514923096e-09,5000000,10000000,15000000],"categoryorder":"array","categoryarray":[15,10,5,0,5,10,15],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"y","title":{"text":"USERS","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"yaxis":{"domain":[0,1],"automargin":true,"type":"linear","autorange":false,"range":[0.4,18.6],"tickmode":"array","ticktext":["Stage 18: 5th Purchase","Stage 17: 4th Purchase","Stage 16: 3rd Purchase","Stage 15: 2nd Purchase","Stage 14: 1st Successful Purchase","Stage 13: Payment Successful","Stage 12: Payment","Stage 11: Submit Order Page","Stage 10: Address Verification Page","Stage 09: Cart Confirmation Page","Stage 08: Buy Button Clickers","Stage 07: Buy Button Page","Stage 06: Campaign-Email Clickthroughs","Stage 05: Campaign-Email Opens","Stage 04: Email Confirmed","Stage 03: Email Signups","Stage 02: Unbounced Users","Stage 01: Browsers"],"tickvals":[1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18],"categoryorder":"array","categoryarray":["Stage 18: 5th Purchase","Stage 17: 4th Purchase","Stage 16: 3rd Purchase","Stage 15: 2nd Purchase","Stage 14: 1st Successful Purchase","Stage 13: Payment Successful","Stage 12: Payment","Stage 11: Submit Order Page","Stage 10: Address Verification Page","Stage 09: Cart Confirmation Page","Stage 08: Buy Button Clickers","Stage 07: Buy Button Page","Stage 06: Campaign-Email Clickthroughs","Stage 05: Campaign-Email Opens","Stage 04: Email Confirmed","Stage 03: Email Signups","Stage 02: Unbounced Users","Stage 01: Browsers"],"nticks":null,"ticks":"","tickcolor":null,"ticklen":3.65296803652968,"tickwidth":0,"showticklabels":true,"tickfont":{"color":"rgba(77,77,77,1)","family":"","size":11.689497716895},"tickangle":-0,"showline":false,"linecolor":null,"linewidth":0,"showgrid":true,"gridcolor":"rgba(235,235,235,1)","gridwidth":0.66417600664176,"zeroline":false,"anchor":"x","title":{"text":"reorder(STAGE, abs(USERS))","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}},"hoverformat":".2f"},"shapes":[{"type":"rect","fillcolor":null,"line":{"color":null,"width":0,"linetype":[]},"yref":"paper","xref":"paper","x0":0,"x1":1,"y0":0,"y1":1}],"showlegend":true,"legend":{"bgcolor":null,"bordercolor":null,"borderwidth":0,"font":{"color":"rgba(0,0,0,1)","family":"","size":11.689497716895},"title":{"text":"GENDER","font":{"color":"rgba(0,0,0,1)","family":"","size":14.6118721461187}}},"hovermode":"closest","barmode":"relative"},"config":{"doubleClick":"reset","modeBarButtonsToAdd":["hoverclosest","hovercompare"],"showSendToCloud":false},"source":"A","attrs":{"3bed7ccc6f10":{"x":{},"y":{},"fill":{},"type":"bar"}},"cur_data":"3bed7ccc6f10","visdat":{"3bed7ccc6f10":["function (y) ","x"]},"highlight":{"on":"plotly_click","persistent":false,"dynamic":false,"selectize":false,"opacityDim":0.2,"selected":{"opacity":1},"debounce":0},"shinyEvents":["plotly_hover","plotly_click","plotly_selected","plotly_relayout","plotly_brushed","plotly_brushing","plotly_clickannotation","plotly_doubleclick","plotly_deselect","plotly_afterplot","plotly_sunburstclick"],"base_url":"https://plot.ly"},"evals":[],"jsHooks":[]}</script>




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

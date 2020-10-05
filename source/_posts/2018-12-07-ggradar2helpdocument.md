---
title: "ggradar2: Help document "
categories: [Research, Data visualization, R, ggradar2]
tags: [R,ggplot, ggradar2, Data visualization,help document]
---

In this blog, the details of the arguments used in [ggradar2](https://github.com/xl0418/ggradar2) are provided.

<!--more-->

## ggradar2: arguments


**plot.data** :
The input data should be in the data.frame format with columns named. The values in the data are supposed to be numeric. If you want to apply scales like 'high', 'middle', 'low'. Please evaluate them first and put them as `gridline.label` . 

Notice that 'group' column is suggested to included in your data. `ggradar2` now can smartly detect if 'group' is correctly provided. If not, you will be asked if the first column is allowed to defined as the group column. 

```
WARNING: 'group' column is not detected. The first column will be chosen as the group name. Yes/no? (y/n)
```

If you want to plot multiple plots against some subgroups, please specify it in the column `data$facet1`.

**base.size**: The size of radar chart. The default value is 20. 

**webtype**: `"mini"` set a web type with 3 grid lines while `"lux"` set a type with 5 grid lines. Default setting is `"mini"`.

**axis.labels**:  The label of each column in your data is plotted around the radar. 

**axis.label.offset**: The offset of axis labels.

**axis.label.size**: The size of axis labels.

**axis.line.colour**: The color of axis labels.

**grid.min, grid.max**: Rescale your values in this range.

**centre.y**: The radius of inner circle. 

**label.centre.y**: `TRUE` prints the central value. `FALSE` turns it off.

**grid.line.width**: The width of grid lines.

**grid.line.trend**: `"classic"` sets equal width of the grid lines. `"increase"` sets an outward-increasing width of the grid lines. `"decrease"` sets an outward-decreasing width of the grid lines.

**gridline.min.linetype, gridline.mid.linetype, gridline.max.linetype**: Set the grid line type for the inner, middle and outer circles. The default setting is `"longdash"`.

**gridline.min.colour, gridline.mid.colour, gridline.max.colour**: Set the colors for the inner, middle and outer circles. The default settings are `"grey", "#007A87", "grey"`.

**grid.label.size**: Set the size of grid labels.

**gridline.label.offset**: The offset of grid labels.

**gridline.label**: The default setting is the percentage. Replace it with your labels.

**group.line.width**: The width of group lines.
 
**group.point.size**: The size of the point in each axis for group lines.

**group.colours**: Set colors for the group lines.

**polygonfill**: Turn on/off the polygon fill.

**polygonfill.transparency**: The transparency of polygon fills.

**group.fill.colours**: The colors of polygon fills.

**background.circle.colour**: The background color for the radar.

**background.circle.transparency**: The transparency of the background.

**radarshape**: `"round"` gives you a round radar. `"sharp"` gives you a sharp radar.

**multiplots**: Turn on/off multi-plotting function. If on, `data$facet1` column should be included in your data. TRUE/FALSE

**fullscore**: Set full scores to your values. 

**stripbackground**: Turn on/off the background for the panels of multiple plots.

The followings are basic settings.

```R
legend.title="",
plot.legend=TRUE,
plot.title="",
legend.text.size=14,
```
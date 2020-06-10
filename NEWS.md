
<div align="center">

<img src="./man/figures/logo.png" height="250px" />

<!-- badges: start -->
[![CircleCI build status](https://circleci.com/gh/JohnCoene/coronavirus.svg?style=svg)](https://circleci.com/gh/JohnCoene/coronavirus)
[![Travis build status](https://travis-ci.org/JohnCoene/coronavirus.svg?branch=master)](https://travis-ci.org/JohnCoene/coronavirus)
[![AppVeyor build status](https://ci.appveyor.com/api/projects/status/github/JohnCoene/coronavirus?branch=master&svg=true)](https://ci.appveyor.com/project/JohnCoene/coronavirus)
![R-CMD-check](https://github.com/JohnCoene/coronavirus/workflows/R-CMD-check/badge.svg)
[![Lifecycle: stable](https://img.shields.io/badge/lifecycle-stable-brightgreen.svg)](https://www.tidyverse.org/lifecycle/#stable)
![](https://img.shields.io/badge/license-MIT-blue)
<!-- badges: end -->

Dashboard to track the spread of the coronavirus, based on three data sources, built with [shinyMobile](https://rinterface.github.io/shinyMobile/) and [echarts4r](https://echarts4r.john-coene.com/).

[Home](README.md) | [Tracker](https://shiny.john-coene.com/coronavirus) | [Getting Started](GETSTARTED.md) | [Information](INFO.md) | [Changelog](NEWS.md) | [Contribute](CONTRIBUTE.md)

</div>

## Change Log
Below is a complete version history of the **coronavirus** package and the main changes within each version.


### [coronavirus 0.1.4](https://coronavirus.john-coene.com/#/news?id=coronavirus-014)

-   Updated JHU data source, no longer provides recovered data

### [coronavirus 0.1.3](https://coronavirus.john-coene.com/#/news?id=coronavirus-013)

-   Meet new country naming convention of John Hopkins data.
-   Added, in jhu tab, click on country to narrow down trend

### [coronavirus 0.1.2](https://coronavirus.john-coene.com/#/news?id=coronavirus-012)

-   Added news tab
-   Added daily cases to JHU tab
-   Added line graph of cases outside China
-   Added cumulative view on new cases in JHU tab
-   Improve chart transition

### [coronavirus 0.1.1](https://coronavirus.john-coene.com/#/news?id=coronavirus-011)

-   Initialise embeds; ability to embed charts, optionally.
-   Corrected JHU maps.
-   Changed JHU China map to piecewise visual map
-   Changed DXY maps to piecewise

### [coronavirus 0.1.0](https://coronavirus.john-coene.com/#/news?id=coronavirus-010)

-   Initialise API, see `run_api`

### [coronavirus 0.0.6](https://coronavirus.john-coene.com/#/news?id=coronavirus-006)

-   Add total numbers as returned by Weixin; great discrepancy between those and the daily figures.
-   Fixed to meet new John Hopkins data format.
-   PWA works on iPhone

### [coronavirus 0.0.5](https://coronavirus.john-coene.com/#/news?id=coronavirus-005)

-   Add hubei default province in DXY tab.
-   Add shinyscroll to scroll to selected province in DXY tab.
-   Extend toast duration to 5 seconds.
-   Remove coordinates of cities from crawl.
-   Switch to using [Github](https://github.com/CSSEGISandData/2019-nCoV) instead of spreadsheet for JHU data.
-   Add death rate and plot to JHU dashboard
-   Added icons, thanks to Victor Perrier

### [coronavirus 0.0.4](https://coronavirus.john-coene.com/#/news?id=coronavirus-004)

-   Revamped DXY tab, uses counties and provinces instead of geo-located cities.
-   John Hopkins added timeline bar chart.
-   Added `create_script` to easily create cronjob script.
-   Use translation as internal dataset instead of utils data.frame due to encoding issue see [#6](https://github.com/JohnCoene/coronavirus/issues/6).
-   Force Shiny version `1.4.0`, see [#6](https://github.com/JohnCoene/coronavirus/issues/6).
-   Improve loader on DXY city map

### [coronavirus 0.0.3](https://coronavirus.john-coene.com/#/news?id=coronavirus-003)

-   Connect all charts in dxy and weixin tabs
-   Corrected deaths and recovered in DingXiangYuan data, was swapped, see [#2](https://github.com/JohnCoene/coronavirus/issues/2)
-   Number of suspected by city given by DingXiangYuan is wildly inaccurate, has been removed.
-   JHU timeline uses time scale for better, more accurate representation of events.
-   Corrected legend on timeline in JHU tab

### [coronavirus 0.0.2](https://coronavirus.john-coene.com/#/news?id=coronavirus-002)

-   Added DXY data source and corresponding tab
-   Corrected Timeline map dates on JHU map

### [coronavirus 0.0.1](https://coronavirus.john-coene.com/#/news?id=coronavirus-001)

-   Initial version
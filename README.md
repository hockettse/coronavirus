
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

## About

The Coronavirus Tracker tracks data from Johns Hopkins, Weixin (WeChat), and DingXiangYuan (DXY) on the Novel Coronavirus 2019 (COVID-19). The tracker sources a database that is refreshed every hour. The code for the tracker is written in R and optimized for mobile.

The code for the tracker is open source and can be deployed locally. Please see the [instructions](GETSTARTED.md) on how to run the API on your own machine/sever.

Please use the links in the navigation bar immediately above this section for more information on this project, including how to contribute and getting started with your own iteration.
## Features
You can visit the live tracker at [**shiny.john-coene.com/coronavirus**](https://shiny.john-coene.com/coronavirus/). The app is optimized for mobile.
![](https://coronavirus.john-coene.com/_media/banner.png)The app features a wide array of graphs and maps to view and analyze datasets from Johns Hopkins, Weixin, and DXY. It also features a great deal of interactive data visualization:
#### Ex. Timeline of Confirmed Cases by Province in China
![](https://coronavirus.john-coene.com/_media/coronavirus_time1.gif)
#### Ex. Province and City Breakdown
![](https://coronavirus.john-coene.com/_media/coronavirus_time2.gif)
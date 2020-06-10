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

[Home](README.md) | [Tracker](https://shiny.john-coene.com/coronavirus) | [Getting Started](GETSTARTED.md) | [Information](INFORMATION.md) | [Changelog](NEWS.md) | [Contribute](CONTRIBUTE.md)

</div>

## Information

Below is a collection of information on dat and how to embed charts. 

 - If you need guidance on how to get the tracker up and running, please see the [Getting Started](GETSTARTED.md) page.
 - If you need information on the overarching goals of the project, please see the [Home](README.md) page. 
 - If you'd like to know how to contribute to the project, please see the [Contribute](CONTRIBUTE.md) page.

## Embedding Charts
#### Requirements to get started:

 - A Postgres database setup (also needed for API deployment)
 - The config file used to deploy the API locally (please see the [Getting Started](GETSTARTED.md) page for specific instructions)

Embedded charts are hosted in a separate shiny application which can optionally be deployed on your own server too. The `run_app` function takes an `embed_url` argument which defaults to `https://shiny.john-coene/coronavirus-embed`, but can be changed to your own if you choose to deploy the embedded chart API.
#### 1. Copy your config file and create a new directory on your server

    echo "coronavirus::run_embeds()" > app.R 
    
#### 2. Run the app using the new directory URL (see below)

    run_app(embed_url = "http://my-server.com/name-of-directory")

## Data
#### Sources

 - Data from [John Hopkins GIS dashboard](https://github.com/CSSEGISandData/2019-nCoV) accessed via readr (used to be from Google sheet)
 - Data from Weixin using the [nCov2019](https://github.com/GuangchuangYu/nCov2019) package thanks to Guangchuang Yu
 - Data from [DingXiangYuan](https://ncov.dxy.cn/ncovh5/view/pneumonia) scraped using rvest.

### Data Refresh Cron Job Setup
If you wish to automatically refresh the data on your iteration of the API, below are instructions on how to set up a cron job to do this for you.

#### 1. Recreate your config file in your home directory
For guidance on how to set up your config file, please see the [Getting Started](GETSTARTED.md) page.

    cd /home
    mkdir ncov
    R -e "coronavirus::create_config()"
    vi _coronavirus.yml
 
#### 2. Call `create_script()`
The `create_script()` function will edit the config file to make it suitable for crawling fresh data.

    R -e "coronavirus::create_script()"
This will create a file called `script.R` in your current working directory.

#### 3. Test the crawler
Run the newly created script from the terminal to test that it works

    Rscript script.R
#### 4. Create the cron job
Edit your cron jobs by calling `crontab -e` from your terminal. Then, insert your new job. We have the job below set up to run every hour, but you can change this interval to whatever you would like. We recommend [crontab guru](https://crontab.guru/) if you're new at setting up cron jobs.

    0 * * * * cd /home/ncov && Rscript script.R
All set!

Though every version should be backward compatible, it’s a good practice to re-run a crawl after installing a new version of the package.
### Data Corrections
Below is a list of corrected inaccuracies pertaining to the datasets used:

`v0.1.1`

-   There was an issue were the number of cases counted in the John Hopkins map of china and world map was wrongly filtered and gave numbers higher than actually are.

`v0.0.6`

-   Corrected death rate from `deaths/confirmed` to `deaths/(confirmed + recovered)`

`v0.0.3`:

-   Deaths and recovered numbers for DingXiangYuan data was previously [swapped](https://github.com/JohnCoene/coronavirus/issues/2), now fixed.
-   Number of suspected by city given by DingXiangYuan is wildly inaccurate, has been removed.
-   Replaced Map on JHU tab as color scaling was inaccurate due to timeline.
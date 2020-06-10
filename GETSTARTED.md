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

## Getting Started

Below is a step-by-step guide to getting your own iteration of the Coronavirus Tracker project set up on your local machine. 
#### Requirements to get started:

 - Install R (an IDE, such as RStudio, is also highly recommended) 
 - Install the latest version of the `remotes` and `shinyMobile` packages

### 1. Install the "coronavirus" package
The tracker is installed via a package called **coronavirus**. You can download and install the package from github using `remotes`:

    remotes::install_github("JohnCoene/coronavirus")

### 2. Test that the app deploys correctly
Deploying the app is very simple. Simply load the `coronavirus` package and run the `run_app()` command:

    library(coronavirus)
    
    virus <- crawl_coronavirus()
    run_app(virus)
The app should deploy in a new window and display the same as the [web version](https://shiny.john-coene.com/coronavirus).

#
**After step 2, you are able to run your own LOCAL iteration of the tracker. If you wish to deploy your own iteration, please continue through the steps below.**
#

### 3. Create a Postgres Database
In order to deploy your own iteration of the tracker, you will need to create a Postgres database. If you do not have a Postgres account, you can get started with one [here](https://www.postgresql.org/) for free. 

### 4. Get a NewsAPI Token
If you wish to incorporate news article sinto your iteration of the project, you will need a NewsAPI token. You can get one for free [here]([newsapi.org](https://newsapi.org)).

### 5. Create a Crawler Config File
You will need to create a configuration file in order to run the crawler. *This only needs to be done once.* Run the following code to create the file:

    library(coronavirus)
    
    create_config()

### 6. Fill the Config File
Fill in the config file created with the credentials to a Postgres database and the optional [NewsAPI](https://newsapi.org) token. Then, run the crawler. The config file should look like this:

    database:
        name: database-name
        host: 123.123.123.12
        user: me
        password: my-password
    newsapi:
        key: xxXx6X43X12YXx4Xx0XxXx7y # from newsapi.org

Every time you want to update the data, re-run `crawl_coronavirus`; it collects fresh data and overwrites all existing data.

    crawl_coronavirus()
    
 ### 7. Deploy
 
 #### Using Docker (recommended)
 
 ##### 1. Pull the container
 
    docker pull jcoenep/corona
 ##### 2. Copy the config file to the container
 
    docker run -v "$(pwd)"/_coronavirus.yml:/_coronavirus.yml -p 3000:80 jcoenep/corona
    
##### 3. Visit the site locally

    localhost:3000

 #### Using R

##### 1. Deploy on a Shiny community server

    sudo su - -c "R -e \"install.packages('remotes')\""
    sudo su - -c "R -e \"remotes::install_github('JohnCoene/coronavirus')\""

##### 2. Create the config file and store it under a directory called `/srv/shiny-server/`

    cd /srv/shiny-server
    mkdir coronavirus
    cd ./coronavirus
    R -e "coronavirus::create_config()"
    vi _coronavirus.yml

##### 3. Fill in the config file and create the Shiny app

    echo "coronavirus::run_app()" > app.R 
##### 4. Visit the site at ``http://my.server.ip:3838/coronavirus``
Note that you can change the port in the `/etc/shiny-server/shiny-server.conf` file to `80` in order to to have your app hosted at `http://my.server.ip/coronavirus`.
#
Please see the [information](INFO.md) section for instructions on how to refresh data and embed charts.
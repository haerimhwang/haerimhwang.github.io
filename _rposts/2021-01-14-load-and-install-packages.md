---
title: Load and Install Packages 
layout: rpost
rpost-image: "https://haerimhwang.github.io/assets/images/r.png"
description: Codes for Loading Packages and Installing Those Which are not Installed
  
tags:
- R
- Data Science
- Load packages
- Install packages

---

* These codes load packages and install those which are not installed.
<br> 
<br>

* Codes

  - Specify the packages of interest
  
    ```
    packages = c("Rmisc", #for summarizing data
               "dplyr", #for selecting/summarizing data, etc.
               "tidyr", #for tidying messy data
               "reshape", #for reshaping data
               "ggplot2", #for plotting
               "ggrepel") #for labeling data points
    ```
    <br>
    <br>
    
  - Load packages; install them if they are not installed
    ```
    package.check <- lapply(
      packages,
      FUN = function(x) {
        if (!require(x, character.only = TRUE)) {
          install.packages(x, dependencies = TRUE)
          library(x, character.only = TRUE)
        }
      }
    )
    ```

<br>
<br>


---


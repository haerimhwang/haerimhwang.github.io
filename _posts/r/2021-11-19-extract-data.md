---
title: Extract Particular Values from Data
layout: rpost
rpost-image: "https://haerimhwang.github.io/assets/images/r.png"
description: Codes for Extracting Particular Values from Data
tags:
- data extraction
- data science 
- r
---

* These codes extract rows with certain values in data frame.  
<br>

* You can download [the sample dataset](https://haerimhwang.github.io/assets/data/CSV_judgment_data.csv){:target="_blank"} for practice.  
        
* Codes
    
    * Open the sample CSV file you downloaded from the above link
        
          raw_data <- read.csv(file.choose(), header = TRUE, stringsAsFactors = T)
             
        
    * Extract the “critical\_wanna” conditions only
        
          raw_data <- raw_data[which(raw_data$type == "critical_wanna"),]
          raw_data <- droplevels(raw_data) 
            
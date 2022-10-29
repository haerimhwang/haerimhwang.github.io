---
title: Summarize Data
layout: post
categories: r
rpost-image: "https://haerimhwang.github.io/assets/images/r.png"
description: Codes for Summarizing Data
tags:
- summarizing data
- descriptive statistics
- data science 
- r
---

* These codes summarize data by outputting (a) mean, (b) standard deviation, (c) standard error, and (d) confidence interval.  
          
* You can download [the sample dataset](https://haerimhwang.github.io/assets/data/CSV_judgment_data.csv) for practice.  
         
* Codes
    
    * Open the sample CSV file you downloaded from the above link
        
          raw_data <- read.csv(file.choose(), header = TRUE, stringsAsFactors = T)
      
    * Summarize data by condition using the package “dplyr” : Mean, Standard Deviation, Standard Error, Confidence Interval (CI)
        
          data_summary_practice_01 <- raw_data %>%
              group_by(condition) %>%
              summarize(mean_acceptance_rate = mean(judgment, na.rm = TRUE))
      
        
    * Summarize data by condition using the package “Rmisc” : Mean, Standard Deviation, Standard Error, Confidence Interval (CI)
        
          data_summary_practice_02 <- summarySE(raw_data, measurevar="judgment", groupvars="condition") 
            

---
title: Exclude Particular Values from Data
layout: post
categories: r
post-image: "https://haerimhwang.github.io/assets/images/r.png"
description: Codes for Excluding Particular Values from Data
tags:
- data exclusion
- data removal
- data science 
- r
---

* These codes exclude rows with certain values in data frame.  
<br>
<br>

* Codes    
    * Open the sample CSV file you downloaded from the above link
        
          raw_data <- read.csv(file.choose(), header = TRUE, stringsAsFactors = T)         
   
   <br>
    * Exclude the group “Bilingual”; the two lines below do the same thing
        
          raw_data <- subset(raw_data, raw_data$group != "Bilingual")
          raw_data <- raw_data [(!(raw_data$group == "Bilingual")),]           
   
   <br> 
    * Exclude the response “I don’t know,” which is coded as “9”; the two lines below do the same thing
        
          raw_data <- subset(raw_data, raw_data$judgment !="9")
          raw_data <- raw_data [(!(raw_data$judgment == "9")),]          
   
   <br>
    * Remove one participant whose proficiency is N/A
        
          raw_data <- raw_data[!is.na(raw_data$proficiency),]
<br>
<br>
            

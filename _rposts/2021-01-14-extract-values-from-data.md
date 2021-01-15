---
title: Extract Values from Data
layout: rpost
rpost-image: "https://haerimhwang.github.io/assets/images/r.png"
description: Codes for Extracting Values from Data
  
tags:
- R
- Data Science
- Extract Values

---

* These codes extract rows with certain values in data frame.
<br> 
<br>

* You can download [the sample dataset](https://haerimhwang.github.io/assets/data/CSV_judgment_data.csv) for practice.

* Codes

  - Open the file "CSV_judgment_data.csv"
  
    ```
    raw_data <- read.csv(file.choose(), header = TRUE, stringsAsFactors = T)
    ```
    <br>
    <br>
    
  - Extract the "critical_wanna" conditions only
  
    ```
    raw_data <- raw_data[which(raw_data$type == "critical_wanna"),]
    raw_data <- droplevels(raw_data) 
    ```
<br>
<br>

---


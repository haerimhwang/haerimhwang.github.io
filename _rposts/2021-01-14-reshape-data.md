---
title: Reshape Data
layout: rpost
rpost-image: "https://haerimhwang.github.io/assets/images/r.png"
description: Codes for Reshaping Data
  
tags:
- R
- Data Science
- Reshaping Data

---

* These codes reshape data (a) from a long format to a wide format or (b) from a wide format to a long format.
<br> 
<br>

* You can download [the sample dataset](https://haerimhwang.github.io/assets/data/data_summary_L2.csv) for practice.
<br> 
<br>
<br>

* Codes

  - Open the file "data_summary_L2.csv"
  
    ```
    data_summary_L2 <- read.csv(file.choose(), header = TRUE, stringsAsFactors = T)
    ```
    <br>
    <br>
    
  - Reshape data from a long format to a wide format

    ```
    data_summary_L2 <- select(data_summary_L2, participant, proficiency, condition, judgment)
    droplevels(data_summary_L2)
    data_L2_wide = spread(data_summary_L2, key = "condition", value = "judgment")
    ```
    <br>
    <br>
    
  -  Reshape data from a wide format to a long format
    
    ```
    data_L2_long <- gather(data_L2_wide, condition, judgment, If_No_gap:Who_Gap, factor_key = TRUE)
    ```
<br>
<br>

---



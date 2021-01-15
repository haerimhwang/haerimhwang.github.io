---
title: Exclude Values from Data
layout: rpost
rpost-image: "https://haerimhwang.github.io/assets/images/r.png"
description: Codes for Excluding Values from Data
  
tags:
- R
- Data Science
- Exclude Values
- Remove Values

---

* These codes exclude rows with certain values in data frame.
<br> 
<br>

* You can download [the sample dataset](https://haerimhwang.github.io/assets/data/CSV_judgment_data.csv) for practice.
<br> 
<br>
<br>

* Codes

  - Open the file "CSV_judgment_data.csv"
  
    ```
    raw_data <- read.csv(file.choose(), header = TRUE, stringsAsFactors = T)
    ```
    <br>
    <br>
    
  - Exclude the group "Bilingual"; the two lines below do the same thing
  
    ```
    raw_data <- subset(raw_data, raw_data$group != "Bilingual")
    raw_data <- raw_data [(!(raw_data$group == "Bilingual")),] 
    ```
    <br>
    <br>
    
  - Exclude the response "I don't know," which is coded as "9"; the two lines below do the same thing
    
    ```
    raw_data <- subset(raw_data, raw_data$judgment !="9")
    raw_data <- raw_data [(!(raw_data$judgment == "9")),]
    ```
    <br>
    <br>
    
  - Remove one participant whose proficiency is N/A

    ```
    raw_data <- raw_data[!is.na(raw_data$proficiency),]
    ```
<br>
<br>


---


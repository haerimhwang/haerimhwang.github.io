---
title: Word2Vec Model Analysis for Semantic Similarities
layout: pythonpost
pythonpost-image: "https://haerimhwang.github.io/assets/images/python.png"
description: Codes for Analyzing Semantic Similarities via Word2Vec Model
  
tags:
- 
- Word2Vec
- Semantic similarities

---

* This script analyzes semantic similarities between words by constructing a Word2Vec Model.
<br> 
<br>
<br>

* Codes

  - Step 1: Import modules

    ```
    import os
    import csv 
    from itertools import groupby
    ```
<br>
<br>
 
- Step 2: Split a CSV file to text files

  ```
  for key, rows in groupby(csv.reader(open("xxx.csv", encoding="utf-8-sig", errors="ignore")), lambda row: row[0]): # group the data based on the first column 
      with open("%s.txt" % key, "w") as output: # or "with open("data/%s.txt" % key, "w") as output:" if you want to put all text files under the "data" folder
          for row in rows: # iterate through rows            
              output.write("".join(str(row[1])) + "\n") # combine the information in the cells under the second column

  ```

<br>
<br>




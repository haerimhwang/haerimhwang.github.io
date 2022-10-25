---
title: Split CSV to Multiple Text Files
layout: python
post-image: "https://haerimhwang.github.io/assets/images/python.png"
description: Codes for Splitting One CSV File to Multiple Text Files
tags:
- file transformation
- csv to text
- data science
- python
---

* This script splits a large CSV dataset into multiple text files based on the first column. The name of each file comes from the first column and the content of each file will come from all the cells in the second column.  
<br>      

* Codes
    
    * Step 1: Import modules
        
            import os
            import csv 
            from itertools import groupby
      
        
    * Step 2: Split a CSV file to text files
        
            for key, rows in groupby(csv.reader(open("xxx.csv", encoding="utf-8-sig", errors="ignore")), lambda row: row[0]): # group the data based on the first column 
                with open("%s.txt" % key, "w") as output: # or "with open("data/%s.txt" % key, "w") as output:" if you want to put all text files under the "data" folder
                    for row in rows: # iterate through rows            
                        output.write("".join(str(row[1])) + "\n") # combine the information in the cells under the second column
            

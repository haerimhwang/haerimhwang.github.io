---
title: Move Files from One Directory to Another
layout: python
post-image: "https://haerimhwang.github.io/assets/images/python.png"
description: Codes for Moving Files that Match a Certain Criterion from One Directory to Another

tags:
- move files 
- change directories 
- criterion
- data science 
- python
---

* This script moves multiple files that match a certain criterion from one directory to another.  
<br>

* Codes
    
    * Step 1: Import modules
        
            import os
            import shutil
            import glob 
            
 
    * Step 2: Move files that match a certain criterion from one directory to another
        
            source = "source_directory"
            
            filenames = glob.glob("source_directory/*.txt")
            
            for filename in filenames:
                if "Korean.txt" in filename:
                    destination = "source_directory/Korean/"
                    shutil.move(filename, destination + filename) 
            
                elif "English.txt" in filename:
                    destination = "source_directory/English/"
                    shutil.move(filename, destination + filename)
            
                elif "Mandarin.txt" in filename:
                    destination = "source_directory/Mandarin/"
                    shutil.move(filename, destination + filename) 
           

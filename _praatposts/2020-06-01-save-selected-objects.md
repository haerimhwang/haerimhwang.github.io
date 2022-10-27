---
title: Save Selected Objects 
layout: praatpost
post-image: "https://haerimhwang.github.io/assets/images/praat.png"
description: Codes for Saving Selected Objects 
tags:
- saving selected objects
- praat
---

* This script is for saving the objects selected on the Praat window.  

* Codes
    
    * Set your output directory where the selected objects will be saved
        
          dir$ = "/Users/haerimhwang/Desktop/re-recorded/"
        
    * Select the sound objects selected on the Praat window
        
          n = numberOfSelected("Sound")
          for i from 1 to n
          s'i' = selected("Sound",'i')
          s'i'$ = selected$("Sound",'i')
          endfor
            
    * Save the objects as WAV files in the set directory
        
          for i from 1 to n
          n$ = s'i'$
          select s'i'
          Write to WAV file... 'dir$''n$'.wav
          endfor

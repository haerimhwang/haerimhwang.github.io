---
title: Save Selected Objects
layout: praatpost
praatpost-image: "https://haerimhwang.github.io/assets/images/praat.png"
description: Codes for Saving Selected Objects on Praat
  
tags:
- praat
- save objects

---

* This script is for saving the objects selected on the Praat window.
<br>
<br>
<br>

* Codes

  - Set your directories	
		
    ```
    dir$ = "/Users/haerimhwang/Desktop/re-recorded/"
    ```
    <br>
    <br>

	
  - Select the sound objects selected on the Praat window
  
    ```
    n = numberOfSelected("Sound")
    for i from 1 to n
    s'i' = selected("Sound",'i')
    s'i'$ = selected$("Sound",'i')
    endfor
    ```
    <br>
    <br>
    
  - Save the objects as WAV files in the set directory
  
    ```
    for i from 1 to n
    n$ = s'i'$
    select s'i'
    Write to WAV file... 'dir$''n$'.wav
    endfor
    ```
<br>
<br>

---

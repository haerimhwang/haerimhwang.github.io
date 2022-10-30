---
title: Equalize Amplitude
layout: post
categories: praat
post-image: "https://haerimhwang.github.io/assets/images/praat.png"
description: Codes for Tagging English Words for Part-of-Speech
tags:
- amplitude equalization
- sound volume
- praat
---

* This script takes all the files in the specified directory, modify their amplitude (dB), and writes new files to a new folder. It takes three arguments: InputDir is the input folder; positive dB is a dB value to which you want your files to be modified.  
<br>
<br>

* Codes
    
    * Let the script know the input directory and set the wanted amplitude value
        
          form Files
            sentence InputDir  /Users/haerimhwang/Desktop/Done/
            positive dB 65
          endform
          
    <br>
    
    * Create an output folder (named “output”)
        
          createDirectory ("/Users/haerimhwang/Desktop/Done/output/")
          
    <br>
    
    * What Praat does for looping is first to create a string list and counts how many files there are in that list (find n)
    <br>
    <br>
    
    * This allows us to do operation X for n-times
        
          Create Strings as file list... list 'inputDir$'*.wav
          numberOfFiles = Get number of strings
          
    <br>
    
    * “for” is a function for loop.
    <br>
    <br>
    
    * “ifile” means as follows:
    <br>
    <br>
    
    * Start i with 1 and do the operation that follows: change i to 2 and do the operation, change i to 3…., keep until i becomes n
    <br>
    <br>
    
    * Open i-th file in the string list
    <br>
    <br>
    
    * Write the output file (see your script folder)
        
          for ifile to numberOfFiles
            select Strings list
            fileName$ = Get string... ifile
            Read from file... 'inputDir$''fileName$'
            
            Scale intensity... 'dB' # THIS IS WHERE YOU SPECIFY THE OPERATION YOU WANT PRAAT TO DO
            
            Write to WAV file... 'fileName$'
            
            select all # cleaning
            minus Strings list 
            Remove # remove everything from the object window	
            
          endfor
          select all
          Remove
          
<br>
<br>

* Reference:  
  `http://user.keio.ac.jp/~kawahara/scripts/equalize_amp_dB.praat`
  
<br>
<br>


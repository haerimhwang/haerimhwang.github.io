---
title: Measure Duration 
layout: post
categories: praat
post-image: "https://haerimhwang.github.io/assets/images/praat.png"
description: Codes for Measuring Duration of Sound Files
tags:
- duration
- length
- praat
---

* This script is for measuring the duration of individual sound files and saving the ourput in a separate text file. This script is developed based on the two scripts: (1) one by Brynn Hauk from the praat workshop in LING 632 at University of Hawai’i and (2) the other by Paul Boersma and David Weenink.  
<br>
<br>

* Codes
    
    * Set your input directory
        
          form Analyze pitch of sound files 
               comment Directory of sound files
               text sound_directory /Users/haerimhwang/Desktop/Done/
               sentence Sound_file_extension .wav
               comment Full path of the resulting text file:
               text resultfile /Users/haerimhwang/Desktop/results.txt
          endform
          
    <br>
    
    * Check if the result file exists
        
          if fileReadable (resultfile$)
              pause The result file 'resultfile$' already exists! Do you want to overwrite it?
              filedelete "'resultfile$'"
          endif
          
    <br>
    
    * Write a row with column titles to the result file; remember to edit this if you add or change the analyses!
        
          titleline$ = "object_name	duration	'newline$'"
          fileappend "'resultfile$'" 'titleline$'
          
    <br>
        
    * Make a list of all the sound files in the directory you’re using, and put the number of filenames into the variable “number\_files”
        
          Create Strings as file list...  list 'sound_directory$'*.wav
          number_files = Get number of strings
          
    <br>
    
    * Set up a “for” loop that will iterate once for every file in the list
    <br>
    <br>
    
    * Query the file-list to get the first filename from it, then read that file in
    <br>
    <br>
    
    * Make a variable called “object\_name$” that will be equal to the filename minus the “.wav” extension
    <br>
    <br>
    
    * Save result to text file
        
          for j from 1 to number_files
              select Strings list
              file_name$ = Get string... 'j'
              Read from file... 'sound_directory$''file_name$'
        
              object_name$ = selected$ ("Sound")
            
              select Sound 'object_name$'
              startTime = Get start time
              endTime = Get end time
              duration = (endTime - startTime) 
            
              resultline$ = "'object_name$'.wav	'duration'	'newline$'"
            
              fileappend "'resultfile$'" 'resultline$'		
            
          endfor
          
    <br>
    
    * Clean up all files on the list
    <br>
    <br>
    
    * Show if the process is completed
        
          select all
          Remove
          
          print All files have been processed!
          
  <br>
  <br>

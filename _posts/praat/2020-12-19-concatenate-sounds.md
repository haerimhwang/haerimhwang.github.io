---
title: Concatenate Sound Files
layout: post
categories: praat
post-image: "https://haerimhwang.github.io/assets/images/praat.png"
description: Codes for Concatenating Sound Files
tags:
- concatenation
- combining sound files
- praat
---

* This script makes pairs of two sounds using all the sound files in a folder. It does not make a pair of two identical sounds. The ISI duration can be specified in the input menu.       
<br>
<br>

* Useful for 2AFC listening experiments.  
<br>
<br>

* Codes  
    * Open two files in the input directory
    <br>
    
    * Concatenate them

          form Files
            comment Specify the directory
            sentence InputDir ./
            comment Specify the silence duration 
            positive silenceDur 1.00
          endform

          createDirectory ("combined")

          Create Strings as file list... list 'inputDir$'*.wav
          numberOfFiles= Get number of strings

          for i to numberOfFiles


            select Strings list # opens the first file
            fileName1$ = Get string... i
            Read from file... 'inputDir$''fileName1$'
            soundOne$=selected$("Sound")


              silence$ = Create Sound from formula... silence Mono 0 silenceDur 44100  0 # create silence
              silenceSound$=selected$("Sound")


                for k to numberOfFiles # opens the second file	
                select Strings list
                fileName2$ = Get string... k
                  if k <> i
                  Read from file... 'inputDir$''fileName2$'
                  soundTwo$=selected$("Sound")


                    select Sound 'soundOne$' # Now concatenate	
                    plus Sound 'silenceSound$'
                    plus Sound 'soundTwo$'
                    Concatenate

                    name$ = fileName1$ - ".wav"
                    Write to WAV file... ./combined/'name$'_'fileName2$'
                  endif
                endfor
          endfor


          select all
          Remove
          
<br>
<br>

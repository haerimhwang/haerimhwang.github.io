---
title: Duration Measurement 
layout: praatpost
praatpost-image: "https://haerimhwang.github.io/assets/images/praat.png"
description: Experiment MFC Codes for Running a AX Discrimination Listening Experiment
  
tags:
- praat
- duration

---

*This script is based on the two scripts: (1) one by Brynn Hauk from the praat workshop in LING 632 at University of Hawai'i and (2) the other by Paul Boersma and David Weenink. This script is modifed by Bonnie Fox and Haerim Hwang.


## Set your directories:
```
form Analyze pitch of sound files 
  	 comment Directory of sound files
  	 text sound_directory /Users/haerimhwang/Desktop/Done/
  	 sentence Sound_file_extension .wav
 	 comment Full path of the resulting text file:
 	 text resultfile /Users/haerimhwang/Desktop/results.txt
endform
```

##  Check if the result file exists:
```
if fileReadable (resultfile$)
	pause The result file 'resultfile$' already exists! Do you want to overwrite it?
	filedelete "'resultfile$'"
endif
```

##  Write a row with column titles to the result file
##  (Remember to edit this if you add or change the analyses!):
```
titleline$ = "object_name	duration	'newline$'"
fileappend "'resultfile$'" 'titleline$'
```

##  Make a list of all the sound files in the directory we're using, 
##  and put the number of filenames into the variable "number_files":
```
Create Strings as file list...  list 'sound_directory$'*.wav
number_files = Get number of strings
```

##  Set up a "for" loop that will iterate once for every file in the list:
```
for j from 1 to number_files
	##  Query the file-list to get the first filename from it, then read that file in:
	select Strings list
	file_name$ = Get string... 'j'
    Read from file... 'sound_directory$''file_name$'

	## Make a variable called "object_name$" that will be equal to the filename minus the ".wav" extension:
    object_name$ = selected$ ("Sound")

	select Sound 'object_name$'
	startTime = Get start time
	endTime = Get end time
	duration = (endTime - startTime) 

	##  Save result to text file:
	resultline$ = "'object_name$'.wav	'duration'	'newline$'"
	
	fileappend "'resultfile$'" 'resultline$'

		
endfor

##  Clean up all files on the list: 
select all
Remove

print All files have been processed. # show if the process is completed
```

* This script creates an AX discrimination task with the inputted sound files. In the task, a stimulus consists of two sub-stimuli played in sequence, and the participants are asked to judge the similarity/difference between these sub-stimuli.
<br>
<br>

* [Click Here for the Praat Codes](https://haerimhwang.github.io/assets/praatcodes/AX.txt){:target="blankl"}
<br>
<br>

* Reference: <br>
  `https://www.fon.hum.uva.nl/praat/manual/ExperimentMFC_3_1__A_simple_discrimination_experiment.html`


---

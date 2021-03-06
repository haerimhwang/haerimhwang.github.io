
from itertools import groupby # group categories and apply a function to the categories (https://www.kaggle.com/crawford/python-groupby-tutorial)

for key, rows in groupby(csv.reader(open("Kor-teacher_data/FLKC.csv", encoding="utf-8-sig", errors="ignore")), 
                         lambda row: row[0]): # for the csv file; group the data based on the first column (i.e., teacher code)

    with open("Kor-teacher_data/%s.txt" % key, "w") as output: # under the data folder
        for row in rows: # iterate through rows            
            output.write("".join(str(row[1])) + "\n") # combine the info under the second column (i.e., utterances)

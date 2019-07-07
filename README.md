# Grader Rework


### Project Goals
- [x] Preparation 
- [ ] ( In Progress ) Attempt rework
- [ ] Test the rewored grader on at least 2 assignments, as full master_grader has to be written
- [ ] ( Optional ) Set up and test the anti-cheating code

### Preparation
- [x] Get access and obtain sample solutions and students' submissions from COMP204
- [x] Download all the files and set up folder structure
- [x] Research python graders
- [x] Outline current pipeline
- [x] **Design new grading pipeline**
- [x] Configure current grader to its best state
     - [x] Set up raw_student information.csv
     - [x] Set up reviewer_list.csv
     - [x] Set up configuration.json


### Current Pipeline: Folder Structure

COMPXXX/AX contains configuration.json for the specific assignment and the following 5 folders:

* **other data**: Contained the actual .java and .class files that would be run as the master grader, after rework it 
should contain master_grader.py
* **outputs**: Contained a folder called _comments_ which contained all the .txt files to be uploaded to MyCourses with grade,
compilation log/output, test cases, name of the TA who looked at it and so on. This should stay the same, provided that
the output should now be captured from the master_grader.py
It also contains _emails_with_zero_grade.txt_ file with the student emails who failed the compilation. Now we won't do anything.
The folder also contained other files that we don't care about.

* **processed_data**: Had 1 folder for each student with the name being the student's McGill ID. In the folder there were all
the .java files that the student submitted, all the .class files that were generated from the compilation and the 
output .txt file. This should remain unchanged, it should contain the .py files submitted plus the output file.

* **raw_data**: Contained .zip files downloaded straight from MyCourses, remains unchanged.

* **review**: Had 1 folder for each TA grading, which would contain the submissions to be looked at by the TA. Remains unchanged.



### Pipeline Goals / Rough Outline
* **init**: Sets up folder structure, should remain unchanged.
* **compile/grade**: To be merged into 1 action while performing following steps:
     * Unzip the submissions
     * Move them into folders with Student ID
     * Perform filename check
          * ( Optional ) Update emails_with_zero_grade.txt - most like this step will be skipped
     * Run the master_grader.py 
     * Capture the output and create the .txt files
* **distribute/merge**: Should remain unchanged.

### Update after first week:
All the preparation is done, starting to attempt the rework next week.

### Update after 2nd week:
* I realized I needed a python IDE to manage all the files, it is going to be simpler than running everything from the console, so I had to install PyCharm ( Used it before )
* I wrote a grader for COMP204 Assignment 1 
     * This took a long time since 
          * a) I am relearning python pretty much from scratch
          * b) The biggest issue was the same one I was facing with Java when students were asked to use STDIN, since
          COMP204 A1 solely relies on input() method as input instead of writing functions. I googled far and wide to
          figure out how to flush the STDIN with the text I want, but I figured it out
* I started debugging the grader to see what needs to change and where
     
     

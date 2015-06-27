---
layout: post
title: "Cub Scout Database Structure"
category: code
---
One of the major goal I have is to create a system that allows us to track the progress toward each Scout's badges.  One of the major hurdles was data entry for the new requirements.  I discovered how to translate a PDF with the requirements into a spreadsheet.  There are 43 page of spreadsheet that need to be reformatted, but that is much easier than typing every requirement.

It is a new program for the scouts with many more requirements than in the past.  Wolf Cubs (second graders) have seven required activities and one elective.  Each of the required activities have up to eight requirements to complete the activity.  Some of the requirements are to complete two of three listed.

The Wolf badge has 13 electives of which they only have to complete one.  Most of the electives have multiple steps of which the scout has to complete one or two sub items.

There are five badges with this type of structure and one that has a simple set of requirements.  

This is a challenge as to how to structure the tables to minimize the number of separate tables.  I am currently thinking that each badge will have its own table, so there will be six badge tables total.  There will also be two tables to track people, one for the scout and one for the parents or guardians.  

Tracking each scout's progress is straight forward.  It is more challenging to figure out how to track progress without too much repetition or individual coding.  I could write a separate code for every task, but that is very inefficient and hard to maintain.  I want to write a code that will be adaptable to future changes in the program without any (or too much) new code.

Instead, I am going to figure out how to write one code that covers all of the different scenarios, triggered by data stored in the database.  For example, if a certain cell contains a two, then only two of the subset of data need to be completed for a task.  When there are program changes, the database will be updated and include the appropriate trigger for the various requirements.

The program is likely to be updated over time.  The design needs to be easily updated to accommodate future changes.  Right now I am inclined to create a table for each task and link them together for each badge.  The modular approach will ease updating and does not significantly change the complexity of the database.

This is a fun challenge to determine the best database structure for current and future code.
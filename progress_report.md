## 1st Progress Report

1. Read two dataset (`ted_main` and `tran`) and remove NA values.  
2. Sort out the `event` columns - there are different kinds of TED conferences such as main TED conference, TED Global, TEDx, etc. Other kinds of TED conferences except main one mostly target fewer number of audience, therefore they tend to have fewer views and comments. I decided to use the data from TED original since I am planning to use views and comments as the criteria of popularity.   
3. Merge two dataset by `url`, and sort out the columns I need.  
4. Tokenize the transcript and remove puntuations _(in progress)_  
5. Make K-band using `count_1w.txt` file. _(in progress)_  
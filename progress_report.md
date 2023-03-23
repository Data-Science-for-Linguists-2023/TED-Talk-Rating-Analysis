## 1st Progress Report

1. Read two dataset (`ted_main` and `tran`) and remove NA values.  
2. Sort out the `event` columns - there are different kinds of TED conferences such as main TED conference, TED Global, TEDx, etc. Other kinds of TED conferences except main one mostly target fewer number of audience, therefore they tend to have fewer views and comments. I decided to use the data from TED original since I am planning to use views and comments as the criteria of popularity.   
3. Merge two dataset by `url`, and sort out the columns I need.  
4. Tokenize the transcript and remove puntuations _(in progress)_  
5. Make K-band using `count_1w.txt` file. _(in progress)_  

## 2nd Progress Report

1. Data Sharing Plan: I asked for an advice to Dr. Collister because I was not sure about its license. The person who uploaded the dataset on Kaggle specified its license as **CC BY-NC-SA 4.0**, but I was not confident if I can blindly believe this. Below is Dr. Colliester's comment regarding my question:

    Right now TED talks are licensed under a CC-BY-NC-ND license according to their website.

    I might suggest that you do one of these things if you’re very concerned about this: 
    1.	Dive into the Wayback Machine to an archived version of TED.com from 2017 to check what the license on that website says at the time this dataset was collected (or as close as you can get). 
    2.	Contact the author of the dataset to confirm that they have the right permissions to share these data. 

    Because the dataset is licensed under a friendly license right now, you can also make an argument that points back to this website with the original dataset, saying that it’s here and openly licensed, which would redirect any concerns back to the original dataset creator.


So, now I know that their website stipulated that the data set is under a CC-BY-NC-ND license, I guess I can use and share (only a bit of it, of course) the data for my project, EXCEPT the data that I modified.
(Please correct me if I am wrong)

2. Progress

    1. Finish making k-band and calculating sentence length of each transcript
        Also checked the relationship between the number of comments and k-band/sentence length repectively.
    2. Finish refining the 'ratings' column
    3. 
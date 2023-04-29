## 1st Progress Report

1. Read two dataset (`ted_main` and `tran`) and remove NA values.  
2. Sort out the `event` columns - there are different kinds of TED conferences such as main TED conference, TED Global, TEDx, etc. Other kinds of TED conferences except main one mostly target fewer number of audience, therefore they tend to have fewer views and comments. I decided to use the data from TED original since I am planning to use views and comments as the criteria of popularity.   
3. Merge two dataset by `url`, and sort out the columns I need.  
4. Tokenize the transcript and remove puntuations _(in progress)_  
5. Make K-band using `count_1w.txt` file. _(in progress)_  

## 2nd Progress Report

1. Data Sharing Plan: I asked for an advice to Dr. Collister because I was not sure about its license. The person who uploaded the dataset on Kaggle specified its license as **CC BY-NC-SA 4.0**, but I was not confident if I can blindly believe this. Below is Dr. Colliester's comment regarding my question:

    _Right now TED talks are licensed under a **CC-BY-NC-ND** license according to their website._

    _I might suggest that you do one of these things if you’re very concerned about this:_
    _1.	Dive into the Wayback Machine to an archived version of TED.com from 2017 to check what the license on that website says at the time this dataset was collected (or as close as you can get)._
    _2.	Contact the author of the dataset to confirm that they have the right permissions to share these data._

    _Because the dataset is licensed under a friendly license right now, you can also make an argument that points back to this website with the original dataset, saying that it’s here and openly licensed, which would redirect any concerns back to the original dataset creator._


So, now I know that their website stipulated that the data set is under a **CC-BY-NC-ND** license, I guess I can use and share (only a bit of it, of course) the data for my project, EXCEPT the data that I modified.
(Please correct me if I am wrong)

2. Progress

    1. Finish making k-band and calculating sentence length of each transcript
        Also checked the relationship between the number of comments and k-band/sentence length repectively.
    2. Finish refining the 'ratings' column
    3. Find a way to measure the popularity of each talk using rating column _(in progress)_

3. 'Found' portion of the data:

    1. It seems that _the number of comments_ and _average k-band_ has no correlation, unfortunately.
    Should I change my hypothesis? Hmm..
    2. Due to the disparity in the number of words that are considered positive or negative (positive: 10, negative: 4), it seems that it is going to be a little trickier that I expected to use _rating_ column to measure the popularity. I am not sure how I should reflect this difference.

    ## 3rd Progress Report

    1. Progress

        1. Finish polishing the `rating` column

        2. Finish testing my hypothesis (and sub-hypothesis too.)
            * chose multinomial NB model and SVM to use.

        3. Now the data is pretty much ready for the analysis.

    2. Found portion of the data:

        1. I checked the relationship between individual ratings and the related features of the transcript. Unlike what I expected, there was no relationship (or not a strong relationship) between k-band and `obnoxious`, abd between sentence length and `longwinded`.

        2. Regarding my first hypothesis (It is possible to predict whether a talk is popular or not based on its transcript), I concluded that it is not possible to predict the popularity of a talk based on its transcript. I presume that there must be other elements that affect the popularity of the talks, and I believe those elements include nonverbal cues such as the tone, the body language, the facial expression, the delivery of the speaker.

        3. I also contemplated `comments` and `views` as a measure of popularity, instead of ratings. I have checked the correlation between `comments` and tf-idf features, and there was no correlation at all. I am glad I chose `ratings` column as a criteria of popularity.
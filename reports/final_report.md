# Final Report: The application of text classification model to the public talk – TED Talk
Soobin Choi | soc69@pitt.edu | 04/25/2023

### Table of contents
* [Introduction](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/final_report.md#Introduction)
* [Main Hypothesis](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/final_report.md#Main-Hypothesis:-it-is-possible-to-predict-the-popularity-of-a-talk-based-on-its-transcript)
* [Sub-hypothesis 1](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/final_report.md#sub-hypothesis-1-the-correlation-between-the-k-band-and-the-rating-obnoxious)
* [Sun-hypothesis 2](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/final_report.md#sub-hypothesis-2-the-correlatiob-between-the-sentence-length-and-the-rating-longwinded)
* [Conclusion](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/final_report.md#conclusion)
* [General thoughts I had during this project](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/final_report.md#General-thoughts-regarding-the-project)
* [Reference](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/final_report.md#reference)

## Introduction
### Motivation and hypotheses
The motivation for this project is straightforward: since TED talk was one of the main sources I used to learn English, I became curious when I saw a project in Kaggle.com, titled [*What Makes a Popular TED Talk?*](https://www.kaggle.com/code/holfyuen/what-makes-a-popular-ted-talk) I realized that, without solid ground, I assumed that it is the lexical contents that attract people, and that it is the main source which the speech gains popularity from. Therefore, taking this project as an opportunity to check if my hasty assumption is valid, I intend to discover ***whether it is possible to predict a talks popularity solely based on the lexical contents of it***. As the project proceeds, it also seemed interesting to check the correlation between specific ratings and a couple of textual features, hence two sub-hypotheses are added as below:

* There is a positive correlation between the rating `obnoxious` and the mean of [k-band](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/final_report.md#what-is-k-band)

* There is a positive correlation between the rating  `longwinded` and the mean length of sentence in the transcript

#### What is **K-band**?
K-band is one of the ways to measure the vocabulary level of a written language. Since common and everyday words are used more frequently than technical and sophisticated words, it is designed to measure the level of a word by its frequency. The K-band in this project is built on the unigram file (`enable1.txt`) collected by Google, the 1/3 million most frequent words on the platform. The unigram file can be found [on this website](https://norvig.com/ngrams/)


### About data
For this project, I used two datasets from [Kaggle](https://www.kaggle.com/datasets/rounakbanik/ted-talks), which are [`ted_main.csv`](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/data_sample/ted_main_sample.csv), [`transcript.csv`](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/data_sample/transcript_sample.csv). `ted_main.csv` file contains the general information of each talk, such as the title, the number of comments, the ratings they received, the url, etc. `transcript.csv` file contains only two columns, which are the url, and the transcript. For my project, I simply merged two datasets by `url` column, and started the data cleaning process from here. In the merged file,  there are 2544 talks, with 2.3 million tokens in total.

#### License
Both datasets are licensed under a [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International Public License](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/LICENSE.md#creative-commons-attribution-noncommercial-noderivatives-40-international-public-license).


## Main Hypothesis: it is possible to predict the popularity of a talk based on its transcript

There are several columns that can be taken into account when to calculate the popularity of a talk, which are `comment` column, `view` column, and `rating` column. The only column I used for this project was the `rating` column since it provides more information in detail. There are 14 catetories in `ratings`, and nine of them are positive, four of them are negative, and one rating is neutral. Since each values in `rating` column is the total sum of each rating as below, I have calculated the percentage of positive/negative ratings. In the case of one neutral rating, I did not add it up to neither positive nor negative. After calculating the percentages, I found that most of the talks are positively skewed. Therefore, I labelled the talks based on the percentage of negative ratings: if the percentage of negative ratings is higher than the mean of negative ratings percentage (8.12%), I labelled it as negative. Other than that, I labelled it as positive. After finishing labelling, I calculated the base line, and it was 66%.

![ratrings](/images/ratings.png) ![ratings2](/images/ratings3.png)

*examples of ratings column, before cleaning and after cleaning*

In this case, I have tried a Multinomial Naive Bayes model and a Support Vector Machine (SVM), and it was interesting to find that both demonstrate quite different effects.

### Multinomial Naive Bayes
The first machine learning model I tried for classification was Multinomial Naive Bayes. I first set `max feature` number as 1500, then increased to 3000 in the case of unigram feature. The results are below.

<img src="/images/multinomialNB_1gram.png"  width="430" height="360"> <img src="/images/multinomialNB_1gram2.png"  width="430" height="360">

There is almost no difference at all in the case of unigram feature even though the max feature has been adjusted from 1500 to 3000. Both models labelled the majority of the talks as positive, which is not a surprise, considering the fact that the better part of the talks are already highly positively skewed. Since both models predicted that almost all of them are positively-rated talks, their performance does not show a big difference from the base line (69% and 70% respectively). After that, I tried the bigram feature in the hope that by incorporating the bigram feature, it would be possible to enhance its performance.

![MultinomialNB_unigram](/images/multinomialNB_ngram1.png)

After changing the unigram feature to bigram feature, the performance of the model actually deteriorated. The accuracy score decreased to 65%, which is lower than the based line. However, since the model is basically classifying all the talks as positive after adding bigram to the model as well as increasing the maximum number of features to 20000, it is safe to say that this model's performance will come out as same as the base line if I conducted cross validation. 

I am not sure if this result is due to the increase in the maximum feature number or due to the bigram features, but what we can conclude from here is that it is not possible to predict the popularity of a talk based on its transcript in the case where multinomial Naive Bayes model is employed.

### Support Vector Machine

Since both maximum feature numbers and C parameter have a significant impact on the performance of Support Vector Machine models, I have adjusted both when testing the model. However, in this project, the maximum feature number did not affect the performance significantly while the C parameter did. 

<img src="/images/SVM_1gram1.png"  width="430" height="360"> <img src="/images/SVM_1gram3.png"  width="430" height="360">

The interesting point in the figure above is the number of true negatives in each plot. While Naive Bayes model showed poor performance in classifying true negatives, SVM model demonstrates better performance in detecting true negatives. When the margin was harder, the model classified true negatives more successfully than when the margin is softer. However, as a classifier, the model with harder margin is of no use in that its performance is even lower than the base line (63%). In the case of softer margin, the model performed slightly better than the base line (70%), but there is no significant difference in terms of performance between SVM and multinomial Native Bayes model. 

![SVM Ngram](/images/SVM_ngram.png)

For Further research, I replaced unigram features with bigram/trigram features. I also increased the maximum feature number from 1500 to 15000 to make sure that the model uses trigram features, too. Discouragingly, even after changing both maximum feature number and linguistic feature, the performance remained almost the same (69.7%). However, when comparing this model to Naive Bayes model, it still shows better performance in classifying true negatives, from which it can be concluded that SVM is a more sophisticated model than Naive Bayes. 


## Sub-hypotheses 

For both sub-hypothesis, I have calculated the percentage that `obnoxious` and `longwinded` take up in each row in `rating` column. Due to the fact that both dependent and independent variables are continuous, I used a regression model to test the sub-hypotheses.

### 1: The correlation between the k-band and the rating `obnoxious`

![kband-obnoxious](/images/kband_obn.png)

To my disappointment, the correlation between the k-band and the rating `obnoxious` was very low. The coefficient is .11, and the mean absolute error is 1.24, indicating that the model is off by 1.24 on average.

### 2: The correlation between the sentence length and the rating `longwinded`

The second hypothesis is also rejected, unfortunately. The coefficient of the model is .0013, which is even lower, and the mean absolute error is 1.71, indicating that the model is off by 1.71 on average.

![sentlen-longwinded](/images/sent_long.png)

## Conclusion

This project aims to reveal the correlation between a talk's popularity and its lexical content. The main hypothesis tested was that it is possible to predict the popularity solely based on the talk's transcript. After testing two different models which are multinomial Naive Bayes and SVM, it is concluded that it is not possible to predict the talk's popularity purely based off of the lexical contents. Additionally, as a follow-up hypothesis, I explored the correlation between specific ratings (`obnoxious` and `longwinded`) and non-lexical features such as k-band and sentence length. Despite the higher hope in these follow-up hypotheses, the regression model proved them wrong. No correlation was found between certain ratings and non-lexical features. Having tested all the hypotheses, it can be concluded that there are other factors other than lexical contents that draw people's attention and play a role in gaining popularity beyond the lexical content.


## General thoughts regarding the project
I am glad that I was able to learn funtamental python packages such as *pandas*, *numpy*, *matplotlib*. Even though my result is somewhat disappointing, I am still glad that I was able to push through and finish this project. I regret that I did not put more effort into choosing the topic at the beginning of this project, but it is what it is. It was demanding, but it was so much fun. This project was a great opportunity to confirm that I do love this work and would like to pursue a career in this field. I would like to thank Dr. Han for giving me this valuable experience.


## Reference

Dataset collected:  
Rounak, B. (2017) *TED Talks.*  Retrieved from https://www.kaggle.com/datasets/rounakbanik/ted-talks

count1w.txt file  
Thorsten B. & Alex F.  (2008) *Google Web Trillion Word Corpus.* Retrieved from https://norvig.com/ngrams/


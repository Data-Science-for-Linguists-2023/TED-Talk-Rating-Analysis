# Final Report: The application of text classification model to the public talk – TED Talk
Soobin Choi | soc69@pittedu | 04/25/2023

## Introduction
### Motivation and hypotheses
The motivation for this project is straightforward: since TED talk was one of the main sources I used to learn English, I became curious when I saw a project in Kaggle.com, titled [*What Makes a Popular TED Talk?*](https://www.kaggle.com/code/holfyuen/what-makes-a-popular-ted-talk) I realized that I, without solid ground, assumed that it is the content that attracts people, and that it is the main source which the speech gains popularity from. Therefore, utilizing this project as an opportunity to check if my hasty assumption is valid, I intend to discover whether the actual content of talks is the main factor that determines the popularity of talks or not. As the project proceeds, it also seemed interesting to check the correlation between specific ratings and a couple of textual features, hence two sub-hypotheses are added as below:

* There is a positive correlation between the rating `obnoxious` and the mean of [k-band](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/final_report.md#what-is-k-band)

* There is a positive correlation between the rating  `longwinded` and the mean length of sentence in the transcript

#### What is K-band?
K-band is one of the ways to measure the vocabulary level of a written language. Since common and everyday words are used more frequently than technical and sophisticated words, it is designed to measure the level of a word by its frequency. The k-band in this project is built on the unigram file (`enable1.txt`) collected by Google, the 1/3 million most frequent words on the platform. The unigram file can be found in [this website](https://norvig.com/ngrams/)


### About the dataset
For this project, I used two datasets which are: [`ted_main.csv`](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/data_sample/ted_main_sample.csv), [`transcript.csv`](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/data_sample/transcript_sample.csv). `ted_main.csv` file contains the general information of each talk, such as the title, the number of comments, the ratings they recieved, the url, and so on. `transcript.csv` file contains only two columns, which are the url, and the transcript. For my projecct, I simply merged two datasets by `url` column. In the merged dataset, I mainly focused on three columns which are `ratings`, `transcript`


#### License
Both datasets are under a [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International Public License](https://github.com/Data-Science-for-Linguists-2023/TED-Talk-Rating-Analysis/blob/main/LICENSE.md#creative-commons-attribution-noncommercial-noderivatives-40-international-public-license).


## Main Hypothesis: it is possible to predict the popularity of a talk based on its transcript

(350)

## Sub-hypothesis 1: the correlation between the k-band and the rating `obnoxious`
(350)

## Sub-hypothesis 2: the correlatiob between the sentence length and the rating `longwinded`
(350)

## Conclusion
* What I have found
* Future development regarding this data
(200~300)


## Have a paragraph devoted to the overall history and process of your project, warts and all. Document setbacks, false starts, and other difficulties you experienced.


## Reference
google k-band 잊지말기

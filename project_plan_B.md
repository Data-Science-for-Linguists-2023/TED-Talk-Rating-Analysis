# Project Plan B

## A working title.
Music Lyric Analysis - focusing on thier view on women (if possible..)

## A brief summary.
Just like other literature, or more than it does, songs reflect people's desire and how they view the world. Therefore, in this project, I will attempt to create two generative language models based on the lyrics of the songs that are on Billboard Hot 100 in order to find out how people's general perception of women has changed in the United States over the past 60 years. 


## The DATA portion. 

### What will your data look like? 
I am planning to use `billboard_lyrics_1964-2015.csv` by Kaylin Pavlik. This dataset contains the year each song was released, lyrics, and their rank, so it perfectly fits the purpose of my project. I also need the lyrics of the songs released after 2016, so I am considering doing the same process as Kaylin Pavlik did for her article to add more recent songs. For the errors that we found in class, I am considering just ignore them and delete the songs whose lyrics contain any erroneously tokenized word.

### What sorts of data sourcing and cleaning up effort will be involved?
I might need to do a lot of data scraping from _Billboard Year-End Hot 100 Songs_ wikipidia. I learned how to scrap the data from website a little bit, but little I remember at this moment. In addition, I learned the method with R language, so I probably need to learn how to scrap the data from website with Python from the scratch.

For the data that Ms. Pavlik uploaded, I don't think I will spend a lot of time cleaning up the data except deleting the errors since it is already quite well organized. My concern at this moment is that I need to think about the way to incorporate the gender information of the singer. Gender information of the singer will be quite a crucial data to include since we need to know who is _you_ (or which gender is _you_) in the song. I do not have a concrete idea to realize this at this moment. 

I might have to do topic modeling for each songs in order to prove that the song is about a woman and the lyrics are used to describe women.. 

### Do you have an existing data source in mind that you can start with, and if so, what are the URLs or references?

[50 years of Pop Music](https://www.kaylinpavlik.com/50-years-of-pop-music/)


## The ANALYSIS portion. 

The end goal of this project is to make two generative language models created based on the lyrics of the songs that are listed in the Billboard Hot 100 and compare the output of each model. In addition, as a side goal, I am planning to measure the frequency of words and see if there is any specific tendency in each period. I do not own any hypothesis at this moment, but the only point that I can assume for now is that the lyrics of more recent songs will describe women more agentive or active figure whereas that of older songs will depict women as somebody to be conquered by men.

## The PRESENTATION portion. 
I am only considering power point at this moment with many plots such as histogram, barplot.
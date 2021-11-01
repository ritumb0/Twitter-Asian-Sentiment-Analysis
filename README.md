# Analyzing Change in Sentiment Towards Asians Through the COVID-19 Pandemic

## Description

With the rise of social media in the past year, hate speech has become a huge and growing issue. Around the beginning few months of the global pandemic, negative sentiment in the US increased towards Asian Americans and Pacific Islanders. To investigate how that sentiment shifted throughout the pandemic, I took an approach of diagnosing hate speech with regression—0 to 1 going from neutral to negative—where I detect the sentiment towards Asian groups on Twitter using deep learning and linear methods.

## Dataset

I used the Twitter API and the searchtweets library to compile the dataset of Tweets from which I produced my findings. I drew tweets from March 10, 2020 to August 31, 2020 and January 1, 2021 to April 30, 2021 with the purpose of viewing data from beginning-to-middle of the pandemic and later from mid-final of the pandemic. Because I wanted to gauge how sentiment towards Asians transformed on Twitter throughout the pandemic, comparing the early pandemic and the post-vaccine-approval pandemic ensured that the tone of conversation would be shifted. I filtered only tweets that had both “Asian” and “China” in them. This choice was made in an effort to avoid skewing my results by searching specifically for clearly positive or negative hashtags like WuhanVirus or StopAsianHate.

While I was selecting my training data, I was faced with data availability constraints—because there was no available Twitter dataset showing Asian hate in a cultural context, which would have been valuable for my model to soak up themes and clues which would be present in my Tweet corpus, I decided upon using the Toxic Comment Classification Challenge dataset https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge/data to see how a model trained on Wikipedia comments would be able to generalize towards the tweets. The Toxic Comment Classification dataset, ranging from highly negative to minimally positive, consists of 223,549 samples, each labeled with 6 one-hot encoded multiclass labels: toxic, severe_toxic, obscene, insult, threat, and identity_hate. To transfer these six classification scores into one number between 0 and 1, I read some of the comments in the dataset and looked at several features across the board. I combined these insights and trends into my final scoring: score for a comment starts at 0, if a comment is labeled as toxic add 0.2, if it is an insult, add 0.1, if it is an obscene insult, add 0.1, if it is a threat or identity hate, add 0.2, if both, add an additional 0.1, if severe toxic, add 0.5, if score is greater than 1, cap at 1. My score ranges from neutral to negative because given the domain of the solution, whether or not a social media comment is hate speech and the user should be blocked is key, so positivity is irrelevant information.  

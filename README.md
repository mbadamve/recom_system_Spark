# Recommendation System on Spark
In this project, the aim is to build a recommendation system on Spark using Collaborative Filtering and Alternate Least Squares (ALS) algorithm.

By leveraging this data, and appropriate feature engineering it is possible to identify which is the genre, artist and language user mostly interested in and from this data, it is easy to recommend top songs to the user in the app.

# Business Understanding
## Music recommendation algorithm
1. From NetEase Cloud Music's annual report and daily recommendations
    1. The glory days of records and DJs are over (gossip on the Kaggle page)
    2. This era belongs to the music recommendation algorithm
2. What is the problem to be solved by the music recommendation algorithm?
    1. Whether the user will like a song or singer recommended to him
    2. How to know what kind of songs a new user will like
3. There are two main ideas
    1. Content-based
    2. People-oriented
4. Good music recommendation algorithm?
    1. A better user experience
    2. Stronger user stickiness
        1. Music copyright a large number of missing NetEase cloud to retain users can not be separated from the recommendation system
KKBOX
A picture of a client;
A digital music media service provider originating in Taiwan
A paid music service is available
Business needs and objectives
KKBOX currently has a music recommendation system based on matrix decomposition for collaborative filtering

KKBOX wants to see better predictive methods to help them more accurately recommend their favorite songs to users

Objective: Improve the accuracy of predictions

The problem definition
Predict the probability that a user will choose to play a song again some time after he or she first hears it.
Make a judgment based on a user's record of playing a song
Target indicates whether it will be played again in the next month
Data Understanding
An overview of the data
In addition to trains and tests, there are songs, song_extra_info, and three data sheets.

Train and test:KKBOX users listen to the song record
Select only the record information for the first time a user has listened to a song in a certain period of time
The match between the user ID and the song ID
The operating environment in which the song is heard
The target variable target
songs and songs_extra_info
Song ID and song title
Singers, songwriters, songwriters
Music style
The length of the music
Song language
ISRC: International standard recording coding
members: Membership information
User ID
City, gender, age
Sign up for the channel
Registration time and membership expiration time
Go deep into the data
ISRC
International Standard Recording Code
Coding rules: country publisher year
Music style
genre_ids: 124|324|754
Statistical ids number distribution, which explains why only the first three are selected
put the distribution map
Age and gender
There are simply not too many missing values

Operating environment
source system tab
Feature partition (level 1 directory)
people: Large V users
listen with: DJ put what you listen to what
source screen name
Interface (Secondary Directory)
A subpage of discovery
Discover featured: Includes daily recommendations
chart: List
source type
The source of the song
Show what values each property has
Data Preparation
Song-related information
Extract the genre_1st genre_2nd genre_3rd from the genre_ids
The same music has multiple singers, compositions, compositions of the situation, extract the first person
ISRC spin-off (skipped)
Extract the number of songs per year/country/company
Member-related information
The transformation of date format data

Value transformation
Continuous variables
Take a pair to reduce the impact of outliers
Classify variables
LabelEncoder, converted to No
The time series
illustrate

The records in train and test are arranged in an orderly manner
The location of a record throughout the dataset reflects the order in which this playback behavior occurred
Based on this, a series of interesting features can be extracted
features

How long has it been since a member listened to the singer's music
Modeling
Xgboost
decision tree
Integrated learning boosting
The parameter settings
List

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
- A picture of a client;
- A digital music media service provider originating in Taiwan
- A paid music service is available

## Business needs and objectives
KKBOX currently has a music recommendation system based on matrix decomposition for collaborative filtering

KKBOX wants to see better predictive methods to help them more accurately recommend their favorite songs to users

_Objective: Improve the accuracy of predictions_

## The problem definition
1. Predict the probability that a user will choose to play a song again some time after he or she first hears it.
    1. Make a judgment based on a user's record of playing a song
    2. Target indicates whether it will be played again in the next month

## Data Understanding
### An overview of the data

In addition to trains and tests, there are songs, song_extra_info, and three data sheets.

1. Train and test:KKBOX users listen to the song record
    1. Select only the record information for the first time a user has listened to a song in a certain period of time
    2. The match between the user ID and the song ID
    3. The operating environment in which the song is heard
    4. The target variable target
2. songs and songs_extra_info
    1. Song ID and song title
    2. Singers, songwriters, songwriters
    3. Music style
    4. The length of the music
    5. Song language
    6. ISRC: International standard recording coding
3. members: Membership information
    1. User ID
    2. City, gender, age
    3. Sign up for the channel
    4. Registration time and membership expiration time
## Go deep into the data
### ISRC
1. International Standard Recording Code
2. Coding rules: country publisher year
### Music style
1. genre_ids: 124|324|754
2. Statistical ids number distribution, which explains why only the first three are selected
    1. put the distribution map
### Age and gender
There are simply not too many missing values

### Operating environment
1. source system tab
    1. Feature partition (level 1 directory)
    2. people: Large V users
    3. listen with: DJ put what you listen to what
2. source screen name
    1. Interface (Secondary Directory)
    2. A subpage of discovery
        1. Discover featured: Includes daily recommendations
        2. chart: List
3. source type
    1. The source of the song
4. Show what values each property has
## Data Preparation
### Song-related information
1. Extract the genre_1st genre_2nd genre_3rd from the genre_ids
2. The same music has multiple singers, compositions, compositions of the situation, extract the first person
3. ISRC spin-off (skipped)
    1. Extract the number of songs per year/country/company
### Member-related information
The transformation of date format data

### Value transformation
1. Continuous variables
    1. Take a pair to reduce the impact of outliers
2. Classify variables
    1. LabelEncoder, converted to No
### The time series
1. illustrate

    1. The records in train and test are arranged in an orderly manner
    2. The location of a record throughout the dataset reflects the order in which this playback behavior occurred
    3. Based on this, a series of interesting features can be extracted
2. features

    1. How long has it been since a member listened to the singer's music
## Modeling
1. Xgboost
    1. decision tree
    2. Integrated learning boosting
2. The parameter settings
    1. List

# youtube-analytics with sentiment analysis on comments

## Introduction

For this project we’re going to be utilizing **Youtube Data API V3**, which allows us to collect data from youtube. This data will help us get useful insights on the videos, such as sentiment analysis for comments, most liked video, top videos based on views, etc.

## Files
**youtube_analytics.ipynb** This notebook contains all the code.
**vdoLinks.csv** contains youtubeIDs of over 25000 videos. We use these IDs to retrieve data of the corresponding videos.

## Data Collection

For data collection, we are collecting _100 comments, Description of the video, View count, Like count, Dislike count, Comment count,Duration of the video, and Favourite count_ for all the videos.

Now for extracting the above information we need to use google’s API key, which only allows 10000 requests a day. So each of our video requires more than 2 requests, and 5000 videos will easily cross 10000 requests. Per day quota cost based on the request can be calculated from the following link. **https://developers.google.com/youtube/v3/ determine_quota_cost** So to solve this issue, we had to split the video links data into 10 equal parts, and use 10 different API keys to retrieve all the information at once. Then we combined all 10 dataframes into **_youtube_df,_** and then saved it into a CSV file for later use.




## Data Cleansing
During the data collection there was considerable missing data, so we just stored empty strings in the place of missing data. But these **empty strings** are of no use, so we replaced the empty strings with **‘Nan’** values.

<img width="993" alt="Screen Shot 2022-04-15 at 1 22 45 AM" src="https://user-images.githubusercontent.com/50517893/163524637-07986adf-cbee-4d73-8367-6788e89c33fc.png">


From the above figure, we can see that most columns have missing values, except for ids and
index (column: Unnamed: 0). Because we have already placed Nan values, we can safely
ignore them from our analysis.

## Analytics

### Sentiment Analysis of comments

The video with highest negative comments is:
**Diverted (2009) Trailer**
The video with highest positive comments is:
**Dangerous Game Trailer 1993**

<img width="981" alt="Screen Shot 2022-04-15 at 1 21 44 AM" src="https://user-images.githubusercontent.com/50517893/163524540-5413234e-1fdc-4a1c-aa6f-9a57ae84ceb4.png">


### Video with highest duration

Trailer for **“Getting to Know You”**

<img width="1001" alt="Screen Shot 2022-04-15 at 1 18 41 AM" src="https://user-images.githubusercontent.com/50517893/163524215-facb3ca9-8eaa-4838-af56-e8bf6153f20f.png">


### Videos with least and highest likes count

<img width="685" alt="Screen Shot 2022-04-15 at 1 18 06 AM" src="https://user-images.githubusercontent.com/50517893/163524162-a26e1403-cbaf-4d46-bc63-40998cbe9326.png">


### Top 10 videos based on views count

Video with the highest views :
**John Legend - All of Me (Official Video)**
Video with the least views :
**Babylon 5: In the Beginning (1998)**

<img width="987" alt="Screen Shot 2022-04-15 at 1 17 19 AM" src="https://user-images.githubusercontent.com/50517893/163524096-8c46696e-53c0-4974-b32c-836d03cf4e8d.png">


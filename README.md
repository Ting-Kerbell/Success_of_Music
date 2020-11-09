# Can We Predict a Song's Commercial Success?

ORIE 4741 Final Project
by Darren Ting (dmt228), Joshua Kwasi Agyei-Gyamfi (jka45), and Mario Medina (mcm382)

## What's this about?
Often times, when musicians begin the songwriting process, it would be common for them to wonder how well this new song could potentially do. Will it be played on the radio? Will the kids these days enjoy it? Is it a "bop"? Being able to predict the success of a song can potentially estimate its ability to bring revenue for the artist/group as well as go mainstream to make an influence in today’s society, or at least a night in a sweaty college town basement.  It can show the trends of current musical interests in mainstream culture which can allow musicians to tailor their music accordingly. For this project, we explore this further by asking, “Can you predict a song’s commercial success based on characteristics of the song?”.

To answer this question, we use supervised machine learning. we build a predictive model using classification of whether or not the song will be successful or not. We will use audio features of songs requested from Spotify’s API as our input variables. This data will be used in conjunction with Billboard Hot 100 data that has been shared on Kaggle which will be used as a benchmark for mainstream musical success. This data set will serve as the response variables for our model. We believe that these datasets will allow us to successfully answer our question and give us more insight on what attributes make a song popular.

## What's our data?
The [Spotify](https://www.kaggle.com/yamaerenay/spotify-dataset-19212020-160k-tracks) and [Billboard](https://www.kaggle.com/danield2255/data-on-songs-from-billboard-19992019) datasets, which we used, were obtained from Kaggle resources and created by Daniel DeFoe and Yamac Eren Ay respectively. The music data we used ranged from 1999 to 2019. A Python script was used to recover the data (2 files) from the data source. After converting all the documents into .csv files, the datasets for 1999 to 2019 were combined into one cleaned master .csv file. Some issues were encountered in which the columns were not consistent with the columns from other files. These were handled by manipulating the data in a plethora of ways (on a case by case basis addressed later) to ensure that the final dataset is uniform. The final dataset has 15 columns and 41,900 rows.
The columns being used for the classifier are:
- Numerical
	- acousticness (Ranges from 0 to 1) (The relative metric of the track being acoustic)
	- danceability (Ranges from 0 to 1) (The relative measurement of the track being danceable)
	- energy (Ranges from 0 to 1) (The energy of the track)
	- duration-ms (Integer typically ranging from 200k to 300k) (The length of the track in milliseconds (ms))
	- instrumentalness (Ranges from 0 to 1) (The relative ratio of the track being instrumental)
	-  valence (Ranges from 0 to 1)  (The positiveness of the track)
	- tempo (Float typically ranging from 50 to 150) (The tempo of the track in Beat Per Minute (BPM))
	- liveness (Ranges from 0 to 1) (The relative duration of the track sounding as a live performance)
	- loudness (Float typically ranging from -60 to 0)
	- speechiness (Ranges from 0 to 1) (The relative length of the track containing any kind of human voice)
	- year (Ranges from 1999 to 2019)

- Boolean
	- mode (0 = Minor, 1 = Major)
	- explicit (0 = No explicit content, 1 = Explicit content) (The binary value whether the track contains explicit content or not)
	-  Is-success (0 = not successful , 1 = is successful)

- Ordinal
	- key (All keys on octave encoded as values ranging from 0 to 11, starting on C as 0, C# as 1 and so on…)  (The primary key of the track encoded as integers in between 0 and 11)

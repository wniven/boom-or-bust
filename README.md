# boom-or-bust
This was a project that I wrote for a systems engineering final project. I created two models different models to predict whether a song would be popular or not based on the song's acoustic or lyrical characteristics.

The first step of the process is seen in the 'spotify_scraper' model. Using the Spotify API and a playlist with 10,000 songs on it, I created a dataframe containing all the data I would need to form the models.

Popularity scores are calculated by Spotify and are not necessarily tied to total listens. Popularity scores are given to both artists and songs. We normalized a song's popularity score by dividing it by the artist's. Then we took the average normalized popularity score for the whole playlist. If a song's normalized popularity score was above this mark, it was labeled as a 'boom', otherwise, it was a 'bust'. We now had a binary classification task for our models.

The first model we looked at was a Convolutional Neural Network that was trained on a spectrogram graphing a snippet of the song. A spectrogram is a visual representation of sound. Were time is on the x-axis, frequency is on the y-axis, and the z-axis (represented as a heatmap) represents decibels. We found this model to be just 2% more accurate (.50 -> .52) than the base accuracy rate. 

The second model we explored was a k-nearest neighbors model whose input vector included a whole host of scalar audio features provided by the Spotify API (e.g. danceability, acousticness, speechiness, tempo, etc). We also used the Genius API to scrape the lyrics for each song and used nltk to find positive/negative/neurtral sentiment intensity scores to add to the input vector. After grid searching for the optimal number of neighbors (59) we were left with a final accuracy only 53%, only slightly better than the CNN.

In conclusion, we were not able to create an effective model to predict a song's popularity. Future attempts should include more data, higher fidelity spectrograms (maybe with a high pass filter), or use a different measure of popularity.

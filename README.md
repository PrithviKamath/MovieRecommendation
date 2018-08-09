# MovieRecommendation

<h4><center>INFO 6101 Data Science Engineering with Python </center></h4>

<h3><center> Team Members : Harshad Pardeshi, Krutika Deshpande, Prithvi Kamath</center></h3>
<h3><center> Under the guidance of </center></h3>
<h3><center> Prof.Konstantopoulos, Dino </center></h3>

<h4> Used MovieLens dataset - a classic dataset for training recommendation models. It can be obtained from the GroupLens website. </h4><h4>Downloaded the data 20 million movie ratings by users (on a 1–5 scale).The users explicitly tell us how they would rate a movie. </h4>
<h4> Following are the steps followed: </h4>
- Importing and extracting the dataset
- Exploratory Data Analysis
- Sampling data for visualization
- Word Cloud of Genres
- Data Visualization in Tableau
- Checking the sparsity of data
- Maximum Likelihood Estimation Implementation
- Representing and extracting data using RDD
- Training, validation and testing data
- Implementing Alternating Least Square Algorithm
- Recommending movies to a new user

## Importing and extracting the dataset
Imported packages like pandas, numpy, scipy, datetime and matplotlib and imported csv files from from the extracted path.

## Exploratory Data Analysis
Created dataframe using the movies.csv file. Dataframe consisted of three columns viz. 'movieid', 'title', 'genres'. 
The 'title' column had the year of the movie embedded into round brackets which was extracted and saved into a seperate column.
The 'genres' column had a combination of the all the genres a movie is about. These genres were extracted from a single column to multiple column with values as 1 and 0 if the particular movie is of that genre.
For example, the movie 'Toy Story' has the genres 'Adventure', 'Animation' , 'Childern' , 'Comedy' and 'Fantasy'. So, for those columns the cell value is set to 1 and rest are 0. The cleaned dataset is then writing into a csv file.

##  Visualization in Tableau
<img src='https://github.com/PrithviKamath/MovieRecommendation/blob/master/Images/User%20with%20mas%20votes.png'></img>
<img src='https://github.com/PrithviKamath/MovieRecommendation/blob/master/Images/Movie%20with%20max%20votes.png'></img>
<img src='https://github.com/PrithviKamath/MovieRecommendation/blob/master/Images/Number%20of%20Movies%20for%20each%20Rating.png'></img>

##  Sampling for Visualization
The movielens dataset contains 20 million ratings for about 27,278 movies by 138,000 users. Since we observed that movies for rating '3' and '4' were exorbitantly high, we sampled the dataset into a smaller dataset with equal number of movies for each rating.
<img src='https://github.com/PrithviKamath/MovieRecommendation/blob/master/Images/Rating%20wise%20Genre%20Count.png'></img>

## Word Cloud of Genres
Filtered the top 100 movies based on the ratings given by the users. With the cleaned csv file prepared initially, mapped the genre for those movies. Created a word cloud of the genres depicting the most frequent and liked genre in the movies.
Visualization is done in Tableau
<img src='https://github.com/PrithviKamath/MovieRecommendation/blob/master/Images/WordCloud%20for%20top%20100%20movies%20with%20maximum%20ratings.png'></img>

## WordCloud with yearwise movie count
Filtered the movies based on the year and selected the ones between 2000 and 2014. With this list we created a word cloud and added the 15 year distrbution over a tooltip.
<img src='https://github.com/PrithviKamath/MovieRecommendation/blob/master/Images/WordCloud%20with%20yearwise%20movie%20count.png'></img>

## Checking the sparsity of data
Builded a ratings matrix with users as rows, items as columns, and ratings as the elements of the matrix to check the sparsity of data. The sparsity matrix checks for the zero elements in the data. For the movielens dataset, the sparsity is 0.5% which indicates the matrix as sparse with zero values which means not every user has rated a movie.

## Maximum Likelihood Estimation Implementation
Filtered the ratings for movie with movieId equal to 1 i.e. ratings for 'Toy Story'.
Sampled the movies into 5 bins based on ratings. Fitted the sample into normal distribution.
The sample appears to be left skewed indicating a unimodal distribution.
Plotted the maximum likelihood estimation for the sampled data and estimated the parameters viz. mean and variance for the sample.
<img src='https://github.com/PrithviKamath/MovieRecommendation/blob/master/Images/MLE.png'></img>

## Representing and extracting data using RDD
Initially we trained and tested our model on a small dataset with around 10,000 ratings.
Using Spark RDD, read those ratings and movies file. First of all, created spark object using SparkContext(), which tells Spark how to use a cluster.Performed transformations on the dataset using lambda functions where we extract the cell values from the dataset and map those into tuples. The header for the csv files is removed.

## Training, Validation and Test Data
Splitting the dataset into training, validation and test with 60%, 20% and 20% distribution respectively.

## Implementing Alternating Least Square Algorithm
Focusing on collaborative filtering models which can be generally split into two classes: user- and item-based collaborative filtering. In either scenario, one builds a similarity matrix. For user-based collaborative filtering, the user-similarity matrix will consist of some distance metric that measures the similarity between any two pairs of users. Likewise, the item-similarity matrix will measure the similarity between any two pairs of items.
we multiply each feature of the user by the corresponding feature of the movie and add everything together, this will be a good approximation for the rating the user would give that movie.

Opting for the best model with the lowest RMSE value.
For rank 2 we get the low RMSE value of 0.99719.
Calculating the error on the testing dataset.
All the operations are initially being tested on the small dataset.

## Recommending movies to a new user
Once the model is trained, the model is tested by adding up a new user and the ratings he gave to the movies he has watched.
Based on this, the system now recommends movies to the user.

## Output
<img src='https://github.com/PrithviKamath/MovieRecommendation/blob/master/Images/Output.png'></img>

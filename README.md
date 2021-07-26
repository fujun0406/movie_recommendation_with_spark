# Project - Movie Recommendation with Spark

## Contents
* [Background](#background)
* [Dataset](#dataset)
* [Methodology](#methodology)
* [Results](#results)

## Background
Recommender System is a system that predict ratings or preferences user may give to this item. It is a method to recommend things to people based on their past behaviour. We often sort or present as "top-N" recommendations which means recommendating people a set of N items from a large collection of items. In this project, we use Apache Spark SparkMLib(ALS) and deep learning to build recommender systems which can provide recommendations to a user.

## Dataset
This data come from [Kaggle MovieLen](https://www.kaggle.com/snehal1409/movielens). 

It contains 671 user, 9125 movies and 100004 ratings and there are no missing values in `ratings.csv` and `movies.csv`. The range of rating is between 0.5 and 5 and most user give score 3 or 4.

|   |userId	|movieId |rating	|timestamp |
|:-:|:-----:|:------:|:------:|:--------:|
|0	|1	    |31	     |2.5     |1260759144|
|1	|1	    |1029	   |3.0     |1260759179|
|2	|1	    |1061	   |3.0     |1260759182|

<em>Table 1: `ratings.csv` file.</em>

|   |movieId|title                    |genres                                         |
|:-:|:-----:|:-----------------------:|:---------------------------------------------:|
|0  |1      |Toy Story (1995)         |Adventure, Animation, Children, Comedy, Fantasy|
|1  |2      |Jumanji (1995)           |Adventure, Children, Fantasy                   |
|2  |3      |Grumpier Old Men (1995)  |Comedy, Romance                                |

<em>Table 2: `movies.csv` file.</em>

## Methodology
In this project, we utilize two algorithms to build model which are ALS and deep leraning. In terms of ALS algorithm, it is a popular algorithm whihc is implemented in [Apache Spark ML](https://spark.apache.org/docs/latest/api/python/reference/api/pyspark.ml.recommendation.ALS.html#pyspark.ml.recommendation.ALS) and built for a larges-scale collaborative filtering problems. So, we consider to use the method in this dataset. For the deep learning algorithm, we use [Keras](https://keras.io/) to construct network. In this project, we only tune the rank parameter in ALS alogrithm, if we consider hyperparameter or different topologies toward both methods, the results may be different.

## Results
For the userID 474, different algorithms provide different recommendations. The results as following,

|Movies with high ratings from user |
|:------------------------------   |
|Philadelphia Story, The (1940) : Comedy,Drama,Romance <br> Local Hero (1983) : Comedy <br> Singin' in the Rain (1952) : Comedy,Musical,Romance <br> Princess Bride, The (1987) : Action,Adventure,Comedy,Fantasy,Romance <br> Godfather: Part II, The (1974) : Crime,Drama|

|Algorithm  |Recommendations   |Algorithm  |Recommendations   |
|  :----:   |:----             |  :----:   |:----             |
|ALS        | Baraka (1992) : Documentary <br> Dear Zachary: A Letter to a Son About His Father (2008) : Documentary <br> Benji (1974) : Adventure,Children <br> Education, An (2009) : Drama,Romance <br> It's a Mad, Mad, Mad, Mad World (1963) : Action,Adventure,Comedy,Crime <br> Fountain, The (2006) : Drama,Fantasy,Romance <br> Frozen (2013) : Adventure,Animation,Comedy,Fantasy,Musical,Romance <br> Wings of Desire (Himmel über Berlin, Der) (1987) : Drama,Fantasy,Romance <br> Big Easy, The (1987) : Action,Crime,Mystery,Romance,Thriller <br> Hedwig and the Angry Inch (2000) : Comedy,Drama,Musical |deep learning  |Patriot, The (2000) : Action,Drama,War <br> Exorcist, The (1973) : Horror,Mystery <br> Charlie and the Chocolate Factory (2005) : Adventure,Children,Comedy,Fantasy,IMAX <br> Double Jeopardy (1999) : Action,Crime,Drama,Thriller <br> Rebel Without a Cause (1955) : Drama <br> Ghost World (2001) : Comedy,Drama <br> Scream 2 (1997) : Comedy,Horror,Mystery,Thriller <br> Hoosiers (a.k.a. Best Shot) (1986) : Drama,Romance <br> Munich (2005) : Action,Crime,Drama,Thriller <br> Man with Two Brains, The (1983) : Comedy |

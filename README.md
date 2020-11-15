# Movie Data -Extract Transform Load (ETL)

## Overview
The propose of this project is to help Britta a member of the Amazing Prime video team extract the data from two different sources: ```Wikipedia and MovieLens```, merge it into a single data set, and finally load that data set into Postgres SQL database so that end user has access to a clean dataset. The movies data is gathered from Wikipedia and their ratings from MovieLens, which is a movie rating website.

**Data Sets**

-	```movies_metadata.csv```:  Metadata file with details about the movies from IMDB.

-	```ratings.csv```: Movie ratings data from MovieLens website on Kaggle.

-	```Wikipedia-movies.json``` : Data pulled from Wikipedia about movies and formatted as a JSON file.

## ETL Process

1.```ETL_function_test.ipynb```

- A function is defined and reads data from Wikipedia, Kaggle and Movielens. Then Data Frame is created for each of the files.

2.```ETL_clean_wiki_movies.ipynb ```
-	The Function defined cleans the Wikipedia data to contain data with 'imdb_link' and ('Director' or 'Directed by') keys and not 'No. of episodes'.
-	A list comprehension is created to iterate through the cleaned wiki movies list.
-	A ```try-except``` block of code is written to catch errors while extracting the IMDb IDs with a regular expression string and ```imdb_id``` duplicates are dropped off. If there is an error, an exception is printed.

3.```ETL_clean_kaggle_data.ipynb``` 

-  After the Wikipedia data is cleansed, ```kaggle_metadata``` and ```ratings``` Data Frames are created.
- The Kaggle metadata data frame is merged with the Wikipedia movies data frame to create the ```movies_df``` data frame. 
- Finally, the MovieLens rating data frame is merged with the ```movies_df``` data frame to create the```movies_with_ratings_df```.
- Merge the Wikipedia dataset with Kaggle data. Update and drop fields that exist in both datasets.

4.```ETL_create_database.ipynb```

- A copy of the ```ETL_clean_kaggle_data.ipynb``` file is created and the  Movie Database is loaded to the PostgreSQL.

## Result

 **Movies Data**
![ Movie data.png](https://github.com/smj452/Movies-ETL/blob/main/Resources/Movie%20data.png)

**Ratings Data**
![ Ratings Data.png]( https://github.com/smj452/Movies-ETL/blob/main/Resources/Ratings%20Data.png)




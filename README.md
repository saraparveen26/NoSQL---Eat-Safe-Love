# Eat Safe, Love - Exploratory Analysis

This challenge is completed as requirement of Data Analytics Boot Camp at University of Toronto.

This assignment performs data exploration and analysis using PyMongo. The data for this assignment comes from UK Foods Standard Agency, which evaluates various establishments across the United Kingdom and gives them a food hygiene rating. The objective is to evaluate some of the ratings data as requested bhy the editors of a food magazine, *Eat Safe, Love*. The purpose of this evaluation is to help the journalists of the magazine and food critics decide where to focus future articles.

This assignment consists of three parts. The first two parts are completed in the Jupyter Notebook named *NoSQL_setup_solved.ipynb*. The third part is completed in the Jupyter Notebook named *NoSQL_analysis_solved.ipynb*.


## Part 1: Database and Jupyter Notebook Setup

This part starts by importing the dependencies. The next step involves importing the data provided in the *establishments.json* file which is stored in the *Resources* folder. This file can be imported through Terminal or GitBash with the code which is added in the first Markdown cell. Alternatively it can be imported by running the code itself in the Jupyter Notebook. 

The next step is to create an instance of the Mongo Client. Then all the databases in MongoDB are listed confirming *uk_food* is listed there which is then assigned to a variable. Then all the collections in the database are listed confirming *establishments* is listed there which is then assigned to a variable and one of its documents is printed to review.


## Part 2: Update the Database

This part includes updating the database for an exciting new Halal restaurant which has just opened in Greenwich but has not been rated yet. The magazine requested to include this new restaurant named "Penang Flavours" to the database.

This part starts by creating a new dictionary containing the data about the new restaurant and then inserting that dictionary into the eixsting collection. Then a query is performed to find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the BusinessTypeID and BusinessType fields. The BusinessTypeID of the new restaurant is then updated from the results found through the query.

The next step is to removed any documents that contain Dover as the magazine is not interested in any establishments in the Dover Local Authority. First, we count the documents containing Dover in LocalAuthorityName which comes at 994. Then all the documents containing Dover are deleted. The documents containing Dover are counted again which give a result of zero confirming that documents were deleted properly. 

Then some of the number values which are stored as string but should be numbers are evaluated. The latitude and longitude data is converted to Decimals. 


## Part 3: Exploratory Analysis

This section performs analysis of the data to answer some specific questions asked by the magazine. Some notes to be aware of to probide better understanding of analysis are:

- RatingValue refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating. Note: This field also includes non-numeric values such as 'Pass', where 'Pass' means that the establishment passed their inspection but isn't given a number rating.

- The scores for Hygiene, Structural, and ConfidenceInManagement work in reverse. This means, the higher the value, the worse the establishment is in these areas.

The database is analyzed to answer the following questions:

### *Question 1: Which establishments have a hygiene score equal to 20?*

This question is answered by first creating a query to only select the data with hygiene score of 20. Then the number of documents contained in the result based on query are counted which equals to 41. The first document in the result is printed using pprint. Then the results are converted into Pandas DataFrame and the number of rows are printed which again equals 41. The first 10 rows of the DataFrame are then displayed.

### *Question 2: Which establishments in London have a RatingValue greater than or equal to 4?*

This question is answered by first creating a query to only select the data for establishments in London and with a RatingValue of 4 or higher. Then the number of documents contained in the result based on query are counted which equals to 34. The first document in the result is printed using pprint. Then the results are converted into Pandas DataFrame and the number of rows are printed which again equals 34. The first 10 rows of the DataFrame are then displayed.

### *Question 3: What are the top 5 establishments with a RatingValue of '5', sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?*

This question is answered by first retrieving the latitude and longitude values of the restaurant, "Penang Flavours". Then a search criteria is defined to find the nearest locations within 0.01 degree on either side of the latitude and the longitude of "Penang Flavours". The next step involves creating a query to only select the data for establishments nearest to the new restaurant and with a RatingValue of 5. The results are also sorted by the lowest hygiene score and limited to 5 to get the top 5 restaurants only. All the documents in the result based on query, sort and limit are stored in a list and then printed using pprint. Then the results are converted into Pandas DataFrame containing 5 rows which is then displayed.

### *Question 4: How many establishments in each Local Authority area have a hygiene score of 0? Sort the results from highest to lowest, and print out the top ten local authority areas*

This question is answered by using the aggregation method. First, a match query is created to get the data which matches the establishments with a hygiene score of zero. Then a group query is created to group the matches by LoalAuthorityName and get their count. Then a sort query is designed to sort the values in descending order of the count. A pipeline is then created using the match, group and sort queries. The results are then retrieved using aggregagtion on the pipeline. The number of documents contained in the result are counted which equals to 55. The first 10 documents in the result are printed using pprint. The results are then converted into Pandas DataFrame and the number of rows are printed which again equals 55. The first 10 rows of the DataFrame are then displayed.
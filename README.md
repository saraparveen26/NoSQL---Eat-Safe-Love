# Eat Safe, Love - Exploratory Analysis

This challenge is completed as requirement of Data Analytics Boot Camp at University of Toronto.

This assignment performs data exploration and analysis using PyMongo. The data for this assignment comes from UK Foods Standard Agency, which evaluates various establishments across the United Kingdom and gives them a food hygiene rating. The objective is to evaluate some of the ratings data as requested bhy the editors of a food magazine, *Eat Safe, Love*. The purpose of this evaluation is to help the journalists of the magazine and food critics decide where to focus future artiles.

This assignment consists of three parts. The first two parts are completed in the Jupyter Notebook named *NoSQL_setup_solved.ipynb*. The third part is completed in the Jupyter Notebook named *NoSQL_analysis_solved.ipynb*.


## Part 1: Database and Jupyter Notebook Setup

This part starts by importing the dependencies. The next step involves importing the data provided in the *establishments.json* file which is stored in the *Resources* folder. This file can be imported through Terminal or GitBash with the code which is added in the first Markfown cell. Alternatively it can be performed by running the code itself in the Jupyter Notebook. 

The next step is to create an instance of the Mongo Client. Then all the databases in MongoDB are listed confirming *uk_food* is listed there which is then assigned to a variable. Then all the collections in the database are listed confirming *establishments* is listed there which is then assigned to a variable and one of its documents is printed to review.


## Part 2: Update the Database

This part includes updating the database for an exciting new Halal restaurant which has just opened in Greenwich but has not been rated yet. The magazine requested to include this new restaurant named "Penang Flavours" to the database.

This part starts by creating a new dictionary containing the data about the new restaurant and then inserting that dictionary into the eixsting collection. Then a query is performed to find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the BusinessTypeID and BusinessType fields. The BusinessTypeID of the new restaurant is then updated from the results found through the query.

The next step is to removed any documents that contain Dover as the magazine is not interested in any establishments in the Dover Local Authority. First, we count the documents containing Dover in LocalAuthorityName which comes at 994. Then all the documents containing Dover are deleted. The documents containing Dover are counted again which give a result of zero confirming that documents were deleted properly. 

Then some of the number values which are stored as string but should be numbers are evaluated. The latitude and longitude data is converted to Decimals. 


## Part 3: Scrape and analyze Mars weather data, which exists in a table

This section involves scraping the [Mars Temperature Data Website](https://static.bc-edx.com/data/web/mars_facts/temperature.html) as shown in the Jupyter notebook named *part_2_mars_weather.ipynb* by performing the following steps:

1. Use automated browsing to visit the [Mars Temperature Data Website](https://static.bc-edx.com/data/web/mars_facts/temperature.html) and then inspect the page to identify which elements to scrape.

2. Create a Beautiful Soup object and use it to scrape the data in the HTML table.

3. Assemble the scraped data into a Pandas DataFrame. The columns have the same headings as the table on the website. This is achieved by scraping and storing header rows separately than the rest of the rows data in the table.

4. Examine the data types that are currently associated with each column and then converting the data to the appropriate datetime, int, or float data types.

5. Analyze the dataset by using Pandas functions to answer the following questions:

### *How many months exist on Mars?*

There are 12 months on Mars.

### *How many Martian days' worth of data are there?*

There is 1867 Martian days' worth of data in this dataset.

### *What is the average low temperature by month?*
### *What are the coldest and the warmest months on Mars (at the location of Curiosity)?*

The following chart is created to display the average low temperatures by months.

![alt text](Mars/Output/Fig1.png)

Month 3 is the coldest month on Mars with an average temperature of -83.31 Celsius.

Month 8 is the hottest month on Mars with an average temperature of -68.38 Celsius.

On average, the third month has the coldest minimum temperature on Mars, and the eighth month is the warmest. But it is always very cold there in human terms!

### *What is the average pressure by Martian month?*
### *Which months have the lowest and the highest atmospheric pressure on Mars?*

The following chart is created to display the average atmospheric pressure by months.

![alt text](Mars/Output/Fig2.png)

Month 6 has the lowest atmospheric pressure on Mars which is 745.05.

Month 9 has the highest atmospheric pressure on Mars which is 913.31

Atmospheric pressure is, on average, lowest in the sixth month and highest in the ninth.

### *How many terrestrial (earth) days are there in a Martian year?*

This question is answered by taking into consideration the number of days elapsed on Earth in the time that Mars circles the Sun once.

The result is visually estimated by plotting the daily minimum temperatures against Sol (Martian days). The following chart is created to display the results and identify peaks:

![alt text](Mars/Output/Fig3.png)

The distance from peak to peak is roughly 1490-808, or 682 days. A year on Mars appears to be about 682 terrestial/ earth days from the plot. Internet search confirms that a Mars year is equivalent to 687 earth days. This means that our visual estimate is within 25% of the actual number.

6. The last step includes exporting the DataFrame to a CSV file named *mars_weather_data.csv* which is stored in the Output folder.
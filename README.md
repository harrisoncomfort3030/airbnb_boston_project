# airbnb_boston_project
Udacity Intro to Data Science Project

Date: January 16, 2021

I. Project Motivation

Aside from the fact that a project testing my understanding and ability to apply the CRISP-DM process outlined for questions through communication is required by the Udacity Introduction to Data Science module, I am personally interested in ways to generate income sources outside of a traditional 9-5 full-time role.

As you may be aware, AirBnB recently completed an initial public offering and is currently valued at approximately $100bn. A large driver for this valuation is the fact that AirBnB has enabled a widey adopted platform which allows anybody with a residence to rent their lodging to a member of the general public, where AirBnB serves as a marketplace, administrative and governance entity. 

The dataset in question focuses only on the Boston area. As both a potential vistor of Boston, and potential host for an AirBnB lodging, I was curious about the best value for money in the Boston area as well as what makes a lodging expensive and highly rated.

II. Libraries Used

This projet is writted in Python uses the following libraries:

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_squared_error
%matplotlib inline


III. Files Overview

In addition to this READ_ME.md, there are three other key files in this repository.

1) listings.csv - a CSV file with 95 columns and 3,585 rows for unique lodging stays in the Boston Area. The columns includes various information about the host, property, listing, guest and review. With this dataset, it is clear that we will be able to explore topics relevant to my interest area: best value for money and factors that impact price / ratings.

2) airbnb_project.py - a Python file that includes the aforementioned libraries, as well as analysis and outputs to inform the blog post. It attempts to follow the CRISP-DM process outlined in this course.

3) HC_AirBnB_Blog_Post - a text file that attempts to summarize the key takeaways from the CRISP-DM process. 

IV: Necessary Acknolwedgments:

In addition to the above libraries, these online resources: https://pbpython.com/currency-cleanup.html, https://jamesrledoux.com/code/group-by-aggregate-pandas, https://stackoverflow.com/questions/49791246/drop-columns-with-more-than-60-percent-of-empty-values-in-pandas, as well as the Pandas documentation. I also receieved support from Udacity instructor Rajat S on my LinearRegression function.


V: CRISP-DM Model Overview:

A) Business Understanding 

We are interested in answering three specific questions:

- What neighborhoods in Boston have the best value for money?
- What factors impact price per lodging?
- What factors impact ratings on lodgings?

B) Data Understanding

After reviewing the listings.csv file using the above libraries, as well as pandas functions such as df.info(), df.column.values_count(), df.describe(), and df.head(), it became clear that the data was suitable to help annswer my questions.

C) Preparing Data

Please see the airbnb_project.py file for more details. One of the main changes that needed to occur was converting the price column to a float from an object. The function: clean_price_column(df, column='price') does this. Furthermore, it is necessary to remove unnecessary columns (specifically columns that are all or mostly NANS, all one variable, are text focused as I don't yet know how to meaningfully analyze text, or are columns associated with the hosts themselved). This preparation mostly occurs in this function: clean_data_for_linear_model(df, response_col, test_size=.3, rand_state=42)

D) Data Modeling

I interepret this to refer to the process of creating an output to evaluate the results. Please see the airbnb_project.py file for more details. For the first question, I was able to use group by and aggregation formulas to calculate the average rating and price per neighborhood. For the second two questions, I created the functions; clean_data_for_linear_model(df, response_col, test_size=.3, rand_state=42), and get_coefs_for_linear_model(coefficients, train_data) to understand the strength of the relationship between the various normalized categories and the price and review_scores_rating variables.

E) Evaluate the Results

For the first question, I created a clustered bar chart with two y-axis (price per lodging and rating) per neighborhood. For the second to questions I created a new dataframe and captured the first 10 inputs through df.head(10).

F) Deploy

Please see the blog post for key a summary of analysis.

VI. General Conclusions

- The neighborhoods West Roxbury and Roslindale appear to offer the best value for money.
- It appears that hosts with lower acceptance rates, fast response times and lodgings within certain neighborhoods have the highest correlation with prices. Frankly, I think that low acceptance rates / fast response times are indicative of hosts that take a lot of pride in their lodging, and therefore, they are able to charge a premium for their lodgings, however, this would need to be studied further.
- It appears that acceptance rates have a high correlation to ratings. While 47% and 50% are lower acceptance ratings with strong correlations to ratings, on the aggregate, these acceptance rates look to be higher than the ones with high correlations to price, so perhaps hosts with higher acceptance rates score higher on ratings (potentially they are less high maintenance / picky) and this general sentiment of being relaxed scores well with guests. This would clearly need to be investigated further. 


VII. Other

Kindly note that I have been studying data science since August 15 through Udacity. I have completed the Introduction to Programming for Data Science (Pyton) and the Data Analyst nanodegrees. Please advise of any feedback, and note that I eager to continue my studies. 

# The Yelp Dataset - A graphical Analysis


### Final Project Data 620
> I use the graphs and some of the tools we have learned through social network analysis to discover some relationships in the Yelp Dataset.
I  utilize the Yelp Open dataset (https://www.yelp.com/dataset/), to understand trends in the food industry and users who utilize yelp to provide reviews and feedback. The goal of the analysis is to understand for a major urban area, focusing on the food industry and restuarants in particular: What are the relationships between users who provide reviews and the businesses that they review?  


#### 1. Overview of the Dataset

The dataset consists of a data subset provided for research by Yelp. The dataset consists of various business and user attributes and photos uploaded by businesses and users. For this project I only utilize the businesses and user attributes to the conduct the analysis. The business and user attributes consist of the following key attributes: 

> Information on Businesses:

There is information on businesses, such as the number of reviews, locations, the type of business and other attributes like the type of cusines offered at the restuarant.

![](images/business_sample.png)

> Information on Users:

There is information on users, such as the number of reviews, number of fans, reviewers who are friends.
 
![](images/users.png)

> Information on Reviews:

Actual text of the reviews and the user-id that created the review is also provided, along with rating provided by the reviewer. 

![](images/reviews.png)

#### 2. Analysis of the data
The analysis below summarizes some of the data cleaning and data munging steps that were taken. I also describe in greater detail descriptions of the data

##### 2.1 Analyzing data from the Businesses
Initial counts of all business indicate that a significant part of the database is located in Arizona. This followed by business in Nevada and then in Ontario Canada
As shown in the table below about 56,600 businesses are located in Arizona. 

![](images/business_counts.png)

The data is json format. After loading the data, we see that most businesses do not have a very high number of reviews.
However there are some businesses that have a large number of reviews. 

![](images/Business_reviews.png)


##### 2.2 Business Data Cleaning

Since the data was presented in Json format a number of attributes needed some additional processing. For example a number of 
attributes were sublists and had to be parsed out separately. In particular each business had category classifications and a number of 
attributes that other attributes such as the ambience of the business. After the data cleaning steps the data fields are summarized
below:

![](images/business_data.png) 


##### 2.3 Business Data Cleaning

The yelp data contains categories of businesses. Varying degrees of detail are provided and the categories (a total of 8 are retained for further analysis) are not consistent throughout. 
For example, category 1 is typically the more detailed, "Burgers", with category 2, listed as "Restaurants". However, this not always the case and there some cases where category 1 is "Restaurants" while in other cases category 2 is "Restaurants".
Below we check and confirm these:

![](images/rest1.png) 

![](images/rest2.png) 

The final list of restaurants is determined by filtering on the eight categories referenced above, as shown in the code below:

![](images/rest_filter.png) 


As a result of the filtering, out of the aproximately **56,600** businesses in Arizona, only approximately **11,300** are restaurants or food businesses.

##### 2.4 Understanding the Restaurant Data

I conduct some initial analysis on the restaurants. Star rating reviews for the restaurants are shown in the charts below. Two charts are shown, in the left
all restaurant ratings are shown, while in the chart on the right showns only those restaurants that have 20 or more reviews. The main goal is to filter out restaurants that have a number of reviews
which may bias the results.  

![](images/star_ratings.png) 


As a results of the additional filter of considering only those restaurants that have 20 or more reviews consist of **7,364** restaurants out of the starting approximately **11,300** restaurants or food businesses. 

I conduct a further categorization of the number of reviews for each business. 

	- Medium: Between 250 and 500 reviews
	- High: Between 500 and 1000 reviews
	- Very High: Greater than 1000 reviews
	- Low: Otherwise

As can be seen that the "very high" review category, which generally consist of the most popular restaurants has mostly postive reviews, with a star rating of 4 or more.
  

![](images/rating_by_cat.png) 


Finally, the number of review counts for each star rating of a restaurant is shown in the chart below. There is a steep decline in the number of business with a high number of reviews.


![](images/rating_review_count.png) 


##### 2.6 Incorporating User Reviews
User reviews for each restaurant, including some information on the user and the text of the review is provided by Yelp. After some data munging we get the first few observations in the dataset as shown below:

![](images/user_data.png) 

The figure below shows the distribution of the reviews by users. As can be seen from the charts most users have relatively few reviews, however, there are some who are very prolific reviewers. 

![](images/user_reviews.png) 


#### 3. Setting up the Social Network Analysis 

##### 3.1 Categorizing Regional Cusines


##### 3.2 Developing the Final Dataset



#### 7. Next Steps

The are a number of steps that can be taken here that can further improve the recommendations generated, and this analysis is quite simple in its approach. 
- Incorporate additional information into the similarlity calculation. Here we only use the ratings, however, we can use / consider information on movie geners and some of the tags that these movie raters have developed
- Consider additional metrics for the ratings similarity calculation including the use of the baseline predictor


### References
1. F. Maxwell Harper and Joseph A. Konstan. 2015. The MovieLens Datasets: History and Context. ACM Transactions on Interactive Intelligent Systems (TiiS) 5, 4: 19:1–19:19. 
https://doi.org/10.1145/2827872
2. J. Leskovec, A. Rajaraman, J. Ullman: Mining of Massive Datasets, http://www.mmds.org


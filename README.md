
# Capstone: Sephora Reviews 

### Problem Statement

Buying cosmestics is an expensive habit that women all around the world face. A study conducted by Skin Store states that women in New York will spend around $300,000 on skincare and cosmestics products in her lifetime. My wallet has personally felt the impact of how expensive makeup can be, as I have averaged spending over $2,000 on cosmetics alone every year for the last 5 years. 

How can we as consumers save some money on cosmestics? The only option seems to be to either buy cheaper products or wait for something to go on sale. But, how will you know when or even if something will get a markdown? Is there a variable that is a definite indicator of a product going on sale?  

We seek to predict whether or not an item will go on sale using a combination of sentiment analysis on reviews, review key words, user demographic and product information using a suite of classification models including Logistic Regression and Multinomial Naive Bayesian Classifiers. The optimal model will be determined on the basis of accuracy. [Link](https://www.skinstore.com/blog/skincare/womens-face-worth-survey-2017/) 

---

### Datasets

Webscraping datasets:

- [Aggregate ratings]('./datasets_clean/df_ratings_clean.csv')
    - Break down of the count of 1 star, 2 star, 3 star, 4 star, and 5 star ratings as well as the average 
- Product information 
    - Product details including: product brand name, category, product name, product ID, list price, sale price 
- Reviews 
    - Review details and user information such as username, skin type, skin tone, and age range 
- Keyword summaries
    - A count of the top key words found in reviews 

The four datasets above were compiled into one final dataset used in the modeling process. 


### Data Description

Data description for the final data set: 

|Feature|Type|Description|
|---|---|---|
|**brand_name**|*object*|Brand name for each product.| 
|**category**|*object*|Product subcategories that fall into the 4 main categories: face makeup, eye makeup, cheek makeup and lip makeup.|
|**isLimitedEdition**|*object*|True or False for whether a product is a limited edition version.|
|**isNew**|*object*|True or False for whether a product is new or not.|
|**isOnlineOnly**|*object*|True or False for whether a product is only sold online.|
|**isSephoraExclusive**|*object*|True or False for whether a product is exclusively sold at Sephora.|
|**listPrice**|*float*|The regular price for each product.|
|**skuId**|*int*|Product ID.|
|**skuType**|*object*|Product ID type.|
|**avg_rating**|*float*|Average rating out of 5 for each product.|
|**review_count**|*int*|The total count of written reviews left for each product.|
|**total_ratings**|*int*|The total count of numerical ratings that were left for each product.|
|**compound_score**|*float*|Weighted average compound score of the keywords from product reviews.|
|**compound**|*float*|Average compound score based on the written reviews for each product.|

---

### Executive Summary

The goal of this project is to create a model that can accurately classify a sale product based on the features available to the everyday consumer from Sephora's website such as brand name, product category, price, ratings, etc. Given these features, it should be able to predict if the product is likely to go on sale. The data was gathered and scraped from Sephora's website and focuses specifically on makeup products only. The metrics used to score my model were accuracy as this is a classification problem. The final model had an accuracy score of 96% on training data and 95.6% on testing data. This model only works at this current time frame as the data is only a snapshot of when the data was collected and does not include previous items that have gone on sale. Another limitation is that the compound scores for the reviews are not representative of the entire reviews. The reviews collected only go back 6 pages (if there are 6 pages of reviews to scrape) which is a total of 30 reviews. The sample size is quite small but given the time restrictions, I was unable to scrape all of the reviews available on the website. 


---

### Methodology

The first part of the project was to collect data. This involved scraping Sephora's website and understanding their website structure. This required inspecting the elements to find the pattern of the website design. There are four different data sets from the initial scrape: product information, reviews, key words, and aggregate reviews. Keeping these data sets separate made for an easier EDA process. It compartmentalized the different features that were important to the model.

Feature engineering included finding the compound scores for the key words as well as the reviews. Empty values for ratings, reviews and key word scores were imputed with 0. Neural networks are able to understand that 0 values are used to NaN values, therefore in this instance imputing 0 worked. 

The models used were logistic regression and a feed forward neural network. The logistic regression and neural network had very similar accuracy scores. The neural network was used to see if it would handle the zero values differently. 

---

### Conclusion and Next Steps 

 

---

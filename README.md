# Amazon_Vine_Analysis
by Bob Ciminera

### Overview

The purpose of this project is to analyze Amazon reviews written by members of the paid Amazon Vine program to determine whether these members are biased to give favorable reviews. 

The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. 

Companies pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

There are 50 review datasets, each of which contains reviews of a specific product, from clothing apparel to wireless products. 

For this analysis US Book reviews were chosen using the following link "https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Books_v1_00.tsv.gz.

Pyspark was used to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin.

A CSV file of the Vine member and non member reviews was created from PostGre and 
Pandas was used to test for bias in the reviews for Vine versus non Vine members.


### Results

1. Perform ETL on Amazon US Book Reviews  

- ETL to extract, transform, and load the review data was created using the following Pyspark code in Google Colab:  [Amazon_Reviews_ETL.ipynb](https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Amazon_Reviews_ETL.ipynb)

- Four DataFrames were created from the dataset extracted from AWS:

- The extracted dataset was then transformed into four DataFrames for customer, product, review, and vine data:

   <img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/Books_customers_df.png" width = "600" >
    <img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/Books_products_df.png" width = "600" >
    <img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/Books_review_id_df.png" width = "600" >
     <img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/Books_vine_df.png" width = "600" >

- Each DataFrame was then loaded into an AWS RDS database and then extracted into PostGre tables: 

    
     <img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/Books_customers_table.png" width = "800" >



    <img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/Books_products_table.png" width = "800" >


  
    <img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/Books_review_id_table.png" width = "800" >


     <img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/Books_vine_table.png" width = "800" >



2. Determine Bias of Vine Reviews

To determine if there is any bias towards reviews that were written as part of the Vine program Pandas was used to test whether having a paid Vine review makes a difference in the percentage of 5-star reviews.

Pandas code was written in Jupyter Notebook to transform the vine_table.csv file to analyse wheter Vine reviews were more favorable as a % of total reviews. The linke to the Pandas code is [Vine_Review_Analysis.ipynb](https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Vine_Review_Analysis.ipynb)


A DataFrame was created for the vine_table data:

<img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/vine_csv_load.png" width = "600" >

The data is filtered to create a DataFrame or table where there are 20 or more total votes:

<img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/20plus_votes.png" width = "600" >

The data was filtered to create a DataFrame where the percentage of helpful_votes is equal to or greater than 50%:

<img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/helpful_50pct.png" width = "600" >

The data was filtered to create a DataFrame where there is a Vine review and another dataframe where there was not a Vine review:
 
<img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/vine_reviews.png" width = "600" >

The total number of votes, the number of 5 star reviews, and the percentage of 5 star reviews were then calculated:

<img src="https://github.com/rciminera/Amazon_Vine_Analysis/blob/main/Screen%20Shots/results_df.png" width = "500" >



### Summary

In summary, for US Amazon Book reviews, paid Vine review members gave a lower percentage (40.5%) of favorable reviews than the non members (45.7%).

1. There were a total of 5.012 Vine reviews and 109,297 non-Vine reviews.
2. 2,031 Vine reviews were 5 stars and 49,967 non-Vine reviews were 5 stars.
3. 40.5% of Vine reviews were 5 stars whereas 45.7%  of non-Vine reviews were 5 stars.

Therefore, in US Book reviews, Vine members do Not show a favorable review bias despite the fact that they are members of the Vine program.  
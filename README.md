# Amazon_Vine_Analysis
by Bob Ciminera

### Overview

The purpose of this project is to analyzing Amazon reviews written by members of the paid Amazon Vine program to determine whether there is any bias toward favorable reviews from Vine members. 

The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. 

Companies pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

There are 50 review datasets, each of which contains reviews of a specific product, from clothing apparel to wireless products. 

For this analysis US Digital Music Purchases was chosen for the analysis.  Pyspark was used to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. 

From there, Pandas was used to test for bias in the reviews for Vine versus non Vine members.


#### Results

Results: Using bulleted lists and images of DataFrames as support, address the following questions:




1. Perform ETL on Amazon Product Reviews

US Digital Music surveys.  

ETL using the following code
[Amazon_Reviews_ETL.ipynb](notebook code)

- An Amazon Review dataset is extracted as a DataFrame. Using PySpark on Google Colab, the US Digital Music review dataset was extracted from AWS and converted into a dataframe using the following code.                               

    [githublogo](Extract code snippet here)

- The extracted dataset was then transformed into four DataFrames, as follows:

    [githublogo](customer)
    [githublogo](product)
    [githublogo](review)
    [githublogo](vine)

- ALL DataFrames are loaded into their respective tables in pgAdmin using the following code.

    [githublogo](customer)
    [githublogo](customer)
    [githublogo](product)
    [githublogo](review)
    [githublogo](vine)

2. Determine Bias of Vine Reviews

To determine if there is any bias towards reviews that were written as part of the Vine program Pandas was used to test whether having a paid Vine review makes a difference in the percentage of 5-star reviews.




### Summary

1. How many Vine reviews and non-Vine reviews were there?
2. How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?
3. What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?
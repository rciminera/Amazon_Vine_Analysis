# Amazon_Vine_Analysis
by Bob Ciminera

Overview


### 1. Perform ETL on Amazon Product Reviews

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




# Amazon_Vine_Analysis


## Overview of Analysis:

We have been asked to analyze Amazon reviews written by members of the paid Amazon Vine program.  We have chosen a random dataset (sports) and used PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Next we used PySpark to determine if there was any bias toward favorable reviews from Vine members in the dataset. The analysis is for SellBy stakeholders


## Resources:

Software:<br/> 
Google Colab<br/>
PySpark version 3.0.3<br/>
pgAdmin4 version 5.2<br/>
PostgreSQL version 12.7<br/>
 
Code:<br/> 
[Amazon_Reviews_ETL.ipynb](Amazon_Reviews_ETL.ipynb)<br/>
[Vine_Review_Analysis.ipynb](Vine_Review_Analysis.ipynb)<br/>

Images:<br/>
[Images](Images/) <br/>

Data:<br/>
https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Sports_v1_00.tsv.gz <br/>


## Amazon Reviews Dataset:

We extracted the Amazon Review Dataset and created a DataFrame.  That DataFrame was transformed into four new DataFrames and loaded into tables in pgAdmin.

Initial DataFrame <br/>
![dataset.png](Images/dataset.png) <br/>

Customer DataFrame <br/>
![customers_df.png](Images/customers_df.png) <br/>

Products DataFrame <br/>
![products_df.png](Images/products_df.png) <br/>

Review ID DataFrame <br/>
![review_id_df.png](Images/review_id_df.png) <br/>

Vine DataFrame <br/>
![vine_df.png](Images/vine_df.png) <br/>


## Determine Bias of Vine Reviews 




## Results of VIne Reviews

- 61948 total amount of combined reviews<br/>

- 32804 total amount of 5 Star Reviews<br/>

- 139 total amount of 5 Star Vine Reviews<br/>

- 32665 total amount of 5 Star non-Vine Reviews<br/>

- 0.42 percentage of 5 Star Vine Reviews<br/>

- 99.58 percentage of 5 Star non-Vine Reviews<br/>

## Summary


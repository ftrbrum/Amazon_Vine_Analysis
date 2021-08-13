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

To start, the DataFrame was filtered to retrieve all the rows that had a count equal to or greater than 20.  This was to pick reviews that are more likely to be helpful and avoids having to divide by zero later on.

![vote_count_20.png](Images/vote_count_20.png) <br/>

The new DataFrame created was filtered to retrieve all the rows where the number of "helpful_votes" divided by "total_votes" was equal to or greater than 50%.

![vote_count_50.png](Images/vote_count_50.png) <br/>

This DataFrame was used to create 2 new DataFrames to sort our data.  One DataFrame was created to showcase all 5 Star reviews by Vine members and the other to showcase 5 Star reviews from non-Vine members.

![vine_program_y.png](Images/vine_program_y.png) <br/>
![vine_program_n.png](Images/vine_program_n.png) <br/>


## Results of VIne Reviews

- 61948 total amount of combined reviews<br/>

- 32804 total amount of 5 Star Reviews<br/>

- 139 total amount of 5 Star Vine Reviews<br/>

- 32665 total amount of 5 Star non-Vine Reviews<br/>

- 0.42 percentage of 5 Star Vine Reviews<br/>

- 99.58 percentage of 5 Star non-Vine Reviews<br/>


## Summary

We can deterrmine from our data that there is not a positivity bias for reviews in the Vine program.  Over 99.5% of 5 star reviews in the sports category were from non-Vine members.  We beleive that Vine members have a tendency to be more critical in the reviews of products.  To get a better understanding of the data we can use the "verified_purchase" column to sort reviews based on purchase.  That would be able to tell us how many people that purchased the products gave favourable reviews vs non-purchasers.
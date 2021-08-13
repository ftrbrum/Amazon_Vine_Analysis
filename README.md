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
[images](images/) <br/>

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


## Summary Statistics on Suspension Coils

The mean, median, variance, and standard deviation (SD) of the suspension coil’s PSI for all lots.

![total_summary.png](images/total_summary.png)<br/>

The mean, median, variance, and standard deviation (SD) of the suspension coil’s PSI for each individual lot.

![lot_summary.png](images/lot_summary.png)<br/>

When looking at the combined PSI variance of all production lots, the variance of the coils is 62.29 PSI, which is within the 100 PSI variance required by AutosRUs'.

Lot 1 and Lot 2 are within the 100 PSI variance requirement (Lot 1 has 0.98 and Lot 2 has 7.47).

Lot 3 has a variance of 170.29 and does not meet the 100 PSI variance required by AutosRUs' and inflates the total variance seen in the total summary of the combined lots.


## T-Tests on Suspension Coils

Below are t.tests to determine if the PSI across all manufacturing lots is statistically different.

All Lots<br/>
![t_test_1.png](images/t_test_1.png)<br/>

Lot 1 <br/>
![t_test_lot1.png](images/t_test_lot1.png)<br/>

Lot 2<br/>
![t_test_lot2.png](images/t_test_lot2.png)<br/>

Lot 3<br/>
![t_test_lot3.png](images/t_test_lot3.png)<br/>


Across all lots: <br/>

The true mean of the sample is 1498.78 and has a p-Value of 0.06, which is higher than the common significance level of 0.05, there is NOT enough evidence to support rejecting the null hypothesis.  The mean of all three of these manufacturing lots is statistically similar to the presumed population mean of 1500.

Individual lots:<br/>

Lot 1 has the true mean of 1500 and has a p-Value of 1.  We cannot reject the null hypothesis that there is no statistical difference between the observed sample mean and the presumed population mean (1500).

Lot 2 has the true mean of 1500.02 and has a p-Value of 0.61.  We cannot reject the null hypothesis that there is no statistical difference between the observed sample mean and the presumed population mean (1500).

Lot 3 has the true mean of 1496.14 and has a  p-Value is 0.04.  That is lower than the common significance level of 0.05. All indicating to reject the null hypothesis that this sample mean and the presumed population mean are not statistically different.


## Study Design: MechaCar vs Competition

To design the MechaCar to "Best the Competition" we will need to compare many variables against all competing manufaturers.  See below for a list of variables. 

Collecting data for competition models across all manufacturers, from the last model upgrade:

Price<br/>
MPG - City<br/>
MPG - Highway<br/>
Horsepower<br/>
Maintenance<br/>
Re-sale Value<br/>

Null Hypothesis (Ho): MechaCar is priced correctly based on its performance of key factors against competition.<br/>

Alternative Hypothesis (Ha): MechaCar is not priced correctly based on its performance of key factors against competition.<br/>

Statistical Tests
I would collect the mean, median, variance, and standard deviation of the above mentioned variables.  I could collect them as a group and than across individual manufacturers.  After I would compare t.tests to compare the data against the MechaCar.
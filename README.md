# Amazon_Vine_Analysis

## Overview of the Project

In this project we are working with SellBy, a new client who is looking to sell some of their products via Amazon. SellBy heavily values customer reviews on their products and as a result they are particularly interested in the Amazon Vine program, a service that allows manufacturers and publishers to receive reviews for their products. This service requires Amazon Vine members to publish a review on any products they purchase. 

Considering the fact that SellBy would need to pay a fee to Amazon in order to enroll in the Vine program, they want to know if there is any bias in the Vine program reviews. We have been tasked with analyzing Amazon review data in order to determine if reviewers of the Vine program are more likely to leave a 5 star review than reviewers who are not part of the Vine program.

In order to analyze this data we used both PySpark and SQL to perform the ETL process as well as the actual analysis of our data. We begun by extracting the Amazon review data in PySpark via a publicly available S3 bucket. Next, we transormed our data by creating 4 new DataFrames titled:
-- customers_df: a DataFrame that contains a column of unique customer IDs and a column of total reviews that the specific customer has given
-- 

# Amazon_Vine_Analysis

## Overview of the Project

In this project we are working with SellBy, a new client who is looking to sell some of their products via Amazon. SellBy heavily values customer reviews on their products and as a result they are particularly interested in the Amazon Vine program, a service that allows manufacturers and publishers to receive reviews for their products. This service requires Amazon Vine members to publish a review on any products they purchase. 

Considering the fact that SellBy would need to pay a fee to Amazon in order to enroll in the Vine program, they want to know if there is any bias in the Vine program reviews. We have been tasked with analyzing Amazon review data in order to determine if reviewers of the Vine program are more likely to leave a 5 star review than reviewers who are not part of the Vine program.

In order to analyze this data we used both PySpark and SQL to perform the ETL process as well as the actual analysis of our data. We begun by extracting the Amazon review data in PySpark via a publicly available S3 bucket. Next, we transormed our data by creating 4 new DataFrames titled:
- "customers_df": a DataFrame that contains a column of unique customer IDs and a column of total reviews that the specific customer has given.
- "products_df": a DataFrame that contains a columns of unique product IDs and a column displaying the title for each product.
- "review_id_df: a DataFrame where each row contains information for an individual review. Information per row includes review ID, customer ID, product ID, product parent, and review dat.
- "vine_df": a DataFrame where each row contains information for an individual review, only in this table contains information regarding the star rating, helpful votes, total votes, if it's a review left through the Vine program, and verified purchase. 

Once we were finished transforming our data, we then loaded our data from PySpark into our PgAdmin database.

After our data was loaded into our SQL database, we returned to PySpark in order to further analyze our Amazon review data. Since SellBy was interested in learning about any potential review bias for the Vine program, we had to perform some further transformations on our data. We did this by creating a new PySpark file and extracting/transforming the data to match the "vine_df" from our previous steps. We then filtered out reviews that had less than 20 votes, as well as filtered out reviews where the "helpful votes" were less than 50% of the "total votes". 

With this new, transformed data we were able to calculate some data points that would potentially help with answering SellBy's inquiry regarding review bias.

## Results
After transforming our review data, we were able to create the two DataFrames below:

### Vine Program Reviews
![](https://github.com/christianhargett/Amazon_Vine_Analysis/blob/main/vine_paid_df.png)

### Regular Customer Reviews
![](https://github.com/christianhargett/Amazon_Vine_Analysis/blob/main/vine_unpaid_df.png)

Once we were able to create a DataFrame containing only Vine program reviews and a DataFrame containing only normal reviews, we then calculated some summary statistics for each DataFrame.

### Total Review Counts
![](https://github.com/christianhargett/Amazon_Vine_Analysis/blob/main/review_counts.png)

We can see here that there are only 60 Vine program reviews and 14,477 normal customer reviews. This is helpful in determining how many Vine reviews that SellBy can expect for their products, but we still want to determine if there is any bias in reviewers participating in the Vine program

### Five Star Review Statistics (Vine Program vs. Regular Reviews)
![](https://github.com/christianhargett/Amazon_Vine_Analysis/blob/main/five_star_stats.png)

We can see here that 56.67% of Vine program reviewers left five star reviews on products. We can also see that 56.72% of regular reviewers left five star reviews on products.

## Summary

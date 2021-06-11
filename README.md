# Amazon_Vine_Analysis

## Overview 
In this project we have been tasked to analyze Amazon reviews written by members of the paid the paid Amazon Vine Program.  The Amazon Vine Program is a service that allows manufacturers and publishers to recieve reviews for thier products.  Companies pay a small fee to Amazone and provide products to Amazon Vine members, who are then required to publish a review. Using PySpark to perform the ETL process on video game data, we will extract the dataset, transform the data into pgAdmin.  Then using PySpark and Pandas to determine if there is any bias toward favorable reviews from Vine members in the dataset. 


## Results
Four data tables were created: customers, products, review id, and vine.  The original data orginated from: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Video_Games_v1_00.tsv.gz.  Using pgAdmin, the four empty tables were created, and the dataset was created using PySpark. Again, using PySpark the orginal dataset was transform into the four seperate sets. 

- Customer Table: The groupby function to count the customer_id column of the dataform, it was then renamed the count(customer_id).  Then using withColumnRenamed function was loaded to pdAdmin.

![image](https://github.com/snkty8/Amazon_Vine_Analysis/blob/main/images/customers_table.png)

- Products Table:  The select function to select product_id and product_title, and dropping duplicates with drop_duplicates function to retreive only unique product_ids. It was then loaded into pgAdmin.

![image](https://github.com/snkty8/Amazon_Vine_Analysis/blob/main/images/product_table.png)

- Review IDs Table: The select function to select the columns that are in the reveiw_id_table, and converting the review_date column to a date.  The table was then loaded into pgAdmin.

![image](https://github.com/snkty8/Amazon_Vine_Analysis/blob/main/images/review_id_table.png)

- Vine Table: The select function was used to select only the columns that are in the vine_table.  It was then loaded into pgAdmin.

![image](https://github.com/snkty8/Amazon_Vine_Analysis/blob/main/images/vine_table.png)

After further evaluation, the number of Vine and non Vine reveiws were calculated. Using Pandas in Jupyter Notebook, the vine table was exported as a CSV.  The data was filtered and a new dataframe was created to retrieve the total votes count equal or greater than 20 to pick reviews that were more likely to be helpful. Next, the new dataframe was filtered to retrieve all the rows where the number of helpful_votes divided by the total votes equal or greater than 50 percent. From this table the following information was caluclated: 

- Vine reviews: 94
- Non Vine reviews: 40471
- 5-star Vine reviews: 48
- 5-star Non Vine reviews: 15663
- Percentage of 5-star Vine reivews: 51.1%
- Percentage of 5-star Non Vine reviews: 38.7%
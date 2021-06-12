# Amazon_Vine_Analysis

## Overview 
In this project we have been tasked to analyze Amazon reviews written by members of the paid Amazon Vine Program.  The Amazon Vine Program is a service that allows manufacturers and publishers to recieve reviews for thier products.  Companies pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review. Using PySpark to perform the ETL process on video game data, we will extract the dataset, transform the data into pgAdmin.  Then using PySpark and Pandas, determine if there is any bias toward favorable reviews from Vine members in the dataset. 


## Results
Four data tables were created: customers, products, review id, and vine.  The original data orginated from: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Video_Games_v1_00.tsv.gz.  Using pgAdmin, the four empty tables were created, and the original dataset was mulnipulated using PySpark. Again, using PySpark the orginal dataset was transformed into the four seperate sets. 

- Customer Table: To create this table, we used the groupby function in PySpark to count the customer_id column of the dataset, it was then renamed the count(customer_id).  Then loaded into pdAdmin. Below is a screen shot of the pgAdmin table.

![image](https://github.com/snkty8/Amazon_Vine_Analysis/blob/main/images/customers_table.png)

- Products Table:  To create this table, we used the select function in PySpark to select product_id and product_title, and dropped the duplicates with drop_duplicates function to retreive only unique product_ids. It was then loaded into pgAdmin. Below is the screen shot from pgAdmin.

![image](https://github.com/snkty8/Amazon_Vine_Analysis/blob/main/images/product_table.png)

- Review IDs Table: To create this table, we used the select function in PySpark to select the columns that are in the reveiw_id_table, and converted the review_date column to a date.  The table was then loaded into pgAdmin. Below is a screen shot from pgAdmin.

![image](https://github.com/snkty8/Amazon_Vine_Analysis/blob/main/images/review_id_table.png)

- Vine Table: To create this table, the select function was used in PySpark to select only the columns that are in the vine_table.  It was then loaded into pgAdmin. Below is a screen shot of from pgAdmin.

![image](https://github.com/snkty8/Amazon_Vine_Analysis/blob/main/images/vine_table.png)

After further evaluation, the number of Vine and non-Vine reveiws were calculated. Using Pandas in Jupyter Notebook, the vine table was exported as a CSV.  The data was filtered and a new dataframe was created to retrieve the total votes count equal or greater than 20 to pick reviews that were more likely to be helpful. Next, a new dataframe was filtered to retrieve all the rows where the number of helpful_votes divided by the total votes equal or greater than 50 percent. From this table the following information was caluclated: 

- Vine reviews: 94
- Non Vine reviews: 40471
- 5-star Vine reviews: 48
- 5-star Non Vine reviews: 15663
- Percentage of 5-star Vine reivews: 51.1%
- Percentage of 5-star Non Vine reviews: 38.7%


## Summary 
The propuse of this project was to determine if there is favorable bias towards Vine reviewers.  From the data above, the percentage of 5-star Vine reviews is 51.1% versus non-Vine reviews at 38.7%.  Although, there are far more non-Vine reviewers compared to actual Vine reviews there does show a bais towards the Vine reviews.  The is because of the higher percentage of the Vine reviews. If only looking at the percentage of Vine reviewers, a customer would be more inclined to go with these reviews when purchasing video games. It would be a great idea to add the verified purchases to the tables. Although this could also add a slight bias towards Vine reviewers, Amazon could add the fact the video game was purchase, played, and then reviewed.  Rather than allowing customers to blindly agree with only Vine reviewers.


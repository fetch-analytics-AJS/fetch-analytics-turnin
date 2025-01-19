This is the submission for Andrew Shi (andrewshi@math.berkeley.edu). 

**1. New Structured Relational Data Model**

![Screenshot 2025-01-19 at 8 38 02 PM](https://github.com/user-attachments/assets/2dff25b7-7677-4932-8ed6-cb55e9bcb04c)



**2. Queries from Predetermined Questions**

Questions:
- What are the top 5 brands by receipts scanned for most recent month?
- How does the ranking of the top 5 brands by receipts scanned for the recent month compare to the ranking for the previous month?
- When considering average spend from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?
- When considering total number of items purchased from receipts with 'rewardsReceiptStatus’ of ‘Accepted’ or ‘Rejected’, which is greater?
- Which brand has the most spend among users who were created within the past 6 months?
- Which brand has the most transactions among users who were created within the past 6 months?

See the .ipynb for queries. 

**3. Data Quality Issues in the Data Provided**

- There are a lot of duplicates in the users table, which can just be dropped. But only 8 states are represented in the data, and the vast majority of them are from Wisconsin. So this leads me to wonder whether this is a complete data set. 
- The brands table is not particularly useful due to lots of dummy information. About half of the brand_codes are of the form 'TEST BRANDCODE @1612366146176'. 
- The useful information for the receipts is the total amount spent, item lits, and count of purchased items, and for about half of the data, that is just completely missing, rendering the rest of the data useless.
- There are a lot of missing barcodes in the items table created from rewardsReceiptItemList in receipts. This is problematic because that is the key we need to match to brands.barcode. 

**4. Communicate with Stakeholders**

Below is my message to the product or business leader following this prompt:

*Construct an email or slack message that is understandable to a product or business leader who isn’t familiar with your day to day work. This part of the exercise should show off how you communicate and reason about data with others. Commit your answers to the git repository along with the rest of your exercise.*

1. What questions do you have about the data?
2. How did you discover the data quality issues?
3. What do you need to know to resolve the data quality issues?
4. What other information would you need to help you optimize the data assets you're trying to create?
5. What performance and scaling concerns do you anticipate in production and how do you plan to address them?

----------------------------

Dear Product or Business Leader:

It's Andrew from Fetch here. I had a chance to look through your data and had a few questions I wanted to go over before we go deeper into the analysis. 

1. In terms of the users, there are a lot of duplicates. But even after removing them, it turns out the vast majority of the users are from Wisconsin. So I was wondering if this was only a partial data set of users we had.
2. Many of the entries in the receipt list (around 45%) are lacking information on the total amount spent, the item list and the count of purchased items. For the purposes of the analysis we provided today, we simply dropped all the data missing these fields, but it has a large impact on Questions 5 and 6. 
Could you please advise on your end with regards to the missing data?
3. In the receipts table, the field rewardsReceiptItemLIst has many items which are missing their barcode. This is problematic because the barcode is the only way we have to link this table to another table, namely the barcode field of the brands table. Is this data you can backfill on your end? We can still look at quantities like the total amount spent and numbers of items bought per user without it, but without the barcodes we can't give a more detailed breakdown.
4. The data set you provided is is relatively small (each table no more than a thousand or so lines), which is fine for a quick analysis. But once we figure out these data issues and want to start scaling our analysis, perhaps we can look into doing the data analysis on the cloud (AWS, GCP, Azure, etc.). But we can table this discussion until we get closer to that phase.

Feel free to give me a call at 123-456-7890 if you'd like to discuss further, looking forward to hearing back from you. Enjoy the long weekend!

Best,
Andrew

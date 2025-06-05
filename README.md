# Data-Cleaning-Framework
Clean Raw Data in an Excel file. Cleaning nonsensical values, missing values, etc. using a five-step framework called CLEAN
Data Cleaning Framework README
GameZone Dataset Owner: Christine Jiang
Data Type: Excel File
Description: Clean Raw Data in an Excel file. Cleaning nonsensical values, missing values, etc. using a five-step framework called CLEAN:	
C conceptualize the data
L locate solvable values
E evaluate unsolvable values
A augment the data
N note and document
Data Cleaning Philosophy: Few, if any, datasets are perfect. The goal is to clean data so that it’s sufficient to analyze, share, and iterate on.
Data Cleaning Steps:
1.	Remove obvious “dirty” values
2.	Polish & standardize the remaining values
3.	Refine and revisit the data after my initial analysis
Company: sample company named GameZone founded in 2018. This company sells new & refurbished gaming products. Most sales are made online, while other sales are made via their mobile app and a variety of marketing channels to find customers. 
Although this company does not exist and has only 20k records (real life datasets usually have at least 50k records), the dataset is modeled after a realistic dataset because of its business relevance, metrics, dimensions, and messiness. 
Columns (on Orders tab unless otherwise noted):
•	User_ID
•	Order_ID
•	Purchase_TS
•	Ship_TS
•	Product_Name
•	Product_ID
•	USD_Price
•	Purchase_Platform
•	Marketing_Channel
•	Account_Creation_Method
•	Country_Code
•	Country_Code  // on Region Tab
•	Region // on Region Tab
Tabs:
•	Orders
•	Region
I.	Conceptualize the data
Preparation Question & Answer:
1.	Ask myself: what type of data am I reviewing? Understanding the data is primary because I need to know what data is important and what data needs to be prioritized in the cleaning process.

Next, I need to know the business questions that are being asked. This can be the primary step as well. In this example, the question is:
“What are the overall sales trends across a variety of regions?”  This question helps me identify the key metric listed in bullet “b” & the key dimension in bullet “c” listed below.
a.	What does each row represent? 
i.	User_ID - each row is assigned to a User_ID
ii.	Order_ID - the identifier for each order
iii.	Purchase_TS - the date of the order 
iv.	Ship_TS -  the date that the order was shipped
v.	Product_Name – name of the product shipped
vi.	Product_ID – code that identifies the type of product
vii.	USD_Price – price that the customer paid for the product
viii.	Purchase_Platform – the platform that the purchase was made
ix.	Marketing_Channel – how the customer discovered the company’s website
x.	Account_Creation_Method – how the customer’s user account was created (to purchase on the company’s website).
xi.	Country_Code – where the customer is located at the time of purchase.
b.	What are the key metrics? USD price column.
c.	What are the key dimensions? 
i.	Time of purchase (purchase date)
ii.	Date of shipment (ship date)
iii.	Product name
iv.	Purchase Platform
v.	Marketing Channel
vi.	Account creation method
vii.	Country code
II.	Locate solvable values
a.	I try to solve issues without the help of the stakeholder who provided the data initially. A few common solvable issues can be:
i.	Inconsistent data formats
ii.	Inconsistent categorizations
iii.	Nulls (not always able to solve nulls)
iv.	Duplicate values (determine what qualifies as a duplicate)
b.	Add a tab and name it: Issues Log
c.	First round of data cleaning
i.	Look for obvious issues
ii.	Filter to find distinct values
iii.	Create & document an Issue Log tab (within same file) that documents each issue that I find. 
iv.	Duplicated the Orders & Region tabs to maintain integrity of the original data. 
v.	Duplicated each column that I cleaned until I can validate that the revisions are accurate. Sometimes the validation is common sense (like date formats, etc.); other times I’ll need to consult w/ the client/stakeholder to validate.
III.	Evaluate Unsolvable Issues
1.	These types of issues are typically caused by the following categories:
a.	Missing date
d.	Outliers that may/may not represent real events, but I can’t confirm. Outliers are defined as a data point that differs from other observations. In most cases, outliers become clear in the actual analysis when I’m looking at the data, so it’s not something I look for.
e.	Business logic violations, e.g., have a ship date prior to purchase date. 
In these cases, I may need to consult w/ the engineering team who extracted the data for validation. 
2.	If the magnitude of the issue cannot be resolved and it’s less than 20%, it’s a good rule of thumb to disregard the issue, unless otherwise advised by the stakeholder. If I disregard the issue, I still document it in my Issues Log.
3.	I will only impute (change) data when:
•	I have a reliable validation source
•	I have clear business logic to infer the value confidently
•	The focus is  data completeness, and I’m allowed to fill in the data with a representative sample. Ex.:  when filling in missing gender data, I can either refer to other rows w/ similar characteristics or use the most common gender in my dataset.
So for the zero-dollar values in the USD_Price column of the Orders tab, I will not guess or assume so that I can avoid bias (inaccurate/misleading/introducing bias) data.
4.	When I have two date columns, after confirming what the dates mean, I need to ensure that the dates make sense. Ex.: I know that the ship date should be after the purchase date. To do this:
a.	Open my dataset & create a column and give it an applicable name, like “Date Check.” 

Create a  column & name it "Date Check" & enter a formula that will mark each row as "true" if the ship date is before the "purchase date" by entering: =E2>=F2 and copy this down the column. For each “true,” this shows where the product was shipped before it was purchased, which isn’t logical from a business standpoint.

5.	 If the magnitude is greater than 20%, I need to resolve this issue, otherwise, I’ll document it and move on (unless this discrepancy is why the stakeholder asked for the data). I created a column on the issues log  showing a guestimate of the magnitude by percentage. This calculation is the number of rows affected by the issue divided by the total number of rows in the Orders tab : =D2/21865m the convert the result to % adding two decimals using the Excel ribbon.

IV.	Augment the Data (Enhance the data) – this step allows me to:
•	Slice & dice data. Ex.: I could slice the purchase dates into weeks, months, or years; or I can insert columns that add more granular data for the year of purchase & month of purchase, so that I can calculate Time -to -  Ship.
•	Add dimensions for exploration
•	Calculate new metrics – I could insert a column that shows “Time to Ship” time, which shows the # of days between the purchase date & ship date. 

Note: since I’ve already discovered that some ship dates are prior to the purchase date, those values will be negative.
•	Add a column to include the Region using a VLOOKUP. I added a column and entered a VLOOKUP function to enter the region for each row. Two rows for EU & two rows for AP returned blanks so I manually entered EMEA for EU and APAC for AP.
V.	Notate and Document
a)	I make sure that each issue on my Issues Log is completed or comments are listed as to why not. 
b)	I document all the issues that I resolved. 
c)	I include a column showing the magnitude of the issue per row.
d)	Comment assumptions (if any).

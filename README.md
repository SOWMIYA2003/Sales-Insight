# Sales-Insight
## Problem Statement:
A Computer Hardware Manufacuturer Company faces certain problems with respect to it's Bussiness Sales.
Let's say that there is a company named 'A' who supplies computer hardware and peripheral to many clients across India, let's say they have there headquaters in Delhi,India. The sales director of the company is facing so many challenges as the market is growing dynamically. He is facing issues in tracking the sales in regional markets , he's having issues regarding to the insights of the bussiness and therfore he has some regional managers (North India , South india, Central India ) working for his company. Whenever he wants the insights regarding these three region he would approach them and get the details. 

The problem is that these conversations are verbal.Even though the managers come up with excel files , its a hugh number of data for the sales director to go through and figure out the need.

The sales director just expects the managers to give a statistical data which are in simpler terms inorder to focus on the weak area that they need to work on inorder to grow their bussiness further.

## Approach towards End goal : 
Project Planning : We will be using AIMS Grid to tackle the problem and find the strategy to solve the problem.

![0 eDWDhAySSL-OlVg-](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/d11f242c-28e0-4009-91a0-c54b677dc370)

![Screenshot 2023-09-24 231726](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/2e85bc95-ad71-41bd-9c7c-7f9537400c80)

Followed by Data discovery , Data cleaning , Data merging and finally generating an interactive dashboard in Power BI.

## DataSet : 
We are provided with a database named "sales".

The database has five tables namely customers , date , markets , products and transactions. 

### Customer table : 
![a1](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/f78c96af-97e3-4f5c-8e10-2d0f40ac9be1)

### Date table :
![a2](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/39eaf6e4-d577-4a1e-a75a-5af6c6c6b214)

### Markets table :
![a3](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/afb8b151-d36d-495c-9301-40af5d3ba03d)

### Products table :
![a4](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/4509b86e-1898-40ad-a59c-eb2f1c50dfa9)

### Transaction tables : 
![a5](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/318e9d2b-5189-4315-ba13-05714843c034)

## Data Model :

Building the data model. 

Once the data tables are loaded into the PowerBI , it creates a data model that establish the realtion among differnt tables between the coulmns present in the table. This helps the data analyst to analyse the data in a better rate and come up with efficient results.

![11](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/e600e599-6cb9-49d6-ac2d-9620bc806aaa)

## Data wrangling and Data munging :

1 . The above tables may contain some null values.

2 . It might contain some inappropriate values like negative and zero values.

3 . It might have duplicate records.

4 . It might have terms expressed in differnt formats ( example : the monetary terms can vary based on international sales exports).

Inorder to handle all these issues we need to clean the data first. In simple terms , if we resolve the above issues our data tables will be cleaned and secure enough to produce the correct results during data processing.

### Removing the Null values from Markets table (column - zone): 
![ab](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/56bfe2e2-c57e-4658-a436-b279fd5a6686)

![b1](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/00309bcf-f80c-4989-a7ad-6a611f3dc761)
### Removing values that are less than and equal to 0 from transaction table (column - sales_amount):
```
SELECT * FROM sales.transactions where transactions.sales_amount<=0;
SET SQL_SAFE_UPDATES = 0;
DELETE FROM sales.transactions WHERE sales_amount <= 0;
select * from sales.transactions;
```
![b4](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/24095504-a549-4e7e-a27a-8aef509c8c89)

### Converting monetary terms from USD to INR : 
```
SELECT * FROM sales.transactions where currency = "USD" or currency = "USD\r";![image]
```
![aa1](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/c81788b0-31e5-4b1f-8c89-3602d16f52ea)

```
Table.AddColumn(#"Cleanup currency", "normalize_sales_amount", each if [currrency]="USD#(cr)" then [sales_amount]*75 else [sales_amount])
```
![c2n](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/4aef6211-df8c-4c45-b421-3540d6ac153c)


## PowerBI : 
### Interface for creating Report : Data Visualization is done here.
![page](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/8561f2b0-6ff1-48a4-82a9-b595789098ec)

For our problem statement , we need to analyse the market status in different areas or zones to get the inference on the sales. And based on the sales insight and the trends the sales director will implement some ideas and solution to make the weak areas into stronger ones.
### Revenue and Sales :
Revenue and Sales Quantity are created and used as the Base Measures for the dashboard.

![1rev](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/e50ab082-671c-4716-8a69-ed3e3802b3e0)
![1sale](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/b5b8d95c-4685-4a15-8c72-2523db448a7e)
### Revenue By Market :
![1revmar](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/cb643870-e766-4d68-930f-423986fd3824)
### Sales Quantity By Market : 
![1salemar](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/cb38e0a9-0057-4bab-b4b5-491194327ce5)
### Time Scale : 
![1year](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/6a2a68c3-b5c2-4e2b-82e5-43bd09bd3725)
![1date](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/7e9d01fb-3dcb-499e-aba3-377860949d31)
### Top 5 Customers : 
![15cus](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/abf00e6b-5a45-4ea6-8d05-341af517230c)
### Top 5 Products : 
![15pro](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/697a3fe8-1b75-489c-ade4-a416abe41819)
### Revenue Trend : 
![1trend](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/ec9305b0-ebe6-4350-901f-b207191af336)
### Final Report : 
![report](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/d57fc7c5-4149-4b55-8bd6-93fb7ac7e496)


## Validation \ Cross Checking : 


## End goal :

By using the interative PowerBi DashBoard the sales director will be able to 

#1 . track revenue numbers and sales quantity numbers over the years .

#2 . track revenue breakdown by regional states.

#3 . track revenue trends.

Enabling him to finally work on the weak areas and come up with new ideas to grow their bussiness in a effective and efficient manner.

## Links :
##### SQL DOWNLOAD LINK :
```
https://dev.mysql.com/downloads/file/?id=520407
```
##### POWERBI DOWNLOAD LINK : 
```
https://aka.ms/pbidesktopstore
```

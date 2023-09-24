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

## Data wrangling and Data munging :
1. The above tables may contain some null values.

2 . It might contain some inappropriate values like negative and zero values.

3 . It might have duplicate records.

4 . It might have terms expressed in differnt formats ( example : the monetary terms can vary based on international sales exports).

Inorder to handle all these issues we need to clean the data first. In simple terms , if we resolve the above issues our data tables will be cleaned and secure enough to produce the correct results during data processing.

#### Removing the Null values from Markets table (column - zone): 
![ab](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/56bfe2e2-c57e-4658-a436-b279fd5a6686)

![b1](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/00309bcf-f80c-4989-a7ad-6a611f3dc761)
#### Removing values that are less than and equal to 0 from transaction table (column - sales_amount):
```
SELECT * FROM sales.transactions where transactions.sales_amount<=0;
SET SQL_SAFE_UPDATES = 0;
DELETE FROM sales.transactions WHERE sales_amount <= 0;
select * from sales.transactions;
```
![b4](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/24095504-a549-4e7e-a27a-8aef509c8c89)

#### Converting monetary terms from USD to INR : 
```
SELECT * FROM sales.transactions where currency = "USD" or currency = "USD\r";![image]
```
(https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/d09a5926-efeb-431b-94f4-ac87b7323f2c)
```
Table.AddColumn(#"Cleanup currency", "normalize_sales_amount", each if [currrency]="USD#(cr)" then [sales_amount]*75 else [sales_amount])
```
![c2n](https://github.com/SOWMIYA2003/Sales-Insight/assets/93427443/4aef6211-df8c-4c45-b421-3540d6ac153c)

## End goal :

By using the interative PowerBi DashBoard the sales director will be able to 

#1 . track revenue numbers and sales quantity numbers over the years .

#2 . track revenue breakdown by regional states.

#3 . track revenue trends.

Enabling him to finally work on the weak areas and come up with new ideas to grow their bussiness in a effective and efficient manner.




## PowerBI : 


## Links And Reference :
### SQL DOWNLOAD LINK :
```
https://dev.mysql.com/downloads/file/?id=520407
```

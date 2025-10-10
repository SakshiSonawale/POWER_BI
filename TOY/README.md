# Toy Store KPI Report in Power BI (Guided)


## THE SITUATION

You're a brand new Data Analyst for AB Toys, a toy store chain with multiple store locations in Mexico.

## THE ASSIGNMENT
You have access to data containing transactional records from January 2022-September 2023, along with information about products and store locations.
#### Your goal is to build a simple, interactive report that the leadership team can use to monitor key business metrics and high-level trends.


## OBJECTIVE 1: CONNECT AND PROFILE THE DATA

1. Connect to the sales, products, stores, and calendar csv files.
2. Review table columns, check for blank or null values, confirm that datatypes are accurately defined, and identify any primary and foreign keys.
3. Take a moment to profile the data. How many transactions were recorded? How many stores does AB Toys operate? What are the lowest and highest priced products?
- Total Transactions - 829262
- Total Stores - 50
- Lowest priced product - 2.99
- Highest priced product - 39.99

4. Add calculated columns in the calendar table for 'start of month' and 'start of week'.

## OBJECTIVE 2: CREATE A RELATIONAL MODEL
1. Load the tables to the data model and create relationships from the sales table to the products, stores, and calendar tables.
2.Confirm that you are following data modeling best practices. Your model should take the form of a star schema, with 1:many relationships between fact and dimension tables.
3. Create a date hierarchy containing the 'start of month', 'start of week', and 'date' fields.
4. Hide all foreign keys in the sales table from the report view.

## OBJECTIVE 3: ADD CALCULATED MEASURES & FIELDS
1. Create calculated columns in the sales table to pull in 'cost' and 'price' from the products table, then use those fields to calculate the revenue and profit for each transaction.
- Cost = RELATED(products[Product_Cost])
- Price = RELATED(products[Product_Price])
- Revenue = sales[Units] * sales[Price]
- Profit = sales[Revenue] - (sales[Cost] * sales[Units])


2. Create measures to calculate the count of orders ('total orders"), sum of revenue ('total revenue') and sum of profit ('total profit')
- Total Orders = DISTINCTCOUNT(sales[Sale_ID])
- Total Revenue = SUM(sales[Revenue])
- Total Profit = SUM(sales[Profit])
  
BONUS: Can you define new measures to calculate total revenue and profit without referencing any of the calculated columns in the sales table?
- Revenue (M) = SUMX (sales, sales[Units] * RELATED(products[Product_Price]))
- Profit (M) = SUMX( sales, [Revenue (M)] - (sales[Units] * RELATED(products[Product_Cost])))

## OBJECTIVE 4: BUILD AN INTERACTIVE REPORT
1. Add KPI card visuals showing 'total orders', 'total revenue' and 'total profit' for the current month, along with monthly trends for each metric.
2. Add a slicer to filter the report page by store location.
3. Add a bar chart showing 'total orders' by product category, and a line chart showing 'total revenue' with the date hierarchy on the x-axis.
4. Assemble the charts into a logical layout and adjust formatting, alignment and polish to finalize the report as you see fit.





















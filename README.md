# Big Mart Sales 

## References
[1] https://datahack.analyticsvidhya.com/contest/practice-problem-big-mart-sales-iii/

## Description and problem statement
The data scientists at BigMart have collected 2013 sales data for 1559 products across 10 stores in different cities. The aim is to build a predictive model and find out the sales of each product at a particular store. Using this model, BigMart can try to understand the properties of products and stores which play a key role in increasing sales.

## Data
[image]

## Imputing of missing values

### Item_Weight
[image]

[image]

### Outlet_Size

[image]


### Item_Visibility

[image]


## Feature engineering
- Combine Low Fat, low fat and LF to Low Fat and reg and Regular to Regular
- Convert the Outlet_Establishment_Years into how old the establishments are
- Create broader category for type of item
- Change value of the 'Item_Fat_Content' of the items that are non-consumables
- Make a new category for items that reflect their sales - very high, high, medium, low.
- Item_Number_Sales


## Preliminary Analysis

### Item_MRP

### Item_Outlet_Sales

### Item_Number_Sales

### Item_outlet_sales and Item_MRP vs Item_Visibility

### Categorical Data¶


## Preparation of data for model building

### Numerical and One-Hot Coding of Categorical Variables¶

### Standardisation of numerical data

### Separate train and test datasets 


## Models

## Baseline models
- Average sales
- Average Sales by Item_Type_Category
- Average Sales by Product_Type_Category in Particular Outlet_Type

## Feature selection with Recursive Feature Elimination and a RandomForestRegressor


## Regression models
- Standard Regression Model
- Ridge Regression Model
- Lasso Regression Model
- Decision Tree Model¶




##



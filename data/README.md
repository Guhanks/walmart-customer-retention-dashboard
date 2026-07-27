# Dataset Schema

Source files are a course-provided dataset (Internshala Trainings) and are not redistributed here due to licensing. Schema below for reproduction with your own data.

| Table | Rows | Fields |
|---|---|---|
| Customer_Demographics | 300 | Customer_ID, Age, Gender, Region, Income_Level, Membership_Since, Preferred_Channel |
| Customer_Transactions | 1,000 | Transaction_ID, Customer_ID, Store_ID, Product_Category, Amount, Promotion_Applied |
| Store_Locations | 50 | Store_ID, Store_Type, Region, Opening_Year |
| Loyalty_Program | 300 | Customer_ID, Loyalty_Tier, Points_Earned, Points_Redeemed |
| Churn_Labelled_Customers | 300 | Customer_ID, Last_Purchase_Date, Churn_Flag, Churn_Reason |

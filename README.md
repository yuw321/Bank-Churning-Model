# Bank-Churning-Model
This project studies the attrition pattern of bank customers based on their account information.

1.	Description of the data:
  -	The Dataset consists of 10127 observations in 21 variables.
  -	These observations consist of customer information about their demographic information.
  -	The seven education levels are: College, Doctorate, Graduate, High Scholl, Post-Graduate, uneducated, unknown.
  -	The six income ranges are: 120K+, 80K – 120K, 60K – 80K, 40K – 60K, Less than 40K, and unknown.
  -	Variable of interests are: Status of customer, is there an attrition with that specific customer?
    - To make prediction on their attrition status, discover the difference between the usage pattern between the existing customers and the attrited customers. To do so, looked at the numerical variables, and create dummy variables for categorical variables and binary variables to examine their importance in predicting the customer’s attrition status. 
-	 Summary statistics
  - Identifiers: CLIENTNUM
  -	Binary Variables: Attrition Flag, Gender, Martial Status,
  - Categorical variables: Educational Level, income category, card category.
2.	Proposed Questions to Investigate:
  - Question One:
    -  What are the factors that have the highest impact on a customer’s credit limit?
      - This question seeks to understand the underlying factors of a customer’s credit limit. 
      - Use best subset, forward selection, and backward selection methods to determine which variables are of the highest importance.
      -	Based on the subset selection methods, I found that the decision tree model of size six provided the best R-squared of 0.5998. The six variables selected are: Gender, Income_Category, Card_Category, Total_Revolving_Bal, Avg_Utilization_Ratio
      -	Based on the model, test the difference in credit limit for different responses.
        - Does male customers tend to have a higher credit limit?
          - The difference between male and female customers’ credit limit was only $55.10, which is rather trivial compared to the differences found in other vairables. 
        - Does customers with a higher revolving balance on their card have a larger credit limit?
          - The difference between high balance and low balance customers’ credit limit was $3574.01, which is a significant difference introduced by the gender variable. 
        - Does customers with a higher average utilization rate have a larger credit limit?
          - The difference between high balance and low balance customers’ credit limit was $6975.10. This is a rather surprising finding. Since customers with a higher balance will have a higher chance of default, it would make sense for the bank to give them lower credit limit. But the model shows that customers with a higher utilization tend to have a higher credit limit than a lower credit limit.
        - Note that income was also tested using the same methodology, and the difference between someone with a high income and a low income is $7446.84. However, this number is not surprising as higher income means the individual have more sizable transactions in their life compared to an individual with a lower income. 

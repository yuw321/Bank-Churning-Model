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
        - The difference between someone with a high income and a low income is $7446.84. However, this number is not surprising as higher income means the individual have more sizable transactions in their life compared to an individual with a lower income. 
  - Question 2
    - What credit card usage pattern does attrit customers exhibit?
      - This question seeks to test whether the mean of each numerical variable for attrited customers is statistically significantly different compared to the existing customers.
        - How does the mean value of each numerical variable differ for attrited customers compared to existing customers and what are their p-values?
          - Before investigating the difference in mean for each numerical variable, a binary variable was created for attrition. This binary variable enabled the feature selection model to find the variables with highest significance for predicting the customers’ attrition status. The six most relevant variables found using best subset, forward, and backward selection is consistent, they are: Total Relationship Count, Months Inactive 12 month, Contacts Count 12 month ,Total Revolving Balance, Total Trans Amt, Avg Utilization Ratio.
        - The following list of variables were studied using the same set of approach:
          - Use two-sample t-test to check if the difference between the variable of interest’s mean between the attrited customer and existing customer is statistically significant.
          - The hypothesis is that the mean is the same for the attrited customers and the existing customers. t.test() in R with a confidence level of 0.95 was used, with numerical variable of interest explained by the attrited variable. 
          - All of the two sample t-test yielded a p-value of 2.2e-16, the p-value shows that the null hypothesis has failed and that we can conclude the  mean between the two groups is different. 
          - Total_Relationship_Count 
            - The mean for existing customer is 3.912871, the attrited customer is 3.283333.
          - Months_Inactive_12_mon
            - The mean for existing customer is 2.269967, the attrited customer is 2.690278.
          - Contacts_Count_12_mon
            - The mean for existing customer is 2.358944, the attrited customer is 2.956944.
          - Total_Revolving_Bal
            - The mean for existing customer is 1263.0199, the attrited customer is 672.5625.
          - Total_Trans_Amt
            - The mean for existing customer is 4663.694, the attrited customer is 3132.556. 
          - Avg_Utilization_Ratio
            - The mean for existing customer is 0.3039046, the attrited customer is 0.1640479.
  - Question Three:
    - Can we predict which customer is going to attrit based on this data?
      - This question builds on the knowledge obtained from the dataset in the last two questions and tries find out the model with the best performance in terms of identifying the customers most likely to attrit. By picking out the model with the highest likelihood of identifying attrited customers, the bank will be able to have the opportunity to stop the attrition and retain those customers.
    - Using the best six variables we have discovered in the previous section, build logistic regression, decision tree and random forest models. Evaluate the performance of each model by looking at its accuracy, sensitivity, specificity.  
      - Discover the most important feature by evaluating the feature importance in random forest model.
        - Using importance() function in the random forest package, the list of most important variables is obtained from the random forest model. 
          - The finding is that total transaction amount on the account is the most important factor in terms of determining the customer’s attrition status. This means that the bank should reach out to a specific customer if their total transaction amount drops compared to the previous month, since it is the most important factor in terms of predicting attrition and very indicative of the customer’s tendency to attrit from the bank.



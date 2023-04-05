# Bank Customer Churn: Project Overview 
## Prediction of customer churn
### Our study has the following goals:
1. Identify and visually represent the factors that contribute to customer churn.
2. Develop a prediction model that can classify if a customer is likely to churn or not.
  * Ideally, choose a model that can also provide a probability of churn, making it easier for customer service to focus on preventing churn among customers with a higher likelihood of leaving.
  * Evaluate and select the most effective model based on its performance. So that customer service can efficiently target efforts to prevent churn.
  
There are questions that remain unanswered and require clarification:
  1. The data appears to be a snapshot at a specific point in time, with balances for a given date. What is the relevance of this date and can balances over a period of time be obtained instead of just a single date?

  2. Some customers have exited but still have a balance in their account. What does this mean? Could they have exited from a specific product or service but not the entire bank?

  3. What does it mean to be an "active" member, and are there different degrees of activity? Would it be more informative to provide transaction counts in terms of both credits and debits to the account?

  4. Providing a breakdown of the products bought by a customer could offer more information, such as a listing of product counts.

  For this project, I am proceeding without context, but it's important to have context and a better understanding of the data extraction process could potentially result in better and more contextual modeling outcomes.
  
## Exploratory Data Analysis (EDA)

Here our main interest is to get an understanding as to how the given attributes relate too the 'Exit' status.
  
  ![image](https://user-images.githubusercontent.com/110792339/229956041-d9b64fbd-636f-4ac1-852a-abae12f7ec70.png)

So about 20% of the customers have churned. So the baseline model could be to predict that 20% of the customers will churn. Given 20% is a small number, we need to ensure that the chosen model does predict with great accuracy this 20% as it is of interest to the bank to identify and keep this bunch as opposed to accurately predicting the customers that are retained.

![image](https://user-images.githubusercontent.com/110792339/229956454-55d36eaf-52fa-4746-8fd2-be60827e15a7.png)


We can observe the following trends in the data:
1. Although the majority of customers are from France, areas with fewer customers seem to have a higher proportion of churned customers. This suggests a potential issue with customer service resources in those areas.
2. Female customers have a higher churn rate compared to male customers.
3. Surprisingly, a significant portion of the churned customers have credit cards. However, since most customers have credit cards, this may be coincidental.
4. Inactive members show a higher churn rate. This is concerning as there is a notable proportion of inactive members overall. Implementing a program to convert inactive members into active customers could positively impact customer churn for the bank.

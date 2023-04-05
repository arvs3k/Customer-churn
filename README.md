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

![image](https://user-images.githubusercontent.com/110792339/229957003-b1283d57-7c37-403d-a99b-84cb92d83af6.png)

We can observe the following trends in the data:

1. There is no significant difference in the distribution of credit scores between retained and churned customers.
2. Older customers are more likely to churn compared to younger ones, indicating a potential difference in service preference among age groups. The bank may need to review their target market or retention strategy for different age categories.
3. Customers with extreme tenures (either very short or very long) are more likely to churn compared to those with average tenure.
4. The bank is losing customers with substantial bank balances, which may impact their available capital for lending.
5. Neither the product nor the salary has a significant effect on the likelihood to churn.

## Feature Engineering
We aim to include additional features that may influence the probability of customer churn. After splitting the data into train and test sets

![image](https://user-images.githubusercontent.com/110792339/229957473-be6123f1-79cb-4653-812d-36664f1ab69b.png)


We can observe that while salary alone has little effect on the likelihood of churn, the ratio of bank balance to estimated salary indicates that customers with a higher balance-to-salary ratio are more likely to churn. This could be concerning for the bank, as it may impact their source of loan capital.

## Model Fitting and Selection

I will experiment with the following techniques for model fitting:

1. Logistic regression in the primal space, using different kernels.
2. Support Vector Machines (SVM) in the primal space, also with different kernels.
3. Ensemble models, which may include methods such as bagging, boosting, or stacking

![image](https://user-images.githubusercontent.com/110792339/229957784-5b5051cc-2bb6-42e4-8e93-dafcf424bb23.png)

Based on the results obtained, my primary objective is to accurately predict customers who are likely to churn, so that appropriate measures can be implemented to prevent churn. The recall measure for the positive class (churned customers) is more important to me than the overall accuracy score of the model.

Given that only 20% of the data represents churned customers, achieving a recall higher than this baseline would already be an improvement. However, I aim to achieve the highest possible recall while maintaining a high precision, so that the bank can effectively allocate its resources towards customers identified by the model without wasting resources on false positives.

Upon reviewing the fitted models, it appears that the random forest model performs the best in terms of achieving a balance between recall and precision. With a precision score of 0.88 on the positive class (churned customers) based on the training set, the model correctly identifies 88% of customers predicted to churn, and with a recall score of 0.53 on the positive class, the model is able to highlight 53% of all actual churned customers.

## Conclusion
The precision of the model on the unseen test data is slightly higher when predicting the customers who churn (1's). However, despite the overall high accuracy of the model, it still misses around half of the customers who actually churn. To improve this, retraining the model with more data over time could be beneficial. In the meantime, working with the model could help save the 41% of customers who would have churned.

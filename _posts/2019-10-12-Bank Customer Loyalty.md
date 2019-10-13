---
layout: post
title: Bank Customer Loyalty
---


![bank image]({{ site.url }}/images/bank.jpeg)


![chart image]({{ site.url }}/images/chart.png)

From the above chart we can see there is about 20% of the bank customers leaving the bank and about 80% of them still customers of the bank. So, as part of the bank's marketing plan, these customers should be treated in a proper way to minimize bank exits. The objective of this project is to develop a churn model that predicts customers exits.


### About the Data

I got this data set from Kaggle you can find it from [here](https://www.kaggle.com/shrutimechlearn/churn-modelling). It contains details of a bank's customers and the target variable is a binary variable reflecting the fact whether the customer left the bank (closed his account) or he continues to be a customer.


**RowNumberRow** Numbers from 1 to 10000.

**CustomerIdUnique** Ids for bank customer identification.

**Surname** Customer's last name.

**CreditScore** Credit score of the customer.

**Geography** The country from which the customer belongs.

**Gender** Male or Female.

**Age** Age of the customer.

**Tenure** Number of years for which the customer has been with the bank.

**Balance** Bank balance of the customer.

**NumOfProducts** Number of bank products the customer is utilising.

**HasCrCard** Binary Flag for whether the customer holds a credit card with the bank or not.

**IsActiveMember** Binary Flag for whether the customer is an active member with the bank or not.

**EstimatedSalary** Estimated salary of the customer in Dollars.

> **Exited** Binary flag 1 if the customer closed account with bank and 0 if the customer is retained.

### Pre-processing

In this part I dropped unnecessary columns like RowNumberRow, CustomerIdUnique and Surname, Then I applied one hot encoding using```get_dummies``` for categorical data such as Gender and Geography.
After that I scale continous variables such as Balance, EstimatedSalary, CreditScore, Tenure and  NumOfProducts by using ```StandardScalar```.


### Baseline Model

I start modelling by the whole features and I used different models in order to see the least modelling performance. The next list presents each model with its accuracy:
1. Logistic Regression with Accuracy of (0.81).
2. KNN with Accuracy of (0.83).
3. SVM with Accuracy of (0.85).
4. Decision Tree with Accuracy of (0.78).
5. Random Forest with Accuracy of (0.87).
6. Naïve Bayes with Accuracy of (0.82).

From the besline Random Forest shows the best accuracy.

### Feature Engineering

After doing the baseline modeling I figure out that theres no big difference between train and test scores and my model is using my features to learn. However, the overall performance still not very good so I decided to improve the models performance by adding some interaction terms to see if it would affect the overall modeling performance and if it would help my models to learn more about my data.
So, I suggests 5 new features listed bellow:
* Tenure / Age
* Tenure * Blance
* Tenure ^2
* Salary ^2
* NumOfProducts ^2

After feeding them to the baseline model I find out a slight improving performance in logistic regression by 0.84 and Naïve Bayes by 0.83.

Next, I start tune my models using ``` GridSearchCV``` and play with hyperparameters.
and I end up with a slight improvment in performance for KNN by (0.85) and SVM by (0.86).

### Conclusion

From the results I end up with choosing Random Forest that has the highest accuracy, and least misclassification in the True negative which is our target (see the next figure). As my data suffers from class imbalance, I have to work on this issue and improve my model to predict misclassified data better.

![randomforest image]({{ site.url }}/images/rf.png)

So, for the future work I decided to resolve misclassification by trying to oversampling.




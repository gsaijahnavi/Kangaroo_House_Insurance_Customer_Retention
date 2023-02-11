# Kangaroo House Insurance Customer Retention
## Problem statement
Kangaroo - House Insurance American Company is concerned about the company’s retention rates and wants to know what is causing policy cancellation and retain existing customers. 
The aim of this project is to create a retention model to identify policies that will be renewed or canceled before the end of the term and understand what variables are most influential in causing a policy cancellation.

## Data Pre-processing
![image](https://user-images.githubusercontent.com/82319213/218241716-75b45f30-4c72-4d33-9d12-0ee99fc074ab.png)

## Feature engineering
![image](https://user-images.githubusercontent.com/82319213/218241741-b396186e-b664-4770-8cbc-4794c66005cc.png)



## Exploratory Data Analysis
### Influence of Sales Channel vs Churn
![image](https://user-images.githubusercontent.com/82319213/218241764-e31e9464-0054-4d70-acf4-b9f521810abf.png)

* If sales.channel is through “Broker”, it is seen that there is  a higher chance of continuing insurance than by other means.
* Phone, Online modes are showing higher incidents of not proceeding with the policy

### Credit vs cancel
![image](https://user-images.githubusercontent.com/82319213/218241785-55f2a616-2e1b-4158-8b53-038f5b2ddda9.png)

* A high credit scorer is most likely to continue the policy than others.
* There are higher chances of convincing the medium credit scorers from canceling the plan. 

### Coverage type vs cancel
![image](https://user-images.githubusercontent.com/82319213/218241806-f7430e59-211a-4f39-9cdf-b76e14752ada.png)
* Coverage A (covering damage to the house) holders are most likely to continue the policy than Coverage C (personal property) 

### Dwelling type vs cancel
![image](https://user-images.githubusercontent.com/82319213/218241832-38b38214-6e2f-4f9c-8d61-fe86f82fa688.png)
* Consumers with “House” dwelling.type are most likely to continue the House Insurance premium plan than the others. 

### Marital status vs cancel
![image](https://user-images.githubusercontent.com/82319213/218241848-50263f8b-6c76-4422-8de7-a558c3718761.png)

* Married policyholders are most likely to continue the policy than unmarried holders.


  


### Claim.ind vs cancel
![image](https://user-images.githubusercontent.com/82319213/218241876-d146f7f7-b6db-4a16-96cd-2d6452fcd483.png)
* Policy holders without claims are most likely to continue the policy.
### Zone vs cancel
![image](https://user-images.githubusercontent.com/82319213/218241905-20e679bd-b96d-4d7f-87ad-6d705de6d289.png)
* Zone-4 (Virginia) policyholders are mostly canceling policies.
* Policy holders from Arizona, Washington, and Iowa can be convinced from cancelling.


### Family size vs cancel
![image](https://user-images.githubusercontent.com/82319213/218241944-a1aaa33d-5e61-4c4d-94de-a5d8b66b39ac.png)
* Small family-size  <=5 are tending to continue the policy.
* Family-size of 6 to 9 can be convinced to continue the policy, whereas if the family size is >=9, they tend towards canceling their plan.

## Modeling
### Class Imbalance
![image](https://user-images.githubusercontent.com/82319213/218241964-a4841360-5c2b-4b87-b5bb-c0876ec51f40.png)

* Class imbalance is 70.9%, 7.2%, 21.9%
* Training-Val split is 80%-20%
* Oversampling algorithms like SMOTE are not showing improvement in predictions

### Evaluation metrics
* Precision is preferred over the False Positive rate for imbalanced data since the FPR can be misleading or uninformative as a number of 0s are more in the data.
* The focus is to improve the precision of 1’s and 2’s predictions.

### XGBoost
#### Accuracy
![image](https://user-images.githubusercontent.com/82319213/218242004-b483edaa-2f96-452e-93b0-9fb7341adf8b.png)

#### Gridsearch parameters
![image](https://user-images.githubusercontent.com/82319213/218242014-fdd837c1-8de0-460f-8206-66ed56f2736c.png)
#### Feature importance
![image](https://user-images.githubusercontent.com/82319213/218242023-35916c76-39de-48d3-aa98-fb418152fbfb.png)

* We are seeing high precision for classes 0 and 2, however, the recall on class-1 has dropped significantly which means there are a higher number of False negatives. This can be attributed to highly skewed data.

## Recommendations

### Suggestions to improve Zone - 4
* In Virginia (Zone-4) where cancellations are more, we are observing that most of the sales communication is made via Online and Phone.
* We can look to employing more in-person sales agents who might win customers in the company's favor of retention of customers
![image](https://user-images.githubusercontent.com/82319213/218242058-0e82b3d4-8072-4f7d-b18e-e4a466ffe2bc.png)

#### Implementation plan
![image](https://user-images.githubusercontent.com/82319213/218242080-ca84d7cd-34dd-4fff-b47b-5f1bd788351f.png)

### Targeting skeptical customers
* Families with three or more adults can be convinced to renew the plan, as most of them have a “High Credit Score”.
* There is no notable trend observed for cancelled and continuing customers.
![image](https://user-images.githubusercontent.com/82319213/218242107-b36bf8ba-4d1a-4b07-9a74-5a3c6994cdb7.png)


### Impact of sales.channel
![image](https://user-images.githubusercontent.com/82319213/218242344-26c8fc57-09a5-4263-b34e-20d3691eba5b.png)
* When the mode of communication is phone, most customers are unable to take a decision.
* For customers with low credit scores, they are also skeptical

### Implementation plan
CASE 1: Improving Website
	Giving some attractive offers to these customers and referral bonus might convince them to continue.
	
CASE 2: Hiring Sales Agents
	Assigning a group of sales agents to these customers might convince them to further continue.
  
  ![image](https://user-images.githubusercontent.com/82319213/218242141-d20e1156-abd5-428c-bca2-b424a6480005.png)

	
## Factors leading to policy cancellations [KPIs to track]
Credit Score
Sales. channel
Age of customer
Tenure remaining
Location
Claim history
Family Size












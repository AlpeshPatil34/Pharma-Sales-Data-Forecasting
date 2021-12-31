# Credit Card Fraud Detection
Credit card fraud is the unauthorized use of a credit or debit card, or similar payment tool (ACH, EFT, recurring charge, etc.), to fraudulently obtain money or property. Credit and debit card numbers can be stolen from unsecured websites or can be obtained in an identity theft scheme. Credit card fraud can be authorised, where the genuine customer themselves processes a payment to another account which is controlled by a criminal, or unauthorised, where the account holder does not provide authorisation for the payment to proceed and the transaction is carried out by a third party.

#### -- Project Status: [Completed]

## Project Intro/Objective
A predictive analysis of fraudulent activity in Credit Card transactions, this project uses multiple prediction models to compare the accuracies at which a particular transaction is considered to be fraudulent or not. This dataset presents transactions that occurred in two days, where we have 492 frauds out of 284,807 transactions. The dataset is highly skewed as the positive class(frauds), only account for 0.172% of all transactions.
It contains only numerical input variables which are the result of a PCA transformation. ![alt text](https://github.com/AlpeshPatil34/Credit-Card-Fraud-Detection/blob/master/images/Desktop%20Screenshot%202021.12.31%20-%2012.38.29.68.png)

### Methods Used
* Inferential Statistics
* Ensemble Learning
* Data Visualization
* Predictive Modeling

### Technologies
* Python
* Plotly, Seaborn, Matlplotlib
* Pandas, jupyter
* Catboost, AdaBoost, xgboost, Lightgbm, Random Forest


## Project Description
The data was obtained from a competition held on Kaggle.com.
The features V1, V2, ... V28 are the principal components obtained with PCA.
The only features which have not been transformed with PCA are Time and Amount. Feature Time contains the seconds elapsed between each transaction and the first transaction in the dataset. The feature Amount is the transaction Amount, this feature can be used for example-dependant cost-senstive learning
Feature "class" is the response variable and it takes value 1 in case of fraud and 0 otherwise.

(Provide more detailed overview of the project.  Talk a bit about your data sources and what questions and hypothesis you are exploring. What specific data analysis/visualization and modelling work are you using to solve the problem? What blockers and challenges are you facing?  Feel free to number or bullet point things here)
Post investigation of the data, relationships between different features were focused upon. ![alt text](https://github.com/AlpeshPatil34/Credit-Card-Fraud-Detection/blob/master/images/Correlation%20plot%20with%20Pearsons.jpg). 

The data was split in 3 parts, a train set, a validation set and a test set. For the first three models, we only used the train and test set.

Since no clear relationships were defined, singular one-on-one correlations were checked. Post that, 4 ensemble predictive models were employed to understand how well the predictions can be done, and on the basis of prerequiste parameters, AUC-ROC scores were calculated to quantifiy the comparisons of the same.

![alt text](https://github.com/AlpeshPatil34/Credit-Card-Fraud-Detection/blob/master/images/ROC%20Analysis.jpg)

We started with RandomForrestClassifier, for which we obtained an AUC scode of 0.85 when predicting the target for the test set.

We followed with an AdaBoostClassifier model, with lower AUC score (0.83) for prediction of the test set target values.

We then followed with an CatBoostClassifier, with the AUC score after training 500 iterations 0.86.

We then experimented with a XGBoost model. In this case, se used the validation set for validation of the training model. The best validation score obtained was 0.984. Then we used the model with the best training step, to predict target value from the test data; the AUC score obtained was 0.974.

![alt text](https://github.com/AlpeshPatil34/Credit-Card-Fraud-Detection/blob/master/images/lightgbm%20ROC.jpg)

We then presented the data to a LightGBM model. We used both train-validation split and cross-validation to evaluate the model effectiveness to predict 'Class' value, i.e. detecting if a transaction was fraudulent. With the first method we obtained values of AUC for the validation set around 0.974. For the test set, the score obtained was 0.946.
With the cross-validation, we obtained an AUC score for the test prediction of 0.93.

## Newer Applications - 
Considering the data was skewered, undersampling techniques should be employed to produce further tangible results which could hold up during live data phase.

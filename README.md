# Payment_Prediction_System

## Problem Statement

In the B2B world, businesses work with other businesses on credit. When a buyer business orderes goods from the seller business, the seller business issues an invoice for the same. In an ideal scenario, the buyer business would pay back the seller business and clear the invoice within a stipulated time. However, in the real world this is rarely the case and thus the Accounts Receivable department must keep track of the invoices generated. The following project is an AI enabled B2B Invoice Management System to be used by the Accounts Receivable department for better management of the invoices generated as well as to predict the clearance date of the invoice based on various factors. 

![image](https://user-images.githubusercontent.com/60508605/172109251-0ad4bdb1-b9e2-4968-9d28-262387b02581.png)

## Prerequisites

* Python 3.10.4
* Pandas
* Numpy
* Scikit-learn
* Seaborn
* Matplotlib

## Workflow

### Data Pre-Processing

Data preprocessing refers to manipulation or dropping of data before it is used in order to ensure enhanced performance. It involves the following:
* Loading the dataset
* Replace missing values in the dataset with null string
* Droping constants and duplicates
* Label encoding 
* Data type conversion

### Splitting the dataset
The dataset is split into train and test in a 60:40 ratio. The train dataset has no null data while the test dataset has only null data.

### Exploratory Data Analysis

* Distribution plot of the target variable 

![image](https://user-images.githubusercontent.com/60508605/172110318-cca14e69-7ef4-4f49-99eb-c6e55cadc67e.png)

![image](https://user-images.githubusercontent.com/60508605/172110348-8df9eb14-a90a-4fa5-add5-2f5d40cbb213.png)

* Grouping on 'business_year'

![image](https://user-images.githubusercontent.com/60508605/172110453-793eaf50-0e9a-407e-ab1f-20eda0e6ff86.png)

![image](https://user-images.githubusercontent.com/60508605/172110481-dbe096b3-d144-4b51-8ab2-b6419630a290.png)

### Feature Extraction
Text data is transformed into feature vectors that can be used as input for the model. Y_train and Y_test values are converted to integers.

![image](https://user-images.githubusercontent.com/60508605/172110852-c879304d-2095-47f6-a023-26ec35f38e05.png)
![image](https://user-images.githubusercontent.com/60508605/172110902-6c7092e1-47db-4b82-96be-2730990aa960.png)

### Modelling
The machine learning models used are:
* Linear Regression
* Support Vector Regression
* Decision Tree Regression
* Random Forest Regression
* XGBoost (Extreme Gradient Boosting Regression)

XGBoost is the best performing model. It makes use of a gradient descent algorithm where the whole idea is to correct the previous mistake done by the model, learn from it and its next step improves the performance. The previous results are rectified and performance is enhanced. It is fast to execute and gives good accuracy as shown in the comparisons above where compared to Linear Regression, Support Vector Regression, Decision Tree Regression and Random Forest Regression, XGB Regressor performed the best with the highest R2 Score.

The nulldata dataframe is passed through the XGBoost Model and the predicted payment date is grouped into aging buckets. The different buckets are:
* 0-15 days
* 16-30 days
* 31-45 days
* 46-60 days
* Greater than 60 days

The new column aging_buckets is created and the results are stores in a different csv file. 

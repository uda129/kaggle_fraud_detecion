# kaggle_fraud_detecion
IEEE-CIS Fraud Detection (Can you detect fraud from customer transactions?)

# Observation
    
## 1. Data Imbalance
training data: 569877(96.5%) v.s. 20663(3.5%)


#### =====(To overcome data imbalance...)=====

#### 1.1 Try to balance the data:

##### (Over sampling)

1. simple over sampling 
2. SMOTE

##### (under sampling)
1. simple under sampling
2. Tomek links

#### 1.2 Transfer learning for few label data
#### ====================================

## 2. Large class in category features

total 49 category features in this challenge

- 26 category features class<=10

- 23 category features class>10 

number of class, from 3 to 13553


##### - if class>10, one hot encoding may suffer from dimension explode
##### - choose other encoding methods if (class>10 and dis-order features)

============================

有序資料可以直接label encoding

無序資料通常做one hot encoding (ex. xgboost, 例外: LGBM餵label encoding即可)

============================

## 3. Plenty of NaN data
Around 180 features get over 50% NaN datas 

- drop NaN
- fill nan with mean, 0, ...
- Interpolate


## 4. Others
(weak) The fraud transaction of most fraud identities < 2, that is to say, most user may not fraud in the same device/place. (if the features in Identity.csv is independent with times)(if not considering NaN)

============================
============================

# To do to improve model performance

### 1. Deal with data imbalancing 
origin data

[current] simple upsampling fraud data

SMOTE

### 2. Change cross-validaiton method (for time series data)

basic cv

[current] time series cv

### 3. Optimize PR curve instead of ROC (PR is a better choice for data imbalance task)

============================
============================

# Feedback of this project

### 1. Important features:
1. card1
2. card2
3. TransactionID
4. TransactionAmt
5. addr1

### 2. Interesting discovery:
1. famous email domain get higher fraud probability. ex. 'gmail.com' 'hotmail.com' 'outlook.com'
2. famous device get higher fraud probability. ex. 'Windows' 'iOS Device'
3. fraud probability highly related to time (TransactionID)

### 3. prediction
- card1(10000-15000) and card2(100-300): higher probability to be fraud


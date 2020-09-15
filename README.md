# kaggle_fraud_detecion
IEEE-CIS Fraud Detection (Can you detect fraud from customer transactions?)

# 1. Observation

## Data Imbalance
training data: 569877(96.5%) v.s. 20663(3.5%)

### Try to balance the data:
(Over sampling)
simple over sampling
SMOTE
(under sampling)
simple under sampling
Tomek links
### Transfer learning for rare label data

## large class in category features
26 category features class<=10, 23 category features class>10 (number of class, from 3 to 13553)

(if class>10, one hot encoding may suffer from dimension explode
choose other encoding methods if class>10 and dis-order features)
有序資料可以直接label encoding

無序資料通常做one hot encoding (ex. xgboost, 例外: LGBM餵label encoding即可)

## plenty of NaN data
Around 180 features get over 50% NaN datas

## others
(weak) The fraud transaction of most fraud identities < 2, that is to say, most user may not fraud in the same device/place. (if the features in Identity.csv is independent with times)(if not considering NaN)

# 2. To do to improve model performance

## deal with data imbalancing (performance variance in current work, 80-90%)
origin data

(current) simple upsampling fraud data

SMOTE

## change cross-validaiton method (for time series data)
basic cv

(current) time series cv

## optimize PR curve instead of ROC (PR is a better choice for data imbalance task)

# 3. Feedback of this project

## important features:
card1
card2
TransactionID
TransactionAmt
addr1
## interested discovery:
famous email domain get higher fraud probability. ex. 'gmail.com' 'hotmail.com' 'outlook.com'
famous device get higher fraud probability. ex. 'Windows' 'iOS Device'

# Table of contents
- [Objective](#objective)
- [Project overview](#project-overview)
- [Dataset](#dataset)
- [Libraries used](#libraries-used)
- [Exploratory data analysis overview](#exploratory-data-analysis-overview)
- [Y preprocessing](#y-preprocessing)
- [X feature engineering](#x-feature-engineering)
- [Machine learning models overview](#machine-learning-models-overview)
- [Machine learning models metrics](#machine-learning-models-metrics)

<div id="objective"></div>

## Objective

To predict the range of the app installs in Google PlayStore

<div id="project-overview"></div>

## Project overview

` apps-EDA-ML-journey.pptx ` contains the summarized version of the exploratory data analysis (EDA) and machine learning (ML) evaluation while the full version and source code is located in ` apps-EDA-ML.ipynb`

<div id="dataset"></div>

## Dataset

Google Play app dataset can be retrieved using one of the links below:
* https://drive.google.com/file/d/1m7KKo_izuhFFTJnmgvOnxmNCnbjn302n/view?usp=sharing
* https://www.kaggle.com/gauthamp10/google-playstore-apps

<div id="libraries-used"></div>

## Libraries used

Please have the following Python libraries installed to run the Jupyter Notebook
* pandas
* numpy
* seaborn
* category_encoders
* xgboost
* sklearn
* matplotlib

<div id="exploratory-data-analysis-overview"></div>

## Exploratory data analysis overview

Perform exploratory data analysis (EDA) on Google Playstore apps to find out what kind of apps can fetch more user installs.  
Six different insights were obtained from doing the EDA. They are:
* Correlation, if any
* Rating vs Installs
* Rating count vs Installs
* Top ten categories
* Top ten categories with most installs
* Distribution of installs

Correlation matrix, boxplot, countplot, barplot, distplot are used to illustrate the findings and insights.

<div id="y-preprocessing"></div>

## Y Preprocessing

Quantile binning is used on Y to separate installs into four different classes of installs.  
Each class can represent four stages or phases of app development.

The **four different classes** are:
* 0 -> 0 to 100 installs
* 1 -> 101 to 1000 installs
* 2 -> 1001 to 10,000 installs
* 3 -> 10,001 to 10,000,000,000

<div id="x-feature-engineering"></div>

## X feature engineering

Below shows the raw features that are selected from the dataset, which then undergo a process or processes to get encoded before they can be be fitted into the machine learning algorithm:

Raw features | Method | Derived features | Columns used
-------------|--------|------------------|-------------
Category | Binary encoding | Encoded category | 6
Free | Dummy encoding | Encoded free | 1
Ad supported | Dummy encoding | Encoded free | 1
In app purchases | Dummy encoding | Encoded free | 1
Editor's choice | Dummy encoding | Encoded free | 1
Rating | Custom quantile encoding & Robust scaler | Encoded rating | 1
Rating count | Custom quantile encoding & Robust scaler | Encoded rating count | 1
Content rating | Custom ordinal encoding | Encoded content rating | 1
Minimum android | Custom extraction | Encoded minimum android | 1
Release date | Custom extraction & Robust Scaler| Encoded released year, released month, released date, released weekend | 4
Updated date | Custom extraction & Robust Scaler | Encoded released last update difference | 1
Developer ID | Derive frequency & Quantile Binning | Encoded developer id count | 1

<div id="machine-learning-models-overview"></div>

## Machine learning models overview

These are the list of models and the parameters that were applied to predict the app range installs.
The parameters were being tested in a few rounds and the final chosen parameter might differ from this list

Model name | Parameters applied
-----------|-------------------
Logistic regression | multi_class='multinomial', solver='newton-cg', C = 166.81005372000593, random_state=13, class_weight= y_installs_weights['weights']
KNN | n_neighbors = 5, p = 2, weights = 'distance'
Decision tree | criterion = 'entropy', max_depth = 5, class_weight=y_installs_weights['weights']
Random forest | n_estimators = 100, criterion = 'entropy', random_state = 555, class_weight = y_installs_weights['weights']
Gradient boosting | n_estimators= 100 , learning_rate= 0.1 ,max_depth= 10, random_state=12
XGBoost | objective='multi:softmax', random_state =42, max_depth=6, gamma=1.0, learning_rate=0.1

<div id="machine-learning-models-metrics"></div>

## Machine learning models metrics

These are the **three** metrics that are used on the machine learning models to evaluate their performance.  
The table below shows the metrics as well as the reasons for using them.

Metric | Reason
-------|-------
F1 score | seek balance between ` precision ` and ` recall ` due to uneven class distribution
ROC AUC ovo | represents the ` degree or measure of separability` and tells how much the model is capable of distinguishing between multi classes
Logloss | to compare between different models especially when the other scores are very similar

# Table of contents
- [Objective](#objective)
- [Libraries used](#libraries-used)
- [Exploratory data analysis overview](#exploratory-data-analysis-overview)
- [Y preprocessing](#y-preprocessing)
- [Dataset](#dataset)

<div id="objective"></div>

## Objective

To predict the range of the app installs in Google PlayStore

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

Six different insights were obtained from doing the exploratory data analysis. They are:
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

<div id="dataset"></div>

## Dataset

Google Play app dataset can be retrieved using one of the links below:
* https://drive.google.com/file/d/1m7KKo_izuhFFTJnmgvOnxmNCnbjn302n/view?usp=sharing
* https://www.kaggle.com/gauthamp10/google-playstore-apps


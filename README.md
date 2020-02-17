# Sentimental-Analysis-of-Amazon-Fine-Food-Review

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/0_c7wMiVrApomEnqcl.png>


## Objective:
Given a review, determine whether the review is positive (Rating of 4 or 5) or negative (rating of 1 or 2).

<br>
[Q] How to determine if a review is positive or negative?<br>
<br> 
[Ans] We could use the Score/Rating. A rating of 4 or 5 could be cosnidered a positive review. A review of 1 or 2 could be considered negative. A review of 3 is nuetral and ignored. This is an approximate and proxy way of determining the polarity (positivity/negativity) of a review.

## [1] Data Cleaning: 

It is observed (as shown in the table below) that the reviews data had many duplicate entries. Hence it was necessary to remove duplicates in order to get unbiased results for the analysis of the data.Also we are sorting the data wit respect to time here 

## [2].  Text Preprocessing:

Now that we have finished deduplication our data requires some preprocessing before we go on further with analysis and making the prediction model.

Hence in the Preprocessing phase we do the following in the order below:-

1. Begin by removing the html tags
2. Remove any punctuations or limited set of special characters like , or . or # etc.
3. Check if the word is made up of english letters and is not alpha-numeric
4. Check to see if the length of the word is greater than 2 (as it was researched that there is no adjective in 2-letters)
5. Convert the word to lowercase
6. Remove Stopwords
7. Finally Snowball Stemming the word (it was obsereved to be better than Porter Stemming)<br>

## [3]. Text Featurization:
for featurizing the text data we have used following 4 techniques:
  - CountVectorizer(Bag of Words)
  - TFIDF
  - Average Weighted Word2Vec(Using pre trained glove model)
  - TFIDF Weighted Word2Vecw(using pre trained glove model)
  
  ## Applying TSNE 
  * TSNE helped in visualizing large dimensions data in 2 dimenions thus indicating somewhat how data is distributed
* Different values of perplexity and running TSNE for higher number of iterations shows better solution finding in each iteration.also it expands dense clusters and shrinks sparse clusters

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/tsne_bow.PNG>

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/tsne_tfidf.PNG>

## ML Supervised Models:Used following Supervised learning models to prdict thee polarity

- __KNN__: Used both kd-tree and brute force appraoch 

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/KNN_results.PNG>

- __Naive Bayes__: Used Multinomial Naive Bayes ,curated new feature 'length of the reviews' after preprocessing and used 10 fold cross validation for hyperparameter tuning.

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/Naive_bayes_results.PNG>

- __Logistic Regression__: Used both L1 and L2 regularization to avoid overfitting of data and performed hyperparameter tuning using GridsearchCV.

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/lr.PNG>

- __Decision Trees__: Used decision trees,performed hhyperparameter tuning of 'min_samples_split' and 'max_depth' using GridSearchCV

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/dt_results.PNG>

- __Random Forest__:Performed hyperparameter tuning of 'max_depth' and 'no_of_estimators' using RandomSearchCV 

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/rf_results.PNG>

- __XGBoostClassifier__:Performed hyperparameter tuning of 'max_depth' and 'no_of_estimators' using RandomSearchCV 

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/xgb_results.PNG>

- __SVM using Linear kenel__:SGDClassifier with hinge loss,performed hyperparameter tuning using GridSearchCV and used CalibratedClassifier for better estmation of the predicted values.

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/svm_linear.PNG width = 1000>

- __SVM using RBF kkernel__:Support Vector Classifier with rbf kernel,performed hyperparameter tuning using GridSearchCV and used CalibratedClassifier for better estimation of the predicted values.

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/svm_rbf.PNG>

## ML Unsupervised Models:Used following Unsupervised learning methods to cluster the reviews.

- __KMeans Clustering__:Used Kmeans after the featurization and found best 'k' using elbow-knee method(plot k vs inertia_) and then plotted the 'k' wordclouds for 'k' clusters.

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/Kmeans.PNG>

- __Agglomerative Clustering__:Used Agglomerative clustering on AvgW2V and TFIDFW2v,chose optimal number of clusters by plotting dendograms.

<img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/agglomerative.PNG>

_ __DBSCAN Clustering__:found the nearest neighbors with min_points and then using elbow method to determine the eps using the elbow method,the point of inflection was eps
 
 <img src = https://github.com/yatscool007/Sentimental-Analysis-of-Amazon-Fine-Food-Reviews/blob/master/Images/dbscan.PNG>



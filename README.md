# NLP

This ipynb contains an implementation and results for the Natural Langauge Processing project.

The Problem Statement here consists of the classifying the YELP dataset reviews with respect to the 1 star reviews and 5 star reviews.

The dataset can be found on : YELP Review Data Set from Kaggle- https://www.kaggle.com/c/yelp-recsys-2013

Each observation in this dataset is a review of a particular business by a particular user.

The "stars" column is the number of stars (1 through 5) assigned by the reviewer to the business. (Higher stars is better.) In other words, it is the rating of the business by the person who wrote the review.

The "cool" column is the number of "cool" votes this review received from other Yelp users. 

All reviews start with 0 "cool" votes, and there is no limit to how many "cool" votes a review can receive. In other words, it is a rating of the review itself, not a rating of the business.

The "useful" and "funny" columns are similar to the "cool" column.!

Steps for Execution:

1. Extracted the data and gathered more info about the same.
2. As we are classifying the reviews for the 1 star and 5 stars so looked at the normal text length of the reviews and created a separate feture for it.
3. Performed Exploratory Data Analysis on those columns and the got to know the reltionship fo the features cool,funny,useful and text_length.
4. Checked their correlation with each other andplotted a heatmap for the same.
5. Sorted out only the 1 star and 5 star reviews now as we are only going to deal with those.
6. Now classified the 'text' i.e message as X feature and y i.e. 'stars' as the y feature.
7. Used CountVectorizer for feature extraction and fitted it to the X feature.
8. Splited the data to train and test and trained the Multinomial Naive Bayes modelm made predictions and evaluated the model.
9. The model is good, but checking the model after Text Processing with TfidfTransformer.
10. Defined a specific pipeline with Bag of words, TfidfTransformer and the classifer model.
11. Trained the model made predictions and then evaluated the results and it actually made the model worse.
12. So further removed the TfidfTransformer and checked how the Random Forest Classifier behaves. 
13. Followed the same pipeline and the accuracy reported was not 86% Not Bad!!
14. Now lets go back to the Logistic Regression model and then evaluate the perfromance of the model on the dataset.
15. After evaluation it reported the same accuracy as that of the Random Forest Classifier.
16. The model is now ready and its upto us which one to choose !!!!!! 


Results :

1. TfidfTransformer and Multinomial Naive Bayes:

**Classification Report:

              precision    recall  f1-score   support

           1       0.00      0.00      0.00       228
           5       0.81      1.00      0.90       998

    accuracy                           0.81      1226
   macro avg       0.41      0.50      0.45      1226
weighted avg       0.66      0.81      0.73      1226

**Confusion Matrix:

[[  0 228]
 [  0 998]]

2. Removing TfidfTransformer and using RandomForestClassifier:

              precision    recall  f1-score   support

           1       0.95      0.23      0.37       228
           5       0.85      1.00      0.92       998

    accuracy                           0.85      1226
   macro avg       0.90      0.61      0.64      1226
weighted avg       0.87      0.85      0.82      1226



[[ 52 176]
 [  3 995]]

3. Removing TfidfTransformer and using basic LogisticRegressor:

Classification Report:

              precision    recall  f1-score   support

           1       0.95      0.23      0.37       228
           5       0.85      1.00      0.92       998

    accuracy                           0.85      1226
   macro avg       0.90      0.61      0.64      1226
weighted avg       0.87      0.85      0.82      1226

Confusion Report:

[[ 52 176]
 [  3 995]]


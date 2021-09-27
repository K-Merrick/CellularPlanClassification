# CellularPlanClassification
We've been tasked with developing a machine learning model that would analyse subscribers' behavior and recommend one of Megaline's newer plans for each user - that is, the Smart or Ultra plan. We have access to monthly data on the number of calls each user has made, the total duration of calls made, the number of messages they sent, how much data they used in Megabytes, and whether they are currently on a Smart or Ultra plan. Given that the desired outcome of the machine learning model is to separate users into two categories (i.e., ultra or not-ultra), this is a classification task. We have been asked to generate a classification model with an accuracy of above .75. 

**Conclusion**: For this project our task was to train a machine learning model to classify Megaline users based on whether they are on a Smart plan or Ultra plan with an accuracy of greater than .75. In carrying out this task, we separated data into training, validation, and testing datasets, and trained various logistic regression, decision tree, and random forest models while iterating through several key hyperparameters. Based on the accuracy scores for the models on the validation dataset, we found that the random forest model with a depth of 24 and 16 estimators was was the most accurate model. This held true when running the test dataset throught he model; however, the accuracy score for the model on the test dataset was slightly lower.

We then performed a sanity check in order to determine whether the model's accuracy score on the test dataset was misleading. We hypothesized, in light of the high variance of data for Ultra users, the overlap of values for features for users on each plan, and the over-representation of data for Smart users in the original dataset, that the model would be less accurate at carrying out the classification task if the users of both plans were equally represented in the dataset. To test this, we randomly selected 500 rows of data for users of each plan from the user_df DataFrame, trained a random tree model using this dataset and with the hyperparameters tuned to the same values as with out test model, and obtained the accuracy score. It turns out our hypothesis was correct, as the model was less accurate at classifying users according to their plan when users of each plan were equally represented in the dataset.

Overall, while our accuracy score for the random forest model on the test data was quite high (and above the required accuracy, as stated by Megaline), we believe that the over-representation of Smart users in the dataset and overlap of feature values for user of each plan caused the model to erroneously classify more users as having the Smart plan than Ultra plan. As such, we would recommend the following:

1) Collect more data for the model: As was stated in the details of this project, Megaline's Ultra and Smart plans are new. Depending on how new the plans are, it is likely that many users on the Ultra plans have not become accumstomed to the allowances they have. We would recommend that Megaline continue to collect more data on individuals using each plan and retrain the random forest model using this new data.

2) Balance the datasets: As was mentioned, there are approximately 3 times more Smart users represented in the dataset than Ultra users. We believe that by ensuring users of each plan are equally represented in the dataset, our model's accuracy score will more accurately reflect its ability to properly classify individuals on each plan.

3) Add additional features to the dataset: We believe that more information could be added to the dataset to make the model more efficient. In our previous Megaline project, we calculated the extent to which individuals on each plan went above their allwances. We consider this information to be highly valuable, as we found that users on the plan with a lower allowance went over their limit more often and to a greater extent than users on the other plan. We believe that our model's accuracy score would be increased with this key piece of data.

## Approach

The competition was based on an imbalanced binary classification problem with AUCROC metric.
I created several features based on textual information and user behaviour to arrive at my final solution
The features created were:
1) Target encoding of user_id with respect to is_open and is_click
2) Target encoding of campaign_id with respect to is_open and is_click
3) Target encoding of communication_type with respect to is_open and is_click
4) Length of email body (word wise)
5) Length of subject
6) Key feature : I pre-processed the text in the subject by removing stop words, lemmatizing them, removing punctuations etc. After that I used a bag of words (unigram) representation of different
		 campaign_ids based on their subject. This was followed by merging this dataset with campaing_ids present in the train and test data. After this merge operation. I used groupby sum based on user_id to obtain a unique representation for every user. This was followed by PCA to reduce the dimensions to 50. This operation added the biggest jump to my score.
7) Number of mails received by different users
8) Cross tab of user_id vs communication type
9) Numerical features present in the campaign_data

This became my general frame work for data preparation before feeding it into any model. An xgboost model with these set of features gave me score of 0.695+ on the public leaderboard. What followed after this was sheer pragmatism. I created several models based on approximately the same frame work and differentiated them by adding variability. Some of the important variations were:
1) Using bi-grams for BOW representation
2) Using tri-grams for BOW representation
3) Using all three of them
4) Using tf-idf with same (unigram,bi-gram,tri-gram)
5) Using lightboost, xgboost and catboost on each of the three representations above
6) Using truncated SVD instead of PCA for dimension reduction
7) I even dropped the best performing feature and tuned the hyper-parameters in such a way to arrive at similar scores using remaining features
8) Target encoding of weekday of sent mail
9) Cosine distance among the Glove vector representations of differnt campaign ids.

These are just some of them. I created many notebooks and added/dropped/modified many features and performed many experiments, which most of the time gave me a public lb score around the vicinity of (0.685 - 0.69). Even though the perfomance of all the models were similar, there predictions were not highly correlated. This gave me the opportunity to take advantage of weighted ensembles to arrive at a higher score. I took the most similar scoring prediction files with the least correlation and took their weighted average. I continued this process in an uphill fashion. I ended up with four best performing predictions with scores (0.699 - 0.7011). I again followed the same hueristic to arrive at my final score which gave me a public leader board score of 0.704. This entire process is very similar to model stacking where diverse base classifiers prediction is fed to a meta classifier to arrive at better predictions. Only in my case, it was me manually adjusting the weights assigned to different models by validating them against the public leader board.  

## How to run the code?
The order of running code files are:

1) LOM2 - (for generating encodings of user id and campaign id using target encoding)
2) LOM-text_features - (for generating features based on text)
3) Features based on len of text
4) LOM_1_model & LOM_model_2 - (both are used for generation of final submissions)
5) LOM_final

PLease take note that I created many many solutions using different features, sometimes different hyper-parameters, and even different algorithms. As for final solution, I took their weighted ensemble (weights decided against public leaderboard).

The LOM_1_model and LOM_model_2 are my top two single performing models. However the best solution is a combination of different predictions. The files in the ensemble folder contain these different predictions (Kindly change the path accordingly in LOM_final notebook)

Some variations that I used for arriving at these predictions are:
1) Using bi-gram text_features
2) Increasing the dimension parameter in PCA
3) Using a mixture of bi-gram & tri-gram
4) Using a mixture of catboost and lightboost algorithm on uni-gram features
5) Averaging predictions over different xgboost depths.
6) Using tf-idf vectors instead of bag of words

Finally, it was a great competition with lots of learning and excitement. 
Thank you team AV for organizing this contest.


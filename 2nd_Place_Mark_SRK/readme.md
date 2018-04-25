## Approach
Most of our time is spent on creating new features. We did validation split based on campaign ids. Our best single model is a light GBM that scored 0.7051 in LB. List of important features we used are:

1. Target encoding on the user ID, user ID - communication type
2. Min, max, mean and standard deviation of the mail sent time.
3. One hot encoding of the campaigns.
4. Time between current mail and previous mail
5. Number of campaigns inbetween current mail and previous mail
6. Total number of mail campaigns per user ID
7. Cumulative count of the mail at user level
8. Hour of the mail

## How to run the code?
Order of files to run
1. Explorations.ipynb - Code file to create the features.
2. build_model.py - Code file to build the Light GBM model
3. build_model_xgb.py - Code file to build the XGB model
4. ensemble.py - Code file to merge both the results.

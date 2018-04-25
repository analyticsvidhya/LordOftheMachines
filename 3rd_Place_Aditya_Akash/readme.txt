Packages used for executing Aditya's model
==========================================
Python Python 3.6.4, Dependencies
===========================================
lightgbm                  2.1.0  
scikit-learn              0.19.1   
pandas                    0.22.0  
numpy                     1.14.0  
xgboost			  0.7

Execution of Aditya's model
============================
Execute following notebooks
Note: train.csv and test.csv should be present in folder name "input". Output files will be genrated at current path
1. user_cluster-kmeans.ipynb, this will generate file user_cluster1.csv in input folder
2. xgb_2fold-cv3_bag3_nt70_scalepos1_best_tree.ipynb, this will generate test prediction file name "xgb_2fold-cv2_bag3_nt70_scalepos1_nt70.csv".
3. lgb_5fold-5_bag_nt45_rank_average_AND_lgb_5fold-5_bag_nt45_rank_average_4f.ipynb, this will generate test prediction file names "lgb_5fold-5_bag_nt45_rank_average.csv" and "lgb_5fold-5_bag_nt45_rank_average_4f.csv".
4. lgb_5fold-5_bag_nt55_rank_average_5f_AND_lgb_5fold-5_bag_nt55_rank_average_4f.ipynb, this will generate test prediction file names "lgb_5fold-5_bag_nt55_rank_average_5f.csv" and "lgb_5fold-5_bag_nt55_rank_average_4f.csv".
5. lgb_new_features-v6-5fold_5bag_cv_retry_lb_692_ens6941-submitted, this will generate lgb_5fold-5_bag_nt55_rank_average.csv.


Packages used for executing Akash's model
==========================================
Python Package Dependencies
===========================================

Keras			  2.0.8
sklearn			  0.19.0
pandas                    0.20.3
numpy			  1.14.2
matplotlib                2.2.2

Instructions:


Execution of Akash's model
============================
Execute each cell in following notebooks
1. cnn.ipynb, it will generate test prediction file submission_cnn.csv
2. lstm.ipynb, it will generate test prediction file submission_lstm.csv
3. lstm_cnn.ipynb, it will generate test prediction file submission_lstmcnn.csv

All train, test, and submission files should be kept in current path of notebook.

Ensemble Model
=========================
Execute final_ensemble-simple_avg.ipynb python notebook, that will rank average all the models output into final submssion.
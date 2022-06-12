# Module 12 Report by Raj Tolani

## Overview of the Analysis


* The goal of this excercise is to produce a tool to evaluate loan applications and classify them has 'Good Loans" or 'High Risk Loans"

* The Loan application requires borrowers to provide the following information
      Loan Amount
      Interest Rate
      Borrower Income
      Number of existing loans and amounts
     
* The software developed uses data of existing 77,536 loans which had been classified as 0 "Good Loans" or 1 "High Risk Loans' based on historical performance. This data is used to train the model. The iniital part of the this application is using the Data as is to develop a prediction Model. The steps taken to develop the prediction tool are
      Split the data into Learn and Test Groups. This is done using the train_test_split function
      Use the train data to develop the model
      Use the predict methd to predict the clasification based on the parameters of the test set
      Compare the Predicted values to the known values of loan_status for the test data. Use the following to evaluate the performance of the model
              balanced_accuracy_score
              confusion_matrix
              classification_report_imbalanced
* The results section of this document discusses the results found for using the data as is. Also to evaluate this model we ran value_counts method on the loan_status for historical data provided. It showed that there were 75,306 good loans compared to 2500 Risky Loans. A model based on this data could potential skew the results. To compensate for that additional data was created using oversampling for high risk loan. The resulting data was used to create another prediction models by repeating the steps above. Then both the models were compared. The results and comparision are discussed below


## Results
 Results based on the learning subset original Data Provided : A regression model was created and fitted using the learn subset of the orignal data. Then this model was used to predict the loan_status for the loans in the test subsection of the data. The predicted values were compared with the known values for these looans. The following metrics were used to validate the performance of this prediction model
      balanced_accuracy_score : 0.952
      confusion_matrix        
                    18663,   102],
                  [   56,   563]
                  To me the most disturbing part of this matrix shows that 56 loans which turned out to be high risk loans were predicted as good loans. This reduces the quality of this model 
      classification_report_imbalanced : This reports shows 1.0 precision and reacll of 0.99 for good loans prediction. This is satisfactory. For high risk loans it shows precision of 0.85 and recall of 0.91. These numbers are less than desireable and like the confusion matrix are indicating that this model will allow high risk loans to slip through as good loans

      
* Results based on the Oversampling Data ; A regression model was created and fitted using the oversampled dataset.Then this model was used to predict the loan_status for the loans in the test subsection of the data. The predicted values were compared with the known values for these loans. The following metrics were used to validate the performance of this prediction model
      balanced_accuracy_score :0.994
      Confusion_matrix : 
                  [18649,   116],
                  [    4,   615]
                  This matrix looks much better. Only 4 high risk loans are incorrectly predicted to be good loans.
      classification_report_imbalanced :This reports shows 1.0 precision and reacll of 0.99 for good loans prediction. For high Risk loans it shows precision of 0.84 and recall of 0.99. The improved recall score makes it a much better model than the original

 

## Summary

My conclusion after reviewing the results is that it would be much better to use the Oversampled model. It improves the predictions for 1 or the high risk loans. Misclassifying the high risk loans as good loans would result in financial losses if and when the high risk loans default. Better prediction of high risk loans is very important



# Event-classification-for-payment-card-fraud-detection

## Introduction
Payment fraud detection is critical for banks, businesses, and consumers. In Europe alone, fraudulent transactions were estimated at €1.89 billion in 2019. Worldwide, approximately 3.6% of commerce revenue is lost to fraud. In this notebook, we train and evaluate a model to detect fraudulent transactions using the synthetic dataset attached to the book Reproducible Machine Learning for Credit Card Fraud Detection by Le Borgne et al. To express these relationships in a way that is understandable by a machine learning model, and to augment features with feature engineering, we We use the Temporian preprocessing library.  
We preprocess a transaction dataset into a tabular dataset and use a feed-forward neural network to learn the patterns of fraud and make predictions.

### Loading the dataset
The dataset contains payment transactions sampled between April 1, 2018 and September 30, 2018. The transactions are stored in CSV files, one for each day. It will take approximately one minutes to download.

### Dataset Representation
Each transaction is represented by a single row, with the following columns of interest:

* TX_DATETIME: The date and time of the transaction.
* CUSTOMER_ID: The unique identifier of the customer.
* TERMINAL_ID: The identifier of the terminal where the transaction was made.
* TX_AMOUNT: The amount of the transaction.
* TX_FRAUD: Whether the transaction is fraudulent (1) or not (0).

### Preparing the training data
Fraudulent transactions in isolation cannot be detected. Instead, we need to connect related transactions. For each transaction, we compute the sum and count of transactions for the same terminal in the last n days. Because we don't know the correct value for n, we use multiple values for n and compute a set of features for each of them.

### Split the dataset into a train, validation and test 
To evaluate the quality of our machine learning model, we need training, validation and test sets. Since the system is dynamic (new fraud patterns are being created all the time), the training set needs to come before the validation set, and the validation set come before the testing set.

Training: April 8, 2018 to July 31, 2018
Validation: August 1, 2018 to August 31, 2018
Testing: September 1, 2018 to September 30, 2018

### Train the model
The original dataset is transactional, but the processed data is tabular and only contains normalized numerical values. Therefore, we train a feed-forward neural network.Our goal is to differentiate between fraudulent and legitimate transactions, so we use a binary classification objective. Because the dataset is imbalanced, accuracy is not an informative metric. Instead, we evaluate the model using the area under the curve (AUC).

### Conclusion
We trained a feed-forward neural network to identify fraudulent transactions. To feed them into the model, the transactions were preprocessed and transformed into a tabular dataset using Temporian. 

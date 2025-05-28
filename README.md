# credit-card-fraud-detection
unbalanced used giving over 2lac rows
dataset link -> https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud


Project Explanation

The goal is to detect fraudulent transactions from a dataset of credit card usage. Since fraud is rare, the dataset is typically imbalanced, meaning very few transactions are fraudulent compared to legitimate ones. We use classification algorithms to learn the patterns of fraud
Dataset Parameters (Common Fields)

Most datasets used in credit card fraud detection include the following:

Parameter	Description
Time	Seconds elapsed between this transaction and the first one in the dataset.
V1 to V28	Principal components obtained from PCA transformation (to protect confidentiality). These are anonymized features.
Amount	Transaction amount.
Class	Target variable: 0 = legitimate, 1 = fraud.

Some real-world datasets (beyond anonymized public sets) might also include:

    Transaction_ID – Unique ID

    Merchant – Merchant name or ID

    Location – Geographic location

    Card_Type – Credit/debit

    Is_International – Domestic or foreign transaction

    Device_Type, IP_Address, etc.


Imbalanced Dataset

    Class Distribution:

        Class 0 (Not Fraud): 284,315

        Class 1 (Fraud): 492

    Why Important: Imbalanced data can lead to biased models that perform well on majority class but poorly on minority (fraud) class.

    Function: Highlights the need for proper handling to detect fraudulent transactions effectively.



Used stratify=y while splitting the dataset

    Used for: Ensuring that both training and test sets maintain the original class distribution.

    Why: To prevent the model from being exposed to only one class during training or testing.

    Function: Maintains proportional representation of fraud and non-fraud cases in both sets.

Applied Under-sampling and Over-sampling on the Training Set only

    Used for: Balancing the training data by either reducing majority class samples (under-sampling) or increasing minority class samples (over-sampling).

    Why: Balanced training data helps the model learn to detect fraud better.

    Function: Improves model performance on minority class without affecting the real-world distribution in test data.

Test Set Not Sampled

    Used for: Keeping test set as-is (imbalanced).

    Why: In real-world deployment, data will remain imbalanced. Testing on such data shows true model performance.

    Function: Provides realistic evaluation of how the model handles actual fraud detection scenarios.
    
Created a Separate Model with Entirely Balanced Dataset(file name : under sampling to whole to whole dataset.ipynb)

    Used for: Building an ideal project scenario by balancing the whole dataset (not just training data).

    Why: To test and showcase performance when full data is cleanly balanced.

    Function: Helps understand the potential of the model under ideal conditions.

    Used for: Building an ideal project scenario by balancing the whole dataset (not just training data).

    Why: To test and showcase performance when full data is cleanly balanced.

    Function: Helps understand the potential of the model under ideal conditions.
    
Used Cross-Validation in Both Models

        Used for: Evaluating different algorithms by splitting training data into multiple folds and computing average performance.

        Why: Ensures more reliable performance estimates and avoids overfitting.

        Function: Helps select the best-performing algorithm based on mean cross-validation score.

Selected Best Model Based on Cross-Validation Mean Score

        Used for: Identifying the algorithm that generalizes best to unseen data.

        Why: Higher mean score indicates better overall model performance.

        Function: Final model is chosen to predict fraud on x_test using best cross-validation results.

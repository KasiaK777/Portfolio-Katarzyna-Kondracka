                                                      Documentation – Hyperparameter Tuning for LogisticRegression

In this project, hyperparameter tuning of a LogisticRegression model was performed on the Titanic dataset using two approaches: GridSearchCV and RandomizedSearchCV. The goal was to find the best combination of hyperparameters to optimize the F1-score.


Data Preparation

The Titanic dataset was loaded from a CSV file. The Name column was dropped as it is not informative for prediction. The Pclass column was converted to string to treat it as a categorical feature.
Categorical variables (Pclass and Sex) were one-hot encoded using OneHotEncoder. The dataset was split into training and test sets (80/20 split). Hyperparameter Tuning

Model: LogisticRegression

Solver: saga (supports both L1 and L2 penalties)

Max iterations: 10,000 to ensure convergence


Hyperparameters tuned:
penalty: ['l1', 'l2']
C: regularization strength, tested in the range 0.01–10

GridSearchCV:
Explored 200 combinations using a predefined grid of C values and both penalties.

RandomizedSearchCV:
Explored 200 combinations by sampling C from a uniform distribution between 0.01 and 10, with both penalties.

          Results
          
          GridSearchCV best parameters: C ≈ 0.10, penalty = 'l2'
          RandomizedSearchCV best parameters: C ≈ 0.18, penalty = 'l2'
          
          Both methods produced similar optimal hyperparameters, indicating consistency in tuning results.

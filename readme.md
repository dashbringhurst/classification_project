## Telco Classification Project

- The goal of this project is to discover the primary features driving customer churn at Telco. My initial hypothesis is that the top features affecting churn are tenure, monthly charges, and contract type. Other features that possibly affect churn are whether or not the customer has extra services (streaming, online security, etc.), payment type, and internet service type.

- An env.py file and Codeup credentials are required to use the acquire and prepare functions for this project.
- The env.py file should contain credentials set to three variables: user, host, password

#### Data Dictionary

- payment_type_id: manual payments or automatic payments; 1 = electronic check, 2 = mailed check, 3 = bank transfer (automatic), 4 = credit card (automatic)
- internet_service_type_id: 1 = DSL, 2 = Fiber optic, 3 = None
- contract_type_id: 1 = month-to-month, 2 = one year, 3 = two year
- customer_id: unique identifier for each customer (string)
- gender: customer's gender, encoded; 1 = Male, 0 = Female
- senior_citizen: encoded values for senior citizen status; 0 = not senior citizen, 1 = is senior citizen
- partner: whether or not the customer has a partner, encoded; 1 = Yes, 0 = No
- dependents: whether or not the customer has at least one dependent, encoded; 1 = Yes, 0 = No
- tenure: number of months the customer has been with Telco (int)
- phone_service: does the customer have phone service, encoded; 1 = Yes, 0 = No
- multiple_lines: does the customer have more than one line, Yes or No (string)
- online_security: does the customer have online security through Telco, Yes or No (string)
- online_backup: does the customer have online backup service, Yes or No (string)
- device_protection: does the customer have device protection, Yes or No (string)
- tech_support: does the customer have tech support service, Yes or No (string)
- streaming_tv: does the customer have streaming tv service, Yes or No (string)
- streaming_movies: does the customer have streaming movie service, Yes or No (string)
- paperless_billing: is the customer signed up for paperless billing, encoded; 1 = Yes, 0 = No
- monthly_charges: the current monthly charge per customer (float)
- total_charges: total charges per customer (float)
- churn: encoded value for whether or not a customer has churned; 0 = No, 1 = Yes
- contract_type: string values corresponding to contract_type_id (Month-to-month, One year, Two year)
- internet_service_type: string values corresponding to internet_service_type_id
- payment_type: whether the customer uses automatic ('auto') or manual ('manual') payment

#### Project Planning

- Acquire the dataset from the Codeup database using SQL
- Prepare the data with the intent to discover the main drivers of customer churn; clean the data and encode categorical features if necessary; ensure that the data is tidy
- Split the data into train, validate, and test datasets using a 60/20/20 split
- Explore the data:
    - Univariate, bivariate, and multivariate analyses; statistical tests for significance, find the three primary features affecting customer churn
    - Create graphical representations of the analyses
    - Ask more questions about the data
    - Document findings
- Train and test models:
    - Establish a baseline
    - Select key features and train multiple classification models
    - Test the model on the validate set, adjust for overfitting if necessary
- Select the best model for the project goals:
    - Determine which model performs best on the validate set
- Test and evaluate the model:
    - Use the model on the test set and evaluate its performance (classification report, confusion matrix, etc.)
    - Visualize the data using an array of probabilities on the test set
- Create a final report

#### How to Reproduce this Project

- In order to reproduce this project, you will need access to the Codeup database or the .csv of the database. Acquire the database from Codeup using a SQL query, which I saved into a function in acquire.py. The acquire.py and prepare.py files have the necessary functions to acquire, prepare, and split the dataset.

- You will need to import the following python libraries into a python file or jupyter notebook: 
    - import pandas as pd
    - import numpy as np
    - import acquire
    - import prepare
    - import matplotlib.pyplot as plt
    - import seaborn as sns
    - from scipy import stats
    - from sklearn.tree import DecisionTreeClassifier, plot_tree
    - from sklearn.metrics import classification_report
    - from sklearn.metrics import confusion_matrix
    - from sklearn.ensemble import RandomForestClassifier
    - from sklearn.neighbors import KNeighborsClassifier
    - from sklearn.linear_model import LogisticRegression

- Prepare and split the dataset. The code for these steps can be found in the prepare.py file within this repository.
- Use pandas to explore the dataframe and scipy.stats to conduct statistical testing on the selected features.
- Use seaborn or matplotlib.pyplot to create graphs of your analyses.
- Conduct a univariate analysis on each feature using barplot for categorical variables and .hist for continuous variables.
- Conduct a bivariate analysis of each feature against churn and graph each finding.
- Conduct multivariate analyses of the most important features against churn and graph the results.
- Create models (decision tree, random forest, KNearest neighbors, and logistical regression) with the most important selected features using sklearn.
- Train each model and evaluate its accuracy on both the train and validate sets.
- Select the best performing model and use it on the test set.
- Graph the results of the test using probabilities.
- Document each step of the process and your findings.

#### Key Findings, Recommendations, and Takeaways




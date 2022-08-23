## Telco Classification Project

- The goal of this project is to discover the primary features driving customer churn at Telco. My initial hypothesis is that the top features affecting churn are tenure, monthly charges, and contract type. Other features that possibly affect churn are whether or not the customer has extra services (streaming, online security, etc.), payment type, and internet service type.

- An env.py file and Codeup credentials are required to use the acquire and prepare functions for this project.
- The env.py file should contain credentials set to three variables: user, host, password

#### Data Dictionary

- payment_type_id: manual payments or automatic payments; 1 = electronic check, 2 = mailed check, 3 = bank transfer (automatic), 4 = credit card (automatic); (int)
- internet_service_type_id: 1 = DSL, 2 = Fiber optic, 3 = None (int)
- contract_type_id: 1 = month-to-month, 2 = one year, 3 = two year (int)
- customer_id: unique identifier for each customer (string)
- gender: customer's gender, encoded; 1 = Male, 0 = Female (int)
- senior_citizen: encoded values for senior citizen status; 0 = not senior citizen, 1 = is senior citizen (int)
- partner: whether or not the customer has a partner, encoded; 1 = Yes, 0 = No (int)
- dependents: whether or not the customer has at least one dependent, encoded; 1 = Yes, 0 = No (int)
- tenure: number of months the customer has been with Telco (int)
- phone_service: does the customer have phone service, encoded; 1 = Yes, 0 = No (int)
- multiple_lines: does the customer have more than one line, Yes or No (string)
- online_security: does the customer have online security through Telco, Yes or No (string)
- online_backup: does the customer have online backup service, Yes or No (string)
- device_protection: does the customer have device protection, Yes or No (string)
- tech_support: does the customer have tech support service, Yes or No (string)
- streaming_tv: does the customer have streaming tv service, Yes or No (string)
- streaming_movies: does the customer have streaming movie service, Yes or No (string)
- paperless_billing: is the customer signed up for paperless billing, encoded; 1 = Yes, 0 = No (int)
- monthly_charges: the current monthly charge per customer (float)
- total_charges: total charges per customer (float)
- churn: encoded value for whether or not a customer has churned; 0 = No, 1 = Yes (int)
- contract_type: string values corresponding to contract_type_id (Month-to-month, One year, Two year)
- internet_service_type: string values corresponding to internet_service_type_id
- payment_type: whether the customer uses automatic ('auto') or manual ('manual') payment (string)

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
- Document key findings and takeaways, answer the questions
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

- After running four models on my train and validate sets, I decided to use the random forest model because it provided the highest accuracy overall. The difference in accuracy was minimal between the models, however. I used the ten most significant features for customer churn (tenure, monthly charges, contract type, payment type, paperless billing, extra services, senior citizen, dependents, partner). I selected a maximum depth of 14 and a minimum sample leaf size of 14. The accuracy of the model on the test set was 82 percent.

- Takeaways: the biggest drivers of churn are monthly charges, tenure, and contract type. Customers with low monthly charges, high tenure, and a two-year contract have the lowest likelihood of churn. The models all performed similarly for accuracy, but none of the models performed above baseline for recall. If Telco wants to predict customers who actually churn, I would recommend a different model or retraining the selected model for increased recall.

- Recommendations for Telco to improve churn:
    - Get the customers into a contract; the two-year contract customers had the lowest amount of churn, followed by one-year contracts. Month-to-month customers churned more than both contracts combined.
    - Increase the number of extra services per customer; customers with 4 extra services had a much lower rate of churn than customers with no extra services
    - Keep the monthly charges below 60 dollars if possible; customers above the mean monthly charge are more likely to churn
    - Get the customers to stay for over one year; customers are most likely to churn within the first year of service

- If I had more time, I would search the data for more intricate relationships between features that are indicative of churn. I would also tune the models for increased recall and precision for churn.

# Titanic_contest_solution_Kaggle
Titanic survival prediction using XGBoost, feature engineering, and cross-validation. Kaggle Score: 0.76794 | Rank: 7,904. Contest: Titanic - Machine Learning from Disaster

# Titanic Survival Prediction

A machine learning project based on the classic Kaggle Titanic dataset. The goal is to predict whether a passenger survived the Titanic disaster using passenger information such as age, sex, passenger class, fare, family size, and title.

## Project Overview

The project follows an end-to-end machine learning workflow:

* Exploratory Data Analysis (EDA)
* Data preprocessing
* Feature engineering
* Logistic Regression baseline
* Model comparison
* XGBoost model development
* Hyperparameter tuning
* 5-fold stratified cross-validation
* Error analysis
* Kaggle submission

## Features Used

The final model uses:

* `Pclass`
* `Sex`
* `AgeGroup`
* `Fare`
* `Embarked`
* `FamilySize`
* `isAlone`
* `title`

### Engineered Features

**FamilySize**

```text
FamilySize = SibSp + Parch + 1
```

**isAlone**

Indicates whether the passenger was travelling alone.

**AgeGroup**

Age was converted into categorical groups:

* Child
* Teen
* YoungAdult
* Adult
* Senior

**title**

Passenger titles were extracted from passenger names.

Common titles were retained:

* Mr
* Miss
* Mrs
* Master

Other titles were grouped as `Rare`.

## Model

The final model is an **XGBoost Classifier**.

### Configuration

```text
n_estimators = 200
max_depth = 6
learning_rate = 0.1
subsample = 0.8
colsample_bytree = 0.8
```

## Model Evaluation

The final model achieved:

**83.84% ± 1.44% accuracy**

using 5-fold stratified cross-validation.

The standard deviation was tracked to measure how stable the model was across different validation folds.

## Feature Experiments

Several features were tested and kept or rejected based on validation performance.

| Feature / Experiment             | Result  |
| -------------------------------- | ------- |
| FamilySize                       | Kept    |
| isAlone                          | Kept    |
| AgeGroup                         | Kept    |
| title                            | Kept    |
| FamilySizeGroup                  | Dropped |
| HasCabin                         | Dropped |
| TicketGroupSize                  | Dropped |
| Sex + Pclass + title interaction | Dropped |

The goal was to add features based on their actual contribution rather than increasing model complexity unnecessarily.

## Project Structure

```text
Titanic-Survival-Prediction/
│
├── notebooks/
│   ├── EDA.ipynb
│   └── Final_Model.ipynb
│
├── submission.csv
├── README.md
└── requirements.txt
```

## Dataset

The project uses the official Kaggle Titanic dataset.

**Contest:** Titanic - Machine Learning from Disaster

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* XGBoost
* Jupyter Notebook
* Matplotlib
* Seaborn

## Kaggle Results

The final model was submitted to the Kaggle Titanic competition.

* **Kaggle Score:** 0.76794
* **Kaggle Rank:** 7,904

The cross-validation score was higher than the final Kaggle score. This difference is documented rather than hidden and can be investigated in future iterations.

## What I Learned

Through this project, I practiced:

* Building an end-to-end machine learning pipeline
* Handling missing values
* Categorical feature encoding
* Feature engineering
* Cross-validation
* Model comparison
* Hyperparameter tuning
* Error analysis
* Preparing Kaggle submissions

## Future Improvements

* Investigate the difference between cross-validation and Kaggle performance
* Improve the train/test feature pipeline
* Test additional carefully motivated features
* Perform deeper error analysis
* Compare additional classification models

## Kaggle Contest

Titanic - Machine Learning from Disaster

[View Kaggle Contest](https://www.kaggle.com/competitions/titanic?utm_source=chatgpt.com)

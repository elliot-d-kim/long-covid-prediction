# Risk Factors Identification and Prediction of Long COVID

## Overview

A machine learning model built in Python to answer the following questions:
1. What are clinical and sociodemographic risk factors for long COVID?
2. Can we predict long COVID in patients?

Final project for CPSC 66 Machine Learning (Fall 2021), with Emma Jin and Victoria Song.

A summary of our project follows. Our [presentation slides](https://github.com/elliot-d-kim/long-covid-prediction/blob/main/presentation/Final%20Presentation%20For%20CS66.pdf) and formal [research paper](https://github.com/elliot-d-kim/long-covid-prediction/blob/main/paper/paper.pdf) are also included in this repository.

## Table of Contents

- [Problem Context](#problem-context)
- [Goals](#goals)
- [Methods and Results](#methods-and-results)
- [Installation and Usage](#installation-and-usage)
- [Technologies Used](#technologies-used)
- [Contributors](#contributors)
- [Acknowledgements](#acknowledgements)

## Problem Context

While COVID-19 in its acute form is widely discussed and researched, long COVID&mdash;when some COVID symptoms persist even after COVID tests return negative&mdash;is poorly understood. Persisting symptoms reportedly include: loss of smell or taste, shortness of breath, heart problems, anxiety, headaches, and fatigue. As of July 2021, long COVID is officially considered a form of disability under the Americans with Disabilities Act (ADA).

## Goals

Use machine learning to:
* Identify long COVID risk factors
* Predict long COVID in patients

## Methods and Results

Datasets: [COVID-19 Fall 2020 & Winter 2021 Community Supplement, MCBS (Medicare Current Beneficiary Survey)](https://data.cms.gov/medicare-current-beneficiary-survey-mcbs/medicare-current-beneficiary-survey-covid-19-supplement)
* 20,000+ patients
* 390 columns

### Data Pre-processing

**Dimensionality reduction**: Removed obviously irrelevant features such as 'user_id' and week of interview (**feature selection**) and consolidated functionally similar features (**feature extraction**), reducing the complexity of the data

**Resampling**: Upsampled long COVID&ndash;negative patients in training set due to low representation in original dataset, enhancing quality of training data

### Building the ML model

Using scikit-learn, implemented several machine learning models, including:
* Logistic regression
* Decision tree
* Random forest
* SVM
* Naive Bayes

Used validation curves and confusion matrices to tune models' hyperparameters, enhancing accuracy for Logistic Regression, SVM, and Naive Bayes.

Ultimately, our random forest model achieved 72.3% accuracy and 81.5% precision for predicting Long COVID in patients.

### Analyzing Risk Factors

To find the most significant risk factors, we compared the potential risk factors by their **Gini feature importance**. Among the sociodemographic and clinical factors in our analysis, the top risk factor for long COVID was **severity of COVID in its acute stage**.

![image](<./paper/Figure6.jpeg>)

## Installation and Usage

1. Clone this repository.
```bash
git clone https://github.com/elliot-d-kim/long-covid-prediction.git
```
2. Navigate to the project directory.
```bash
cd long-covid-prediction
```
3. Install [Python 3.8](https://www.python.org/downloads/release/python-3810/)
4. Install other dependencies.
```bash
pip install -r requirements.txt
```
5. Navigate to the code directory.
```bash
cd code
```
6. Open the JupyterLab notebook, which will open in the browser.
```bash
jupyter notebook
```
7. Run all code up until before Logistic Regression.
8. Build whichever models are of interest by running their respective sections.

## Technologies Used

* Python 3.6
* scikit-learn
* Pandas
* NumPy
* JupyterLab

## Contributors

* Meiqing Emma Jin
* Xinwei Victoria Song
* Elliot Kim

## Acknowledgements

* This project was the final project for Professor Ben Mitchell's CPSC 66 Machine Learning course in Fall 2021. Thanks to Professor Mitchell for his guidance.

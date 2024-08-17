# Loan Approval Prediction

## Project Overview

This project is focused on predicting loan approvals using a variety of machine learning models. The dataset contains information about applicants and their loan details, and the goal is to predict whether a loan will be approved (`Loan_Status`) based on features like applicant income, loan amount, and credit history. The project culminates in the deployment of the best-performing model, making it accessible as a web service.

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Project Structure](#project-structure)
- [Modeling](#modeling)
  - [Data Preprocessing](#data-preprocessing)
  - [Feature Engineering](#feature-engineering)
  - [Model Selection](#model-selection)
  - [Model Evaluation](#model-evaluation)

- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgements](#acknowledgements)

## Dataset

The dataset used in this project is composed of several features related to loan applicants. The key features include:

- **Gender**
- **Married**
- **Dependents**
- **Education**
- **Self_Employed**
- **ApplicantIncome**
- **CoapplicantIncome**
- **LoanAmount**
- **Loan_Amount_Term**
- **Credit_History**
- **Property_Area**

The target variable is `Loan_Status`, indicating whether the loan was approved (`Y`) or not (`N`).

## Project Structure

```
├── data
│   ├── Copy of loan.xlsx          # Original dataset
├── models
│   ├── random_forest_model.pkl    # Saved Random Forest model
├── app.py                         # Flask application for deployment
├── Dockerfile                     # Docker configuration for containerization
├── requirements.txt               # Python dependencies
├── README.md                      # Project README
└── ...
```

## Modeling

### Data Preprocessing

- **Missing Value Imputation**: Handled using the mode for categorical variables and the mean for numerical variables.
- **Feature Engineering**: Log transformation of the `LoanAmount` feature to normalize its distribution.
- **Label Encoding**: Applied to categorical variables.

### Feature Engineering

- Added a `LoanAmount_log` feature as a log transformation of the `LoanAmount`.

### Model Selection

The following machine learning models were trained and evaluated:

- **Logistic Regression**
- **Random Forest Classifier**
- **Decision Tree Classifier**
- **K-Nearest Neighbors Classifier**

The **Random Forest Classifier** was found to perform the best based on accuracy and recall scores.

### Model Evaluation

- **Grid Search CV**: Performed to tune hyperparameters and improve model performance.
- **Stacking**: Combined the Random Forest and Logistic Regression models to further enhance predictive accuracy.
- **Cross-Validation**: Applied to ensure model generalization.

### Containerization

The project is containerized using Docker, allowing for consistent deployment across different environments.

## Installation

To run this project locally:

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/loan-approval-prediction.git
   cd loan-approval-prediction
   ```

2. Install the required dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

Once the application is running, you can make predictions by sending a POST request to the API with the applicant data in JSON format.

Example request:
```json
{
  "Gender": "Male",
  "Married": "Yes",
  "Dependents": "1",
  "Education": "Graduate",
  "Self_Employed": "No",
  "ApplicantIncome": 5000,
  "CoapplicantIncome": 0,
  "LoanAmount": 200,
  "Loan_Amount_Term": 360,
  "Credit_History": 1,
  "Property_Area": "Urban"
}
```

## Results

The Random Forest model achieved the best performance with a balanced accuracy score of `XX%` and recall of `XX%`. The final deployed model can be accessed via the API for making predictions on new data.

## Contributing

Contributions to this project are welcome. Feel free to fork the repository and submit pull requests for improvements.

## License

This project is licensed under the MIT License. See the `LICENSE` file for more details.




# olympic-medal-prediction-model

Project Overview
This project implements a simple linear regression model to predict the number of Olympic medals a country is likely to win. The prediction is based on two key factors: the number of athletes a country sends to the Olympics and their previous medal performance.

The goal is to provide a straightforward example of a machine learning workflow, from data loading and cleaning to model training, prediction, and evaluation.

Purpose of the Code
The Python script medal_prediction.py (or whatever you name your script) performs the following steps:

Data Loading: Reads historical Olympic team data from a CSV file (teams.csv).

Feature Selection: Selects relevant columns for the prediction task.

Exploratory Data Analysis (EDA):

Calculates correlations between features and the target variable (medals).

(If uncommented) Visualizes relationships between athletes, age, and medals using scatter plots with regression lines.

Visualizes the distribution of medal counts using a histogram.

Data Preprocessing: Handles missing values by dropping rows that contain any NaN entries.

Data Splitting: Divides the dataset into training and testing sets based on the year (data before 2012 for training, data from 2012 onwards for testing). This simulates predicting future events.

Model Training: Trains a LinearRegression model using the athletes and prev_medals as predictors to forecast medals.

Prediction: Generates medal predictions for the test set.

Post-processing Predictions: Adjusts predictions to ensure they are non-negative and rounded to whole numbers (as medal counts must be integers).

Model Evaluation: Calculates the Mean Absolute Error (MAE) to quantify the average difference between actual and predicted medal counts.

Error Analysis: Further analyzes prediction errors, including average error by team and error ratios, to identify where the model performs well or struggles.

How to Run the Code
To run this project on your local machine, follow these steps:

Prerequisites
Python: Ensure you have Python 3.7 or newer installed.

Required Libraries: You'll need the following Python libraries. You can install them using pip:

pip install pandas scikit-learn numpy seaborn

(Note: seaborn is commented out in your provided code, but the sns.lmplot calls indicate its intended use. It's good practice to install it if you plan to enable those visualization lines.)

Data Setup
Download teams.csv: The code expects a CSV file named teams.csv. You can obtain this dataset from various sports analytics or machine learning dataset repositories.

Important: Place the teams.csv file in the same directory as your Python script (medal_prediction.py). If you place it elsewhere, you'll need to update the file path in the pd.read_csv() line (e.g., teams = pd.read_csv("path/to/your/teams.csv")).

Running the Script
Save the Code: Save the provided Python code into a file named medal_prediction.py (or any other .py extension).

Open Terminal/Command Prompt: Navigate to the directory where you saved your medal_prediction.py file and teams.csv.

Execute the Script: Run the script using the Python interpreter:

python medal_prediction.py

The script will execute, print various DataFrame outputs, the MAE, and other error analysis results to your console. If you uncomment the sns.lmplot lines, it will also generate plots (which might require a graphical backend or saving them to files).

Interesting Findings and Limitations
Findings:
Correlation: You'll likely observe a positive correlation between the number of athletes and prev_medals with medals, indicating that sending more athletes and having a history of winning medals are strong indicators of future medal counts.

MAE: The Mean Absolute Error provides a concrete measure of how far off, on average, the predictions are from the actual medal counts.

Error Ratio: Analyzing the error_ratio by team can reveal which countries the model struggles to predict accurately, often due to unique circumstances or outlier performances not captured by the simple linear model.

Limitations:
Simplicity of Model: A simple linear regression may not capture complex, non-linear relationships in the data. Factors like political events, economic changes, specific sports performance, or doping scandals are not considered.

Limited Predictors: The model only uses athletes and prev_medals. Incorporating more features (e.g., GDP, population, investment in sports, host nation status) could improve accuracy.

Temporal Split: While a good practice, the fixed 2012 split might not be optimal for all scenarios. A more robust evaluation would involve cross-validation or a more sophisticated time-series validation strategy.

Data Quality: The model's performance is highly dependent on the quality and completeness of the teams.csv data. Missing values are simply dropped, which might lead to loss of valuable information if many rows are affected.

Rounding and Non-negativity: The post-processing steps (setting negative predictions to zero and rounding) are practical but introduce a slight deviation from the pure linear model's output.

Data Source (Optional - if you know where the data came from)
The teams.csv dataset typically contains historical Olympic team data, including details about countries, years, number of athletes, age of athletes, previous medal counts, and actual medal counts. This kind of data is often compiled from official Olympic records or publicly available sports statistics databases.

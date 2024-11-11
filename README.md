# Maharashtra Assembly Election Prediction

This project uses historical election data and sentiment analysis to predict the outcomes of the Maharashtra state assembly elections. Leveraging data from 1962 to 2019 and web-scraped sentiment scores of each party, this model forecasts potential winning outcomes, indicating whether the assembly has a majority or if a coalition is likely required.

## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Collection and Preprocessing](#data-collection-and-preprocessing)
3. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
4. [Feature Engineering](#feature-engineering)
5. [Model Training and Prediction](#model-training-and-prediction)
6. [Post-Processing: Sentiment Analysis](#post-processing-sentiment-analysis)
7. [Final Results](#final-results)
8. [Getting Started](#getting-started)
9. [Project Structure](#project-structure)
10. [Acknowledgments](#acknowledgments)

## Project Overview
The objective of this project is to develop a predictive model for the Maharashtra state assembly elections. By examining historical voting data and current public opinion, this model provides an analysis of seat distribution among political parties, as well as an indication of which parties may form a coalition if a majority is not reached.

## Data Collection and Preprocessing
### Historical Data
Historical election data was collected, covering Maharashtra assembly elections from 1962 to 2019. The data includes:
- Constituency names
- Year and election results
- Party names and candidates' positions
- Votes received

### Sentiment Data
To capture current opinions, news articles were scraped, and sentiment scores were generated for each major party using sentiment analysis tools. Each party received an average sentiment score based on recent public and media sentiments nearing the election.

### Preprocessing Steps
1. **Data Wrangling**: Removing inconsistencies and standardizing column names.
2. **Data Cleaning**: Handling missing values, correcting data types, and filtering out erroneous records.
3. **Encoding**: Label encoding was used for categorical features like party names and constituencies.
4. **Feature Scaling**: Numeric features were standardized to ensure even scaling across the model.

## Exploratory Data Analysis (EDA)
EDA was performed to:
- Analyze vote distribution across parties.
- Examine trends in constituency outcomes over time.
- Visualize data correlations and feature relevance for model inputs.

## Feature Engineering
Key features were created to enhance the model’s predictive power:
- **Const_Victory_Rate**: Historical win rate for each party by constituency.
- **Recent_Victory_Rate**: Recent win rate over the last two elections for each party.
- **Type_Victory_Rate**: Win rate by constituency type (e.g., urban vs. rural).
- **Incumbent_Success**: Advantage metric for parties with incumbents.

These engineered features capture trends that significantly impact election outcomes, improving model performance.

## Model Training and Prediction
An ensemble model was trained using:
- **XGBoost**: A boosting algorithm that excels in handling tabular data with non-linear patterns.
- **RandomForest**: An ensemble of decision trees that reduces overfitting and handles diverse feature interactions.

The ensemble model, using a soft voting strategy, assigns probabilities to each party winning a constituency. **GridSearchCV** was used to tune hyperparameters, ensuring optimal performance.

### Evaluation Metrics
- **Accuracy**: Proportion of correctly predicted winners.
- **Precision, Recall, F1-Score**: Detailed metrics for each party to assess prediction reliability and minimize misclassification.

## Post-Processing: Sentiment Analysis
After initial predictions, sentiment scores for each party were applied to adjust win probabilities:
- The model output was weighted by each party’s average sentiment score.
- This adjustment reflects recent public sentiment trends, enhancing the relevance of predictions.

## Final Results
The final results provide:
- **Predicted Seats per Party**: The likely seat count for each party.
- **Majority Status**: Indicates if any party has achieved a majority (145 seats) or if a coalition is needed.
- **Coalition Scenarios**: In the event of a hung assembly, suggested coalitions based on seat counts to meet majority requirements.

Sample Output:
- Party-wise seat distribution.
- Status of the assembly (majority or hung).
- Potential coalition configurations, e.g., Party A + Party B with combined seats.


## Project Structure
- `data/`: Directory for storing raw and processed datasets.
- `notebooks/`: Google Colab notebooks for EDA and model development.
- `scripts/`: Scripts for data preprocessing, feature engineering, and model evaluation.
- `results/`: Directory where prediction results are saved.

## Acknowledgments
Thanks to the Maharashtra Election Commission for providing historical data and various online sources for recent news articles used for sentiment analysis. 

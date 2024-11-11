# Maharashtra Assembly Election Prediction

This project predicts outcomes for the Maharashtra state assembly elections using historical election data (1962–2019) and sentiment analysis of public opinion as captured from recent web news articles. The model forecasts potential winning outcomes, indicating whether the assembly has a majority or requires a coalition, and provides insights on seat distribution among political parties.

## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Collection and Preprocessing](#data-collection-and-preprocessing)
3. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
4. [Sentiment Analysis](#sentiment-analysis)
5. [Feature Engineering](#feature-engineering)
6. [Model Training and Prediction](#model-training-and-prediction)
7. [Post-Processing and Sentiment Adjustment](#post-processing-and-sentiment-adjustment)
8. [Final Results](#final-results)
9. [Getting Started](#getting-started)
10. [Project Structure](#project-structure)
11. [Acknowledgments](#acknowledgments)

## Project Overview
The objective is to create a predictive model for Maharashtra's elections. Using historical data trends and current public sentiment, this model analyzes party-wise seat distribution, highlights winning parties, and assesses coalition needs in the event of a hung assembly.

## Data Collection and Preprocessing
### Historical Data
Historical data from Maharashtra assembly elections (1962-2019) includes:
- Constituency names
- Election year and results
- Party affiliations, candidates’ positions
- Vote counts

### Sentiment Data
To gauge current public opinion, we scraped recent news articles and applied sentiment analysis to assess the perception of major political parties. Each party received an average sentiment score based on recent news and media sentiment, reflecting the public’s mood nearing the elections.

### Preprocessing Steps
1. **Data Cleaning**: Handled missing values, corrected data types, and filtered out erroneous records.
2. **Data Wrangling**: Standardized formats, organized columns, and consolidated similar party names.
3. **Encoding**: Applied label encoding to categorical features like party names and constituencies.
4. **Feature Scaling**: Used standardization to normalize numerical features.

## Exploratory Data Analysis (EDA)
EDA focused on:
- Understanding vote distributions across parties.
- Identifying voting trends and constituency outcomes.
- Visualizing correlations between features to inform model input selections.

### Visualizations
- **Bar Plot of Sentiment Scores**: Displayed average sentiment scores per party, providing an initial view of public opinion.
- **Heatmap**: Illustrated sentiment polarity across parties, highlighting positive to negative perceptions.

## Sentiment Analysis
Sentiment analysis on scraped news articles used **TextBlob** to calculate sentiment polarity, allowing us to:
1. **Extract Sentiment**: Each article’s sentiment score was calculated, indicating positive or negative bias toward parties.
2. **Average Sentiment per Party**: Grouped articles by party mentions and computed average sentiment scores.
   
   These sentiment scores later adjusted the model’s predictions, offering a nuanced forecast that incorporates recent public opinion.

## Feature Engineering
Key features were created to enhance the predictive model:
- **Const_Victory_Rate**: Historical win rate of each party in a given constituency.
- **Recent_Victory_Rate**: Win rate over the last two elections to capture recent trends.
- **Type_Victory_Rate**: Constituency-type-based win rate (e.g., urban or rural).
- **Incumbent_Success**: Represents advantage if a party holds the constituency.

These engineered features add depth, capturing important political patterns over time to boost model accuracy.

## Model Training and Prediction
An ensemble model was trained, leveraging:
- **XGBoost**: Effective for handling complex relationships in tabular data.
- **RandomForest**: Ensemble decision trees to generalize well across constituencies.

The ensemble model uses a **soft voting** method, aggregating probabilities from both algorithms to decide constituency winners.

### Model Evaluation
- **Accuracy**: Measures the overall rate of correct predictions.
- **Precision, Recall, F1-Score**: Evaluates each party’s performance, offering insights into prediction reliability and misclassification patterns.

## Post-Processing and Sentiment Adjustment
After the initial predictions, sentiment scores were applied to adjust winning probabilities:
- Sentiment scores for each party influenced the likelihood of constituency wins.
- This adjustment incorporates public sentiment into the model’s output, reflecting the recent mood toward each party.

## Final Results
The final predictions include:
- **Seat Prediction per Party**: Likely seat distribution among parties.
- **Assembly Majority Status**: Indicates if any party has a majority (145 seats) or if a coalition is required.
- **Coalition Scenarios**: Suggested alliances if no single party achieves a majority.

### Sample Output:
- **Predicted Seat Distribution**: Party-wise seat counts.
- **Assembly Status**: Majority or hung status.
- **Coalition Possibilities**: Potential combinations for forming a majority, based on seat counts.

3. **Running the Project**:
   - Place the election data and sentiment data in the appropriate directories.
   - Run the model script to generate predictions and view results.

## Project Structure
- `data/`: Raw and processed datasets.
- `notebooks/`: EDA, sentiment analysis, and model development notebooks.
- `scripts/`: Data preprocessing, feature engineering, and model evaluation scripts.
- `results/`: Directory where prediction outputs are saved.

## Acknowledgments
Thanks to the Maharashtra Election Commission for historical election data and various online sources for recent news articles used in sentiment analysis.

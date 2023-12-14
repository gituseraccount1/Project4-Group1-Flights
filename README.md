# Flight Cancellation Prediction Project

## Project Overview

This project aims to develop and train a machine learning model to predict flight cancellations in the United States. The dataset used for this project spans the years 2022 and 2023 and is sourced from [Kaggle](https://www.kaggle.com/datasets/patrickzel/flight-delay-and-cancellation-dataset-2019-2023). Due to the large file sizes, the dataset files are not included in this repository. You can access the dataset [here](https://www.kaggle.com/datasets/patrickzel/flight-delay-and-cancellation-dataset-2019-2023).

## Data Source

The project relies on the following dataset files:

- [2022.csv](https://www.kaggle.com/datasets/patrickzel/flight-delay-and-cancellation-dataset-2019-2023)
- [2023.csv](https://www.kaggle.com/datasets/patrickzel/flight-delay-and-cancellation-dataset-2019-2023)

To merge and process the data, we referred to the [GeeksforGeeks guide on merging two PySpark DataFrames](https://www.geeksforgeeks.org/merge-two-dataframes-in-pyspark/).

To find the Count of NaN in each column of the DataFrame [here](https://note.nkmk.me/en/python-pandas-nan-judge-count/).

## Visualizations
- Our tableau files are here: https://public.tableau.com/app/profile/jacob.anderson2507/viz/Project4BothYearsVisualizations/UseThisStory?publish=yes
- Our visualizations include:
  - Flight Cancellations by Month
  - Total Number of Flights by Month
  - Total Number of Cancelled Flights by Cancellation Type
  - Total Number of Cancellations by Airline
  - Number of Cancellations by Destination in 2022
  - Number of Cancellations by Destination in 2023
  - Total Number of Cancellations by Origin
  - Cancellations by Origin Map

## Data Cleanup
- From the kaggle data site, we used .csv files from 2022 and 2023.
- We uploaded both files to an Amazon AWS S3 bucket.
- The files were very large totaling 11,274,547 rows of data from January 2022 through August 2023.
- For data cleaning, we located the null or NaN values and dropped those columns of data from our DataFrame.
- We also dropped columns that were non-integer columns in order to use the data in the machine learning model.

### Machine Learning / Modeling
- For the machine learning model, we adopted a supervised learning approach, leveraging the fact that we had labeled data indicating whether flights were canceled.
- We assigned the target (y) to the CANCELLED column
- For our features (X), we used CANCELLATION_CODE, AIRLINE_CODE, ORIGIN, ORIGIN_CITY, DEST, DEST_CITY and FL_DATE
- We ran a Logistic Regression Model
  - We used the Standard Scaler, the LogisticRegression from sckit-learn and train_test_split in our combined 2022 & 2023 Dataframe.
  - This generated the confusion matrix and classification reports
- We also ran a Random Forest Model
  - We used the same target and features and received the same 100% accuracy on this model as the Logistic Regression Model.   

## Conclusion
 - This type of model incorporteed into existing systems for automated decision support could streamline processes for flight scheduling, staffing and passenger communications and offer valuable efficiency gains for the airlines.
 - However, we did discover some limitations:
   - Imbalanced Data
   - Real-time Nature of Cancellations
   - Partial Year Data
   - Data Completeness
 - Next Steps could include:
   - Finding workarounds for limitations
   - Improving our Tableau map
   - Bringing in data from other years
   - Bringing in a wider variety of data for the model

## Acknowledgements:

### Thank you to everyone that helped us out on this project.
- Tutor:
  - Limei Hou
- TA's:
  - Randy & Sam
- Instructor:
  - Hunter Hollis


Here are some initial insights derived from the analysis:

- **Cancellation Frequency:** Analyzed the overall frequency of flight cancellations to understand the distribution.

- **Correlation Analysis:** Explored correlations between different features and the likelihood of flight cancellations.

- **Time Analysis:** Investigated whether there are specific times of the day, days of the week, or months with higher cancellation rates.

### Future Work

- **Model Optimization:** Document the optimization process, including iterative changes made to the model and their impact on performance. Consider using tools like MLflow to track parameters and metrics during training.

- **Visualization:** Enhance the project with visualizations to better understand data patterns, model predictions, and evaluation metrics.

- **Explainability:** Consider techniques like SHAP values for explaining model predictions, adding transparency to the decision-making process.

- **Scaling:** Assess the scalability of the solution, especially if the dataset grows significantly. Ensure the code and model perform efficiently.

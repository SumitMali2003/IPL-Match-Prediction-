# IPL Match Prediction using PySpark

This is a small IPL data analysis and prediction project that I made using **PySpark**.

The main idea of this project is to explore IPL match data, get some basic insights from it, and then use a simple machine learning model to predict the match winner based on the two teams and the toss winner.

## What I used

- Python
- PySpark
- Spark MLlib
- Pandas/Notebook environment
- Jupyter Notebook / Google Colab
- IPL match CSV dataset

## What the project does

The notebook mainly covers these steps:

1. Starts a local Spark session.
2. Loads the IPL `Match.csv` file using a defined schema.
3. Checks the match data structure.
4. Finds the number of matches played in each season.
5. Finds teams with the most match wins.
6. Finds the venues where the most matches were played.
7. Converts team names into numerical values using `StringIndexer`.
8. Creates features using:
   - Team 1
   - Team 2
   - Toss winner
9. Trains a Logistic Regression model using Spark MLlib.
10. Uses the trained model to predict a possible match winner.
11. Includes a simple dropdown-based interface in the notebook for selecting the teams and toss winner.

## Dataset

The project expects a file named:

```text
Match.csv
```

The CSV should contain IPL match information such as:

- Team 1
- Team 2
- Match date
- Season
- Venue
- Toss winner
- Match winner
- Win type
- Win margin
- Player of the match
- and other match-related fields

Place the CSV file in the same environment where the notebook is running. In the current notebook, the file is loaded from:

```text
/content/Match.csv
```

This path is mainly for Google Colab. If you are running the project locally, change the path to wherever your `Match.csv` file is stored.

## How to run

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

### 2. Install the required packages

```bash
pip install pyspark findspark
```

If you are using Google Colab, the notebook already contains the installation command.

### 3. Add the dataset

Upload `Match.csv` to the project environment.

For Google Colab, you can upload it through the Files section.

### 4. Open the notebook

Open:

```text
Copy_of_IPLproject.ipynb
```

Run the cells from top to bottom.

## Machine Learning part

For the prediction part, I used **Logistic Regression** from PySpark MLlib.

The input features are:

```text
team1
team2
tosswinner
```

Since these values are text, they are converted into numerical indexes using `StringIndexer`. These indexed values are then combined using `VectorAssembler` and passed to the Logistic Regression model.

The notebook also has a `predict_winner()` function that can be used to give a prediction for a selected match setup.

## Interactive prediction

The notebook includes dropdowns where you can select:

- Team 1
- Team 2
- Toss Winner

and then click **Predict Winner**.

The interface is mainly added to make the project easier to use and demonstrate.

## Project structure

```text
.
├── Copy_of_IPLproject.ipynb
├── Match.csv
└── README.md
```

## Note

This is a learning/project implementation, so the prediction part is fairly simple.

The notebook also contains a demo UI where the displayed accuracy is currently set to `85%` and the button prediction logic is simplified based on the toss winner. This should not be treated as the actual measured accuracy of the Logistic Regression model.

A future version of the project could improve this by properly evaluating the trained model on separate training and testing datasets and using the model itself for every UI prediction.

## Future improvements

Some things I would like to improve:

- Use a proper train/test split.
- Calculate real model accuracy using evaluation metrics.
- Add more features such as venue, season, city, and team performance.
- Try other ML algorithms and compare their results.
- Improve the prediction interface.
- Add more IPL statistics and visualizations.
- Handle teams and data from newer IPL seasons.

## Author

Made as an IPL data analysis and machine learning project using PySpark.

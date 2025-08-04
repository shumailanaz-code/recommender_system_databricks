# 🎮 Steam Game Recommender System using PySpark & MLlib

## 👩‍💻 Overview

This project builds a **collaborative filtering-based recommender system** using the [Steam 200k dataset](#) (provided via Blackboard). The dataset captures users' purchasing and playing behavior on the Steam video game platform and is analyzed using **Apache Spark** and **MLlib ALS (Alternating Least Squares)** in a Databricks environment.

The recommender system is trained to predict game preferences and suggest personalized recommendations based on implicit user feedback.

---

## 📦 Dataset Description

The dataset `steam-200k.csv` contains four columns:

1. **User ID** — Unique identifier for each member  
2. **Game Name** — Title of the game  
3. **Behavior** — Either `'purchase'` or `'play'`  
4. **Value** — 
   - `1` if the behavior is a purchase  
   - Number of hours played if the behavior is `'play'`

Some user-game combinations appear twice (once for purchase, once for play).

---

## 🎯 Objectives

- Load and preprocess the dataset in Spark
- Explore the structure and distribution of user behavior
- Generate **unique integer IDs for games** to make them compatible with ALS
- Train and evaluate a **collaborative filtering model** using Spark MLlib
- Compare different strategies:
  - Using only `'play'` behavior
  - Using both `'purchase'` and `'play'` for implicit feedback
- Display sample recommendations and evaluate performance

---

## 🧠 Key Steps

### 1. 📊 Exploratory Data Analysis
- Count of unique users and games
- Most played/purchased games
- Distribution of hours played
- Handling duplicates and filtering anomalies

### 2. 🔄 Preprocessing
- Generating unique integer IDs for each game directly within Databricks (no external `games.csv` used)
- Encoding user and game IDs as integers
- Creating implicit rating matrix based on playtime or combined behavior

### 3. 🤖 ALS Recommender Training
- Split dataset into training and test sets
- Train ALS model with hyperparameter tuning
- Evaluate using RMSE or ranking-based metrics

### 4. 🔍 Recommendations
- Show top-N recommended games for sample users
- Show similar games to a given title
- Compare results from different behavioral strategies

---

## 🛠 Technologies Used

- **Apache Spark** (PySpark)
- **Spark MLlib ALS**
- **Databricks**
- **Spark SQL**
- **Python**
- **Matplotlib / Seaborn** (optional for visualizations)

---

## 📌 Notes

- This project **generates game IDs within Spark** using `StringIndexer` or mapping logic, avoiding dependency on `games.csv`.
- Implicit feedback is handled using `'play'` time, optionally scaled or filtered for quality.
- The system can be adapted to recommend:
  - Top games per user
  - Similar games based on latent factors
  - Popular or trending games

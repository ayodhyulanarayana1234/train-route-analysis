# 🚆 Train Route Analysis and Journey Time Prediction

A Data Science project focused on analyzing train route data, discovering travel patterns, and predicting train journey duration using Linear Regression.

## 📌 Project Overview

This project was completed as part of an internship Data Science project.

The original dataset contains station-level information for trains, including train numbers, station names, arrival and departure times, route numbers, and cumulative distance.

The project follows a structured Data Science workflow:

**Data Overview → Data Cleaning → Feature Engineering → Exploration → Visualization → Prediction**

The final prediction model uses:

- **Total Distance**
- **Number of Stops**

to predict:

- **Journey Duration**

---

## 🎯 Project Objectives

The main objectives of this project are:

- Understand and analyze real-world train transportation data.
- Identify the structure and characteristics of the dataset.
- Clean and transform station-level data into train-level journey data.
- Explore relationships between distance, stops, routes, stations, and journey duration.
- Create meaningful visualizations to communicate important patterns.
- Build a Linear Regression model to predict journey duration.
- Evaluate the model using MAE and RMSE.
- Develop a simple journey-time prediction function.

---

## 📊 Dataset

The original dataset contains:

| Property | Value |
|---|---:|
| Records | 186,074 |
| Columns | 12 |
| Unique Trains | 11,113 |
| Unique Stations | 8,147 |
| Missing Values | 0 |
| Duplicate Rows | 0 |
| Maximum Distance | 4,260 km |

### Original Dataset Columns

| Column | Description |
|---|---|
| `SN` | Serial number of the station record |
| `Train_No` | Train number |
| `Station_Code` | Station code |
| `1A` | First AC information |
| `2A` | Second AC information |
| `3A` | Third AC information |
| `SL` | Sleeper class information |
| `Station_Name` | Station name |
| `Route_Number` | Route number |
| `Arrival_time` | Arrival time |
| `Departure_Time` | Departure time |
| `Distance` | Cumulative distance |

---

# 🔎 Project Workflow

## Level 1 — Data Overview

The first stage focused on understanding the structure and quality of the dataset.

Tasks completed:

- Identified the total number of records and columns.
- Identified unique trains and stations.
- Created a train-wise start and end station table.
- Calculated basic statistics for distance and station records.
- Checked missing values and duplicate records.
- Investigated distance ordering and route structure.

### Key findings

- 186,074 station-level records were available.
- 11,113 unique trains were identified.
- 8,147 unique stations were identified.
- No missing values were found.
- No duplicate rows were found.
- Distance values ranged from 0 km to 4,260 km.

---

## Level 2 — Data Cleaning & Feature Engineering

The original dataset was station-level, meaning one train could have many rows corresponding to different stations.

The data was transformed into a train-level dataset where each complete train journey is represented by one row.

### Features created

- `Start_Station`
- `End_Station`
- `Start_Departure`
- `End_Arrival`
- `Total_Distance`
- `Number_of_Stops`
- `Journey_Duration`

### Data quality

After cleaning and transformation:

| Property | Result |
|---|---:|
| Complete train journeys | 11,112 |
| Columns | 8 |
| Missing values | 0 |
| Duplicate rows | 0 |
| Duplicate train numbers | 0 |

One incomplete train record was excluded from the final train-level dataset because it did not represent a complete journey.

---

## 📈 Level 3 — Data Exploration

Exploratory Data Analysis was performed to understand:

- Journey duration across routes.
- Train traffic across stations.
- Relationship between distance and journey duration.

### Journey Duration

Journey durations varied substantially, from a few minutes to several days.

The average journey duration was approximately:

**7 hours 14 minutes**

The presence of unusually long durations was investigated and documented as a data limitation.

### Station Traffic

Station traffic was measured using the number of train-level records where a station appeared as either a starting or ending station.

The highest train traffic was observed at:

**CST-MUMBAI — 1,027 train associations**

Other high-traffic stations included:

- SEALDAH
- CHENNAI BEAC
- HOWRAH JN.
- KALYAN JN.

### Distance vs Journey Duration

Total distance and journey duration showed a very strong positive relationship.

**Correlation: 0.9835**

This indicates that longer train journeys generally require longer journey durations.

---

# 📊 Level 4 — Visualization & Pattern Analysis

Several visualizations were created to communicate the findings.

### 1. Journey Duration Across Routes

Routes were compared based on their average reconstructed journey duration.

Long-distance routes generally had substantially higher journey durations.

### 2. Station-wise Train Traffic

A bar chart was created to identify stations with the highest train traffic based on their start/end associations.

### 3. Distance vs Journey Duration

A scatter plot was created to visualize the relationship between total distance and journey duration.

The visualization showed a strong approximately linear upward trend.

---

# 🤖 Level 5 — Prediction Model

A Linear Regression model was developed to predict journey duration.

### Features

The model uses two input features:

```text
Total_Distance
Number_of_Stops
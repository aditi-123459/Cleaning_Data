 

# YouTube Trending Data – Data Cleaning & Preprocessing

## 📌 Project Overview

This project focuses on cleaning and preprocessing a YouTube Trending dataset to prepare it for analysis and machine learning.

The objective is to ensure the dataset is:

* Clean
* Consistent
* Free from duplicates
* Logically valid
* Properly formatted

A structured preprocessing pipeline was implemented to improve data quality and reliability.

## Dataset Information

* **Total Records:** 6234
* **Total Columns:** 16
* **Dataset Shape:** `(6234, 16)`

The dataset includes:

* `title`
* `channel_title`
* `views`
* `trending_date`
* `publish_time`
* `description`
* `tags`
* `comments_disabled`
* Other engagement-related metrics

## 🛠 Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn

##  Data Preprocessing Workflow

### 1️⃣ Dataset Overview

* `df.shape`
* `df.info()`
* `df.describe()`

### 2️ Handling Missing Values

Filled missing text values:

```python
df["description"] = df["description"].fillna("")
df["tags"] = df["tags"].fillna("[none]")
Filled missing numerical values using median:

```python
df["views"] = df["views"].fillna(df["views"].median())

### 3️⃣ Removing Duplicate Records

```python
df = df.drop_duplicates()

### 4️ Text Cleaning & Standardization

```python
df["title"] = df["title"].str.strip().str.lower()
df["channel_title"] = df["channel_title"].str.strip().str.lower()

### 5️ DateTime Conversion

```python
df["trending_date"] = pd.to_datetime(df["trending_date"], format='%y.%d.%m')
df["publish_time"] = pd.to_datetime(df["publish_time"])

### 6️ Encoding Boolean Features

```python
df["comments_disabled"] = df["comments_disabled"].astype('boolean').fillna(False).astype(int)

### 7️ Data Validation

Checked for invalid negative values:

```python
(df["views"] < 0).sum()
```

Removed invalid records:

```python
df = df[df["views"] >= 0]


### 8️ Removing Irrelevant Columns

```python
if 'thumbnail_link' in df.columns:
    df.drop('thumbnail_link', axis=1, inplace=True)


### 9️ Final Dataset Inspection

```python
df.info()
df.describe()

## Key Outcomes

* Missing values handled
* Duplicate rows removed
* Text standardized
* Date columns converted
* Boolean features encoded
* Invalid values filtered
* Dataset ready for EDA or Machine Learning

## Author

Aditi

 

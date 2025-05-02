# Titanic Dataset - Data Cleaning and Exploratory Data Analysis (EDA)

## 📄 Project Overview

This project focuses on data cleaning and exploratory data analysis (EDA) of the famous **Titanic dataset** from [Kaggle](https://www.kaggle.com/c/titanic/data). The goal is to understand the structure and quality of the data, explore relationships between variables, and identify patterns that influence survival rates on the Titanic.

---

## 📂 Dataset

* **Source**: [Kaggle Titanic Competition](https://www.kaggle.com/c/titanic/data)
* **Files**:

  * `train.csv`: The training dataset with labels (used for EDA and modeling).
  * `test.csv`: The test dataset (used for predictions, not covered in this EDA).

---

## 🧼 Data Cleaning Steps

1. **Load Data**:

   ```python
   import pandas as pd
   df = pd.read_csv('train.csv')
   ```

2. **Check for Missing Values**:

   ```python
   df.isnull().sum()
   ```

   * `Age`, `Cabin`, and `Embarked` contain missing values.

3. **Handle Missing Data**:

   * **Age**: Filled with median age.
   * **Cabin**: Dropped due to excessive missing values.
   * **Embarked**: Filled with the mode.

4. **Drop Irrelevant Columns**:

   * Dropped `Ticket` and `Cabin` for simplicity in analysis.

5. **Convert Categorical Variables**:

   * Encoded `Sex` and `Embarked` into numerical values using `pd.get_dummies()`.

---

## 📊 Exploratory Data Analysis (EDA)

### 1. **Survival Distribution**

```python
df['Survived'].value_counts().plot(kind='bar')
```

* Around 38% of passengers survived.

### 2. **Survival by Gender**

```python
import seaborn as sns
sns.barplot(x='Sex', y='Survived', data=df)
```

* Women had a much higher survival rate than men.

### 3. **Survival by Passenger Class**

```python
sns.barplot(x='Pclass', y='Survived', data=df)
```

* First-class passengers had the highest survival rate.

### 4. **Age Distribution**

```python
sns.histplot(df['Age'].dropna(), bins=30, kde=True)
```

* Most passengers were between 20 and 40 years old.

### 5. **Survival by Age**

```python
sns.boxplot(x='Survived', y='Age', data=df)
```

* Children had a higher survival rate.

### 6. **Survival by Embarked Port**

```python
sns.barplot(x='Embarked', y='Survived', data=df)
```

* Passengers who embarked from Cherbourg had higher survival rates.

---

## 🔍 Key Insights

* **Gender**: Being female greatly increased the chance of survival.
* **Class**: First-class passengers were more likely to survive.
* **Age**: Younger passengers, especially children, had better survival rates.
* **Embarkation Port**: Port of embarkation influenced survival, possibly related to class distribution.

---

## 📁 Files Included

* `Task02.ipynb` - Jupyter Notebook with full EDA code and visualizations
* `README.md` - Project documentation (this file)

---

## 📌 Tools Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook

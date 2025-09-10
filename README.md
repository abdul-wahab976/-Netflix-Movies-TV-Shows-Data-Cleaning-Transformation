# 📊 Netflix Movies & TV Shows Data Cleaning & Transformation

## 📌 Project Overview
This project focuses on cleaning and transforming the **Netflix Movies and TV Shows dataset** consisting of **8,807 entries and 12 columns**.  
The dataset includes details such as `title`, `director`, `cast`, `country`, `date_added`, `release_year`, `rating`, `duration`, `listed_in`, and `description`.

The main goal of this project was to **identify structural issues, handle missing values, transform messy data into usable formats, and prepare the dataset for further analysis**.

---

## 🗂️ Dataset Summary
- **Rows:** 8,807  
- **Columns:** 12  
- **Key Features:**
  - `show_id`: Unique identifier for each show
  - `type`: Movie or TV Show
  - `title`: Title of the content
  - `director`: Director(s) of the show
  - `cast`: Main cast members
  - `country`: Country of origin
  - `date_added`: Date when the show was added to Netflix
  - `release_year`: Release year of the content
  - `rating`: Audience rating
  - `duration`: Duration in minutes (Movies) or number of Seasons (TV Shows)
  - `listed_in`: Genre categories
  - `description`: Short description/summary

---

## ⚠️ Issues Identified in the Dataset
1. **Missing Values**  
   - `director`, `cast`, `country`, `date_added`, `rating`, `duration` had several missing values.

2. **Messy Data Types**  
   - `date_added` was in **string format**, needed conversion to `datetime`.  
   - `duration` was a mix of `"min"` and `"Season"`, stored as text.

3. **Structural Issues**  
   - `duration` column contained **two types of information** → numeric value and unit (`min` or `Season`).

4. **Duplicate Values**  
   - Columns like `type`, `country`, `rating`, etc., naturally had repeated values (not a problem).  
   - Only **row-level duplicates** were considered for removal.

---

## 🛠️ Approach to Cleaning & Transformation
1. **Handling Missing Values**
   - For categorical columns (`director`, `cast`, `country`) → filled with `"Unknown"`.
   - For `date_added` → used `NaT` (Not a Time) with `errors='coerce'`.
   - For `rating` and `duration` → filled missing values with `"Unknown"`.

2. **Fixing Data Types**
   - Converted `date_added` → proper `datetime` format.
   - Created two new columns from `duration`:
     - `duration_int`: numeric value (e.g., `90`, `2`, `1`)
     - `duration_type`: unit (`min` or `Season`)

3. **Splitting Columns for Better Usability**
   - `listed_in` (genres) → split into multiple genres.  
   - `cast` and `country` → kept as lists for analysis flexibility.

4. **Dealing with Duplicates**
   - Kept **column-level duplicates** (valid information).  
   - Removed **row-level duplicates** using `drop_duplicates()`.

---

## ✅ Final Cleaned Dataset
- All missing values handled with minimal information loss.  
- Structural issues (like `duration`) resolved by splitting into two separate columns.  
- Dataset is now **ready for analysis and visualization**.  

---

## 📈 Next Steps
- Perform exploratory data analysis (EDA).  
- Create meaningful visualizations (e.g., most common genres, content distribution by year, country analysis).  
- Build a dashboard in Power BI or Tableau for interactive insights.

---

## 🔑 Key Learnings
- Handling missing values without losing data.  
- Converting messy data into structured columns.  
- Importance of understanding duplicates (column vs row level).  
- How to make raw datasets usable for real-world analysis.

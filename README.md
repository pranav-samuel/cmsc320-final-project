# Movie Success Analysis: CMSC 320 Final Project

## Team Members

* Pranav Samuel
* Aarav Nirmal
* Manan Rajput

---

## Project Overview

What actually makes a movie successful?

In this project, we look into the factors that contribute to a film's success using real-world movie data. Because success can mean different things like high box office revenue, strong audience ratings, or overall popularity, we wanted to analyze multiple perspectives to get a more complete picture.

Using a combination of Kaggle datasets and a fresh pull from the TMDB API, we explored how elements like **budget, genre, popularity, crew composition, and audience ratings** influence a movie's performance. We started with classical hypothesis testing to validate (or reject) common industry beliefs, then trained two machine learning classifiers to predict whether a film would turn a profit using only pre-release information.

The full walkthrough lives in [`final_deliverable.ipynb`](final_deliverable.ipynb).

---

## Datasets

We use four datasets in total:

* **TMDB 5000 Movie Metadata** (Kaggle)
  Contains detailed information about movies like budget, revenue, genres, popularity, and ratings.

* **Worldwide Box Office Rankings, 1977 to present** (Kaggle)
  Provides global revenue rankings over time, allowing us to compare performance across different eras.

* **Consumer Price Index (CPI)**
  Used to adjust all financial figures for inflation so that revenue and budget numbers are comparable across decades.

* **TMDB API** (`api.themoviedb.org`)
  A fresh pull of 4,458 movies that we collected directly to fix a class imbalance issue we ran into during ML modeling.

These datasets complement each other by combining movie features that the others may not have.

---

## Hypothesis Testing

### **1.** **Production Efficiency (Chi-Square)**

##### **Type: Chi-Squared Test of Independence**
- We categorized movies into "High Budget" vs. "Low Budget" (using the median) and "Flop" vs. "Success" (Revenue < Budget vs. Revenue > Budget).
- This test answers the question, "Does spending more money statistically decrease your risk of failing, or are low-budget movies actually safer bets?"
- $H_0$: There is no association between budget size (High vs. Low) and financial outcome (Success vs. Flop). They are independent.
- $H_A$: There is a significant association between budget size and financial outcome.
- **Result:** $\chi^2 = 47.09$, $p = 6.78 \times 10^{-12}$. We reject $H_0$. High-budget films succeed at significantly higher rates than low-budget films.
- The plot we used is the Stacked Bar Chart.


### **2.** **Artistic Effects: Director-Writer Overlap**

##### **Type: Comparison of Means (Two-Sample t-test)**
- We created two groups: Group A (Movies where the Director is also a Writer) and Group B (Movies where they are different people). We then compared their Average Ratings.
- This test answers: "Does a singular idea lead to a statistically significant increase in movie quality, or is it better to have specialists?"
- $H_0$: The mean Average Rating for movies with a Director-Writer overlap is equal to the mean Average Rating for movies with separate specialists ($\mu_1 = \mu_2$).
- $H_A$: The mean Average Rating for movies with a Director-Writer overlap is significantly different from movies with separate specialists ($\mu_1 \neq \mu_2$).
- **Result:** Films with director-writer overlap show a small but statistically significant rating boost.
- The plot we used is the Box Plot with points.

### **3.** **Market Analysis: ANOVA (5 Genres vs. Box Office Revenue)**

##### **Type: Analysis of Variance (Multiple Group Comparison)**
- We take five distinct genre buckets (Energy, Suspenseful, Stylized, Emotional, and Lighthearted) and compare their Worldwide Revenue.
- This test answers: "Is there a premier genre that consistently outperforms the others, or is the financial difference between genres just a matter of chance?"
- $H_0$: The mean Worldwide Revenue is the same across all five genre groups ($\mu_{Energy} = \mu_{Suspenseful} = \mu_{Stylized} = \mu_{Emotional} = \mu_{Lighthearted}$).
- $H_A$: At least one genre group has a mean Worldwide Revenue that is significantly different from the others.
- **Result:** $p = 1.46 \times 10^{-60}$. We reject $H_0$. The Stylized and Energy genres significantly outperform the other categories.
- The plot we used is the Bar Chart with means.

---

## Machine Learning

After validating our hypotheses, we built a binary classification pipeline to predict whether a film would be a Success (revenue > budget) or a Flop, using only information available before release.

* **Models:** Logistic Regression (with StandardScaler) and Random Forest Classifier.
* **Features (22 total):** crew composition (crew_size, num_writers, num_producers, avg_crew_popularity), director track record from prior films only, writer popularity, director-writer overlap, five genre dummies, language, and release month.
* **Evaluation:** Stratified 80/20 train-test split, 5-fold cross-validation, classification reports, confusion matrices, and feature importance plots for both models.
* **Results:** Logistic Regression reached 72% accuracy and Random Forest reached 71% accuracy, with macro F1 scores of 0.67 and 0.65 respectively.

The most striking finding came from the feature importances: `crew_size`, `writer_popularity`, and `director_popularity` rank above raw `budget` as predictors. **Who** makes a film matters at least as much as **how much** is spent on it.

---

## Repository Structure

```
.
├── final_deliverable.ipynb   # Main tutorial notebook (start here)
├── checkpoint2.ipynb         # Earlier checkpoint submission
├── README.md                 # This file
└── data/
    ├── tmdb/                 # TMDB 5000 Movie Metadata
    ├── box_office/           # Worldwide box office rankings, 1977 onward
    ├── cpi/                  # Consumer Price Index for inflation adjustment
    └── final_data/           # Pre-pulled TMDB API dataset (committed for reproducibility)
```

---

## How to Run

1. Clone the repository.
2. Install the required Python packages: `pandas`, `numpy`, `matplotlib`, `scipy`, `scikit-learn`, `requests`, `python-dotenv`.
3. Open `final_deliverable.ipynb` in Jupyter or VS Code and run the cells top to bottom.

The notebook is fully reproducible without any external API key. The TMDB API pull cells are optional and the resulting CSV is already committed to `data/final_data/`.

---

# Movie Success Analysis — CMSC 320 Final Project

## Team Members

* Pranav Samuel
* Aarav Nirmal
* Manan Rajput

---

## Project Overview

What actually makes a movie successful?

In this project, we look into the factors that contribute to a film’s success using real-world movie data. Because success can mean different things like high box office revenue, strong audience ratings, or overall popularity, we want to analyze multiple perspectives to get a more complete picture.

Using datasets from Kaggle, we see how elements like **budget, genre, popularity, and audience ratings** influence a movie’s performance. Our goal is to identify patterns and relationships that help explain why some movies perform better than others.

---

## Datasets

We use two primary datasets:

* **TMDB 5000 Movie Metadata**
  Contains detailed information about movies like budget, revenue, genres, popularity, and ratings.

* **Worldwide Box Office Rankings (1977–present)**
  Provides global revenue rankings over time, allowing us to compare performance across different eras.

These datasets complement each other by combining movie features that the other may not have.

---

## Objectives

### **1.** **Production Efficiency (Chi-Square)**  

##### **Type: Chi-Squared Test of Independence**
- We will categorize movies into "High Budget" vs. "Low Budget" (using the median) and "Flop" vs. "Success" (Revenue < Budget vs. Revenue > Budget).
- This test answers the question, "Does spending more money statistically decrease your risk of failing, or are low-budget movies actually safer bets?"
- $H_0$: There is no association between budget size (High vs. Low) and financial outcome (Success vs. Flop). They are independent.
- $H_A$: There is a significant association between budget size and financial outcome. (e.g., High-budget movies are statistically more likely to be successes than low-budget movies).
- The plot we will use is the Stacked Bar Chart


### **2.** **Artistic Effects: Director-Writer Overlap**
    
##### **Type: Comparison of Means (Two-Sample t-test)**
- We will create two groups: Group A (Movies where the Director is also a Writer) and Group B (Movies where they are different people). We then compare their Average Ratings.
- This test answers: "Does a singular idea lead to a statistically significant increase in movie quality, or is it better to have specialists?"
- $H_0$: The mean Average Rating for movies with a Director-Writer overlap is equal to the mean Average Rating for movies with separate specialists ($\mu_1 = \mu_2$).
- $H_A$: The mean Average Rating for movies with a Director-Writer overlap is significantly different from movies with separate specialists ($\mu_1 \neq \mu_2$).
- The plot we will use is the Box Plot with points 

### **3.** **Market Analysis: ANOVA (5 Genres vs. Box Office Revenue)**

##### **Type: Analysis of Variance (Multiple Group Comparison)**
- We take the big three distinct genre buckets (Energy, Suspenseful, Stylized, Emotional, and Lighthearted) and compare their Worldwide Revenue.
- This test answers: "Is there a premier genre that consistently outperforms the others, or is the financial difference between genres just a matter of chance?"
- $H_0$: The mean Worldwide Revenue is the same across all five genre groups ($\mu_{Energy} = \mu_{Suspenseful} = \mu_{Stylized} = \mu_{Emotional} = \mu_{Lightheated}$).
- $H_A$: At least one genre group has a mean Worldwide Revenue that is significantly different from the others.
- The plot we will use is the Bar Chart with Error Bars
---

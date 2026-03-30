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

The main questions we aim to answer include:
1. Production Efficiency (Chi-Square)
  Type: Chi-Squared Test of Independence
  Process: We will categorize movies into "High Budget" vs. "Low Budget" (using the median) and "Flop" vs. "Success" (Revenue < Budget vs. Revenue > Budget).This test answers the question, "Does spending more money statistically decrease your risk of failing, or are low-budget movies actually safer bets?
2. Artistic Effects: Director-Writer Overlap 
  Type: Comparison of Means (Two-Sample t-test)
  Process: We will create two groups: Group A (Movies where the Director is also a Writer) and Group B (Movies where they are different people). We then compare their Average Ratings.This test answers: "Does a singular idea lead to a statistically significant increase in movie quality, or is it better to have specialists?"
3. Market Analysis: ANOVA (3 Genres vs. Box Office Revenue)
  Type: Analysis of Variance (Multiple Group Comparison)
  Process: We take the big three distinct genre buckets (e.g., Action, Comedy, and Drama) and compare their Worldwide Revenue.This test answers: "Is there a premier genre that consistently outperforms the others, or is the financial difference between genres just a matter of chance?
---

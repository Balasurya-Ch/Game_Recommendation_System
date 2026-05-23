<div align="center">

# Collaborative Filtering Recommendation Engine

### Personalization Systems · Machine Learning · Python Deployment

[![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Flask](https://img.shields.io/badge/Flask-000000?style=flat-square&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)]()

| | |
|---|---|
| **Domain** | ML Engineering · Personalization · Recommendation Systems |
| **Stack** | Python, scikit-learn, Flask, Jupyter |
| **Methods** | Collaborative Filtering, Content-Based Filtering, Hybrid Architecture |
| **Application** | Game recommendations — methodology transferable to product, content, inventory |

</div>

---

## The Business Problem

Catalog-based businesses — retail, streaming, gaming, content platforms — face a common operational problem: users who don't know exactly what they want will leave rather than search. A recommendation system solves this by surfacing relevant items proactively, based on what similar users chose or what the item itself shares with things the user already likes.

**The measurable outcomes:** Higher conversion rates. Higher average order value. Lower search friction. Higher retention. These are the numbers that recommendation systems move in production — which is why understanding how to build one is directly relevant to analytics roles in e-commerce, supply chain, and BI.

---

## Challenge

Two problems make recommendation system design non-trivial.

**Sparsity:** Most users have interacted with a tiny fraction of the available catalog. In a user-item preference matrix, the majority of cells are empty. Collaborative filtering degrades when the overlap between users is too sparse to find meaningful neighbors. Content-based filtering fills this gap but lacks the serendipity of collaborative methods.

**Cold start:** New users have no history. Pure collaborative filtering has nothing to work with. A hybrid architecture — collaborative filtering for users with history, content-based fallback for new users — is the standard solution, and the architecture this project implements.

---

## Action

**Data Preparation and Exploratory Analysis**
Game metadata and user rating data were loaded, cleaned, and profiled. Distributions of ratings, catalog coverage per user, and sparsity patterns were analyzed — directly informing the decision to build a hybrid rather than a pure collaborative system.

**Collaborative Filtering**
User-item preference similarity was computed to identify users with overlapping taste profiles. For any given input, the system finds the most similar users and recommends items they engaged with that the query user hasn't seen yet. This surfaces non-obvious, serendipitous suggestions that content similarity alone would miss.

**Content-Based Filtering**
Game attributes — genre, platform, rating categories — were encoded as feature vectors. Item-to-item cosine similarity enabled recommendations based on attribute overlap, providing reliable fallback coverage for new users and sparse catalog regions.

**Hybrid Pipeline and Flask Deployment**
The two approaches were combined in a hybrid pipeline: collaborative filtering as the primary method, content-based as fallback. The full pipeline was deployed via Flask as a browser-accessible web application — transforming the model from a Jupyter notebook into a usable tool.

---

## Result

| Capability | Detail |
|---|---|
| Primary method | Collaborative filtering (preference-based) |
| Fallback | Content-based filtering (cold start coverage) |
| Deployment | Flask web app (localhost:5000) |
| Input | Game title or user preference signal |
| Output | Ranked recommendation list |
| Cold start | Handled via content-based fallback |
| Business transferability | Direct — swap catalog for products, content, or inventory items |

**Why this project matters beyond gaming:** The user-item matrix is domain-agnostic. Product recommendation in retail, article recommendation in content platforms, supplier recommendation in procurement — all use the same fundamental architecture. Building and deploying this system demonstrates the ability to design and implement personalization infrastructure, not just consume it.

---

## Technical Architecture

```
Game Catalog + User Ratings Data
            |
            v
    EDA: Sparsity Analysis | Rating Distribution | Catalog Coverage
            |
      ______|______
     |             |
     v             v
Collaborative    Content-Based
Filtering        Filtering
(user-item       (item attribute
similarity)      similarity)
     |             |
     |_____________|
            |
            v
    Hybrid Recommendation Pipeline
    Collaborative primary | Content-based fallback
            |
            v
    Flask Web Application
    Input: preference | Output: ranked recommendations
```

**Repository structure:**
```
Game_Recommendation_System/
├── app.py                       Flask application
├── game_recommendation.ipynb    Model development and evaluation
├── requirements.txt             Dependency manifest
└── README.md
```

---

## Key Insights

The hybrid architecture is the decision that makes this system practical. Pure collaborative filtering fails in the cold start case — and cold start is not an edge case, it is the default state for every new user. Building in content-based fallback from the start means the system works on day one, not just after a user has accumulated enough history to generate meaningful collaborative matches.

The sparsity analysis during EDA directly shaped modeling decisions. Knowing the density of the user-item matrix before modeling informed the choice of similarity metric and the minimum interaction threshold for collaborative filtering — decisions that are invisible in the final output but critical to whether the recommendations are meaningful or arbitrary.

**The transferable takeaway for data analytics:** Recommendation systems are not just a consumer product feature. Demand forecasting, assortment optimization, supplier matching, and content personalization all rely on the same underlying logic — find the most relevant item for a context based on structured similarity. This project demonstrates that reasoning in a concrete, deployed form.

---

<div align="center">

**[Balasurya Chandana](https://linkedin.com/in/balasurya-chandana)** · Business & Data Analyst · [linkedin.com/in/balasurya-chandana](https://linkedin.com/in/balasurya-chandana)

</div>

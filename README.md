# Restaurant Recommendation System

## Project Overview

This project develops a personalized restaurant recommendation system using both collaborative and content-based filtering. The system helps users discover relevant stores, particularly by focusing on local options and stores with good reputations. With personalized recommendations, users can efficiently find stores that meet their unique preferences, enhancing user satisfaction and engagement.

## Importance of the Project

- **User Experience:** Recommendation systems are essential for personalizing the user experience, especially in e-commerce, where navigating through numerous options can be challenging.
- **Business Value:** Targeted recommendations boost user engagement, drive repeat purchases, and increase customer loyalty.

## Business Understanding

### Problem Statements

1. **Geographical Discovery:** Users face difficulties finding stores within the same city they live in.
2. **Reputation-Based Discovery:** Users struggle to find reputable stores that match their personal preferences.

### Project Goals

- **Content-Based Filtering:** Recommends stores in the user's city to facilitate local shopping experiences.
- **Collaborative Filtering:** Suggests stores with good reputations based on similar users' ratings, enhancing discovery of reputable stores.

## Data Understanding

The dataset used is the Brazilian E-commerce Dataset from Kaggle, containing information on orders, products, sellers, customers, and reviews. Key tables include:

- **Orders:** Information about orders, customer IDs, and order statuses.
- **Products:** Product IDs and categories.
- **Sellers:** Seller locations.
- **Reviews:** Ratings and comments.

## Data Preparation

1. **Data Cleaning:** Dropped irrelevant columns and removed rows with missing values.
2. **Merging Data:** Combined relevant tables to build a comprehensive dataset.
3. **Filtering Data:** Focused on sellers within Minas Gerais (MG) to refine the scope.
4. **Feature Extraction:** Encoded categorical variables and calculated city similarities for content-based filtering.

## Modeling

The recommendation system includes two main models:

### 1. Content-Based Filtering

- **Approach:** Uses TF-IDF to vectorize city names and cosine similarity to recommend stores in similar locations.
- **Strengths:** Good for local relevance; easy to interpret.
- **Weaknesses:** Limited feature diversity and scalability issues.

### 2. Collaborative Filtering

- **Approach:** A neural network-based collaborative filtering model using user and item embeddings.
- **Strengths:** Highly personalized recommendations.
- **Weaknesses:** Cold start problem and complexity in interpretation.

## Evaluation

- **Content-Based Filtering:** Precision metric; model precision = 0.00, indicating improvement potential.
- **Collaborative Filtering:** RMSE metric; achieved a training RMSE of 0.0743 and validation RMSE of 0.3349, suggesting effective generalization.

## Results and Impact on Business

1. **Geographical Discovery:** Content-Based Filtering helps users locate stores within their city.
2. **Reputation-Based Discovery:** Collaborative Filtering effectively recommends stores aligned with user preferences, irrespective of location.

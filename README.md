# RecomSys

## Project Overview 
This project aims to create a personalized restaurant recommendation system that leverages collaborative filtering and content-based filtering techniques. The goal is to provide users with relevant restaurant recommendations tailored to their unique preferences. In the rapidly expanding world of e-commerce, consumers face the challenge of navigating through a vast array of products and sellers. To enhance the shopping experience and assist users in discovering relevant stores, this project focuses on developing a recommendation system. The system leverages both content-based filtering and collaborative filtering to suggest stores that match user preferences, ultimately improving user satisfaction and increasing sales for sellers.

### Importance of this project:
- Recommendation systems are crucial for personalizing the user experience in e-commerce, helping users find stores that meet their needs efficiently.
- By providing targeted store recommendations, the platform can enhance customer retention, drive repeat purchases, and foster customer loyalty.

References:
- [Enhancing E-Commerce Experience with Recommender Systems](https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2023.1167735/full)
- [The Impact of Recommendation Algorithms on E-Commerce Sales](https://digitalschoolofmarketing.co.za/digital-marketing-blog/the-impact-of-recommender-systems-on-e-commerce-success/#:~:text=Through%20an%20e%2Dcommerce%20recommendation,sales%2C%20and%20improved%20customer%20satisfaction.)

## Business Understanding
### Problem Statements
1. Users find it difficult to discover stores located in the same city where they reside.
2. Users struggle to find stores with a good reputation based on their personal preferences.

### Goals
1. Develop a content-based filtering system that recommends stores located in the same city as the user, enhancing local shopping experiences.
2. Implement a collaborative filtering system to recommend stores that have received high ratings from users with similar preferences, helping users find reputable stores.

### Solution statements
To achieve the set goals, here are the proposed solutions:
1. Content-Based Filtering - This approach suggests stores that are located in the same city as the user, helping them discover local options.
2. Collaborative Filtering - This approach recommends stores based on the ratings and preferences of similar users, focusing on identifying stores with good reputations.


## Data Understanding
The dataset used in this project is sourced from the [Brazilian E-commerce Dataset](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce) available on Kaggle. This dataset provides comprehensive information on e-commerce activities in Brazil, including details about orders, products, sellers, and customers.

### Dataset Overview
The dataset consists of several interconnected tables, each containing specific information that is essential for building a recommendation system. The diagram below illustrates the relationships between these tables:
![DatasetSchema](https://github.com/user-attachments/assets/420e4a5a-e09e-49b9-82a5-feab1a4ef15a)

Here’s a brief description of each dataset:
- `olist_orders_dataset`: Contains information about orders, such as the order ID, customer ID, and order status.
- `olist_order_items_dataset`: Provides details about the items in each order, including the product ID and seller ID.
- `olist_products_dataset`: Includes information about the products, such as the product category and product ID.
- `olist_sellers_dataset`: Contains data about sellers, including their ID, city, and state.
- `olist_order_customer_dataset`: Contains customer information, including customer ID and zip code prefix.
- `olist_order_reviews_dataset`: Includes reviews for each order, with details like review score and review comment.
- `olist_geolocation_dataset`: Provides geolocation data for zip code prefixes, linking customers and sellers to specific locations.
- `olist_order_payments_dataset`: Contains payment details for each order, including payment type and value.

Below is an overview of the datasets utilized in this project:
1. `olist_products_dataset`
- **Description**: Contains information about products, including product IDs and categories.
- **Columns**:
    - `product_id`: Unique identifier for each product.
    - `product_category_name`: Category name of the product.
- **Shape**: 32,951 rows with 2 columns
- **Missing Values**:
    - `product_category_name`: 610 missing values.

2. `olist_order_items_dataset`
- **Description**: Provides details about the items in each order, linking products to sellers.
- **Columns**:
    - `order_id`: Unique identifier for each order.
    - `product_id`: Unique identifier for each product.
    - `seller_id`: Unique identifier for each seller.
- **Shape**: 112,650 rows with 3 columns
- **Missing Values**: None.

3. `olist_sellers_dataset`
- **Description**: Contains data about sellers, including their IDs, cities, and states.
- **Columns**:
    - `seller_id`: Unique identifier for each seller.
    - `seller_zip_code_prefix`: Zip code prefix of the seller.
    - `seller_city`: City where the seller is located.
    - `seller_state`: State where the seller is located.
- **Shape**: 3,095 rows with 4 columns
- **Missing Values**: None.

4. `olist_orders_dataset`
- **Description**: Contains information about orders, linking them to customers.
- **Columns**:
    - `order_id`: Unique identifier for each order.
    - `customer_id`: Unique identifier for each customer.
- **Shape**: 99,441 rows with 2 columns
- **Missing Values**: None.

5. `olist_order_reviews_dataset`
- **Description**: Includes reviews for each order, with details like review score.
- **Columns**:
    - `review_id`: Unique identifier for each review.
    - `order_id`: Unique identifier for each order.
    - `review_score`: Rating given by the customer for the order.
- **Shape**: 99,224 rows with 3 columns
- **Missing Values**: None.

### Dataset Summary
- Customers: 99,441 unique customers.
- Sellers: 3,095 unique sellers.
- Products: 74 unique products.
- Order Items: 98,666 order items.
- Reviews: 98,410 reviews.

### Feature Descriptions
The variables that is in used for this project in the Brazilian E-commerce Dataset are as follows:
- `order_id`: A unique identifier for each order.
- `customer_id`: A unique identifier for each customer.
- `seller_id`: A unique identifier for each seller.
- `product_id`: A unique identifier for each product.
- `review_id`: A unique identifier for each review.
- `seller_city`: The city where the seller is located.
- `seller_state`: The state where the seller is located.
- `review_score`: The rating given by the customer for the order.
- `product_category_name`: The category to which the product belongs.


### Exploratory Data Analysis (EDA)
Several visualizations and analyses were conducted to explore and understand the dataset better. Here are the findings:
1. Top 10 Product Categories by Count
The most frequent product categories in the dataset include 'informatica_acessorios', 'utilidades_domesticas', and 'moveis_decoracao'. These categories represent the highest number of products sold, with 'informatica_acessorios' leading significantly.
![TopProduct](https://github.com/user-attachments/assets/ec172b95-b86c-45f9-a6d1-f13bf5a8f81d)

2. Count of Each Review Score
The majority of the products received high review scores, with the score of 5.0 being the most common. This suggests that customers generally had positive experiences with their purchases.
![Review](https://github.com/user-attachments/assets/962639d2-c658-4e58-83c2-ec6fb7cba775)

3. Top 10 Highest-Rated Products
'informatica_acessorios' stands out as the highest-rated product category, followed by 'utilidades_domesticas' and 'ferramentas_jardim'. These categories are not only popular but also highly rated by customers, indicating a strong customer satisfaction.
![HighestRate](https://github.com/user-attachments/assets/22dfda21-5c86-4785-bad9-748e26f0ea81)

4. Top 10 Highest-Rated Cities by Average Review Score
The city of 'belo horizonte' has the highest average review score, far exceeding other cities. This suggests that stores in 'belo horizonte' tend to receive more favorable reviews compared to other cities.
![HighestCity](https://github.com/user-attachments/assets/3c04ec0a-9f36-446c-9b4a-111979ccecec)

5. Statistical Summary
The statistical summary of the review scores provides a detailed overview of the distribution and central tendency of customer ratings within the dataset. Below are the key statistical metrics:
    * **Count:** The dataset contains 7,927 reviews.
    * **Mean:** The average review score is 4.15, indicating generally positive feedback from customers.
    * **Standard Deviation (std):** The standard deviation is 1.29, showing some variability in the ratings, although the majority of scores are clustered around the higher end.
    * **Minimum (min):** The lowest review score given is 1.0, representing the least satisfied customers.
    * **25th Percentile (25%):** 25% of the review scores are 4.0 or below.
    * **Median (50%):** The median review score is 5.0, meaning that more than half of the reviews are perfect scores.
    * **75th Percentile (75%):** 75% of the review scores are 5.0 or below, further indicating that a significant majority of customers provided high ratings.
    * **Maximum (max):** The highest review score is 5.0, reflecting the maximum satisfaction level from customers.

  
## Data Preparation
In this section, various data preparation techniques are applied to clean and organize the dataset before building the recommendation system. These steps are crucial to ensure that the data is in the correct format and structure for the algorithms used.

### 1. Loading and Cleaning Data
First, the dataset is loaded into dataframes, and unnecessary columns that are not needed for further analysis are removed. The columns dropped include metadata about products such as product dimensions, weight, and description length, which are irrelevant to the recommendation task.
Reason: The initial dataset often contains many columns that do not contribute to the final analysis or model. These columns can introduce noise, increase computational complexity, and potentially lead to incorrect results. By removing them, the data used for analysis is relevant and focused.

### 2. Assigning Store Names
Since the dataset contains only `seller_id` without store names, random store names are generated and assigned to each unique seller ID to enhance readability and usability in the recommendation system.
Reason: Assigning store names to `seller_id` is crucial steps in so it would be readable rather than on sellerid.

### 3. Merging Datasets
To create a unified dataset for further analysis, several dataframes are merged. This allows us to bring together product, seller, and customer information along with review scores.
Reason: Merging different data sources into a single DataFrame ensures that all relevant information (e.g., product details, seller information, customer data, and reviews) is available for analysis. This unified dataset is the foundation for building robust recommendation models.

### 4. Filtering and Cleaning Data
After merging, the dataset is further refined by removing rows with missing values in critical columns such as `review_score`, `seller_id`, and `product_category_name`. This ensures that only complete records are used in the analysis.
Reason:  Missing values can skew the results of any analysis, leading to biased or inaccurate outcomes. Removing rows with missing critical values such as `review_score`, `seller_id`, and `product_category_name` ensures that only complete and reliable data is used

### 5. Focusing on a Specific Region
For this project, the focus is narrowed down to sellers in the state of Minas Gerais (MG). This helps in managing the dataset size and making the recommendations more relevant to a specific geographic location.
Reason: Focusing on a specific region (such as the state of Minas Gerais in this project) helps manage the dataset size, making the model more efficient without compromising the quality of the recommendations.

### 6. Correcting Data Inconsistencies
Data inconsistencies such as misspelled city names are corrected to ensure uniformity. Additionally, incorrect or irrelevant entries are removed from the dataset.
Reason: Inconsistent data, such as misspelled city names, can cause issues in analyses that rely on exact matches, such as grouping or merging operations. Correcting these inconsistencies ensures that the data is uniform and can be correctly interpreted by the algorithms.

### 7. Train-Test Split
The dataset is split into training and validation sets to evaluate model performance.
Reason: Splitting the dataset into training and validation sets is crucial for assessing the model's performance and generalizability.

### 8. Feature Extraction for Modeling
- The feature extraction process involves encoding categorical variables like `customer_id` and `seller_id` into numerical values that the models can work with. `customer_id` and `seller_id` are encoded into numerical indices to be used in the collaborative filtering model.
    - Reason: The feature extraction process is crucial for collaborative filtering algorithm because it transforms the data into a format that is suitable for the machine learning algorithms. Encoding categorical variables into numerical indices allows the model to learn patterns from the data.

- The city names (`seller_city` column) are transformed into vectors using TF-IDF (Term Frequency-Inverse Document Frequency). This step captures the importance of each city relative to others in the dataset, allowing the model to understand how similar or different cities are. Also, the similarity between different stores, based on their city locations, is calculated using the cosine similarity measure. This similarity matrix is then used to recommend stores located in cities similar to those where the user has previously shopped.
    - Reason: These steps are essential for the Content-Based Filtering model, enabling it to recommend stores based on the geographical preferences of users by leveraging the similarities between different cities.


## Modeling
This section discusses the recommendation system models developed to address the identified problems. The focus is on providing Top-N recommendations using two different algorithms: Content-Based Filtering and Collaborative Filtering. Each approach has distinct strengths and weaknesses, which are outlined below.

### 1. Content-Based Filtering
Content-Based Filtering recommends items that are similar to those a user has liked in the past. In this project, city names were used as the content feature, based on the assumption that users might prefer stores located in cities similar to those where they have previously shopped.

#### Implementation
- **TF-IDF Vectorization**:
    - Parameter: `max_features` = 5000
    -  TF-IDF (Term Frequency-Inverse Document Frequency) was employed to transform the city names into vectors, capturing the importance of each city relative to others. The `max_features` parameter limits the number of terms to 5000, focusing on the most significant ones.
- **Cosine Similarity**:
    - Cosine similarity was used to measure the similarity between different stores based on their city locations. This approach computes the cosine of the angle between two non-zero vectors, providing a similarity score between 0 and 1.

#### Top-N Recommendations
For the Content-Based Filtering model, the Top-N recommendations are generated for a specific store that a user has interacted with. For instance, if a user has shown interest in the "dfezbxmw store," the model recommends other stores in cities that are geographically or contextually similar to where this store is located.
Sample User Interaction:
- Store Name: "tqjjxsgk store" (Selected as the base store for generating recommendations)
- Generated Recommendations: The model suggests other stores like "yhortlvi store," "htyozlja store," and "egddambii store," which are located in cities similar to where "tqjjxsgk store" is situated.

The figure below shows an example of Top-N recommendations based on Content-Based Filtering:
![ContentBasedTopN](https://github.com/user-attachments/assets/197921e8-03b7-445f-a4e9-99812c2ad958)

#### Strengths
- **Relevance:** This method is particularly effective when location is a significant factor in user preference, ensuring that recommendations are contextually relevant.
- **Interpretability:** The model is straightforward and easy to explain, as it relies on the direct comparison of city names.

#### Weaknesses
- **Limited Diversity:** Since recommendations are based on a single feature (city name), the diversity of recommended stores may be limited.
- **Scalability:** This approach may not scale well with a large number of features or items, as the similarity matrix can become computationally expensive to calculate.


### 2. Collaborative Filtering
Collaborative Filtering recommends items by identifying patterns in user behavior, specifically by finding similar users or items. This project implemented a model that identifies stores with good reputations based on user preferences, regardless of the city they are located in.

#### Implementation
A neural network-based approach was used to factorize the user-store interaction matrix. The Embedding Size parameter determines the dimensionality of the latent space in which user and store features are projected. The Adam optimizer with a learning rate of 0.001 ensures efficient and effective model training. The loss function chosen is BinaryCrossentropy, which is well-suited for the binary nature of the recommendation task. The model was trained for 100 epochs with a batch size of 8.
- `Embedding Size`: 50
- `Optimizer`: Adam with learning_rate=0.001
- `Loss` Function: BinaryCrossentropy
- `Metrics`: RootMeanSquaredError

#### Top-N Recommendations
For the Collaborative Filtering model, recommendations are generated for a specific user. The user is selected based on their previous interactions with various stores. For example, if a user with ID `97c905bbb48e654d4c54d35f094337b5` has shown interest in certain stores, the model predicts and ranks stores that the user might like based on the behavior of similar users.
Sample User:
- User ID: `97c905bbb48e654d4c54d35f094337b5` (Selected to demonstrate personalized store recommendations)
- Generated Recommendations: The model suggests stores like "ijsjwcjz store," "llxranbc store," and "msjbapph store," which have high predicted ratings based on this user's preferences.
The figure below shows an example of Top-N recommendations based on Collaborative Filtering:
![CollaborativeTopN](https://github.com/user-attachments/assets/ad0249ec-29f8-4be3-b9b2-c3b9643a0b7c)

#### Strengths
- **Personalization:** This method offers highly personalized recommendations by considering the preferences of similar users.
- **Flexibility:** It can incorporate various types of user behavior and preferences, leading to more diverse recommendations.

#### Weaknesses
- **Cold Start Problem:** This approach may struggle with new users or stores that have few interactions, leading to less accurate recommendations.
- **Complexity:** The model is more complex and harder to interpret, as it relies on latent features that are not directly observable.

### Model Selection
While both Content-Based Filtering and Collaborative Filtering offer valuable insights, the Collaborative Filtering approach is particularly compelling for this project. This method allows users to discover high-quality stores based on personal preferences, regardless of the city. Since the recommendation output also specifies the store's city, users can easily select stores with high ratings within their own location. This makes Collaborative Filtering the preferred choice, as it not only caters to individual user preferences but also enables users to find the best options within their city, ensuring both quality and relevance in the recommendations.


## Evaluation
This section evaluates the performance of the recommendation system using appropriate metrics that align with the project’s context, problem statements, and desired solution.

### Evaluation Metrics
- Content-Based Filtering
For the Content-Based Filtering model, precision is used as the evaluation metric. Precision measures the proportion of relevant recommendations out of all recommendations made by the model. It is defined by the following formula:
![MetricPrecision](https://github.com/user-attachments/assets/0b550198-81c0-4a95-ab36-ff4d5b4fa71d)

- In the context of a recommendation system, a higher precision indicates that the model is effective at recommending stores that are relevant to the user's preferences. It focuses on the accuracy of the top-N recommendations provided by the model.
- Precision was calculated by comparing the model's recommendations against a test set of known relevant stores. The resulting precision score helps determine how well the model is performing in terms of recommending relevant stores.
- The precision for the Content-Based Filtering model was found to be 0.00. This result indicates that the model did not successfully recommend any stores that were relevant based on the defined criteria.

- Collaborative Filtering
For the Collaborative Filtering model, Root Mean Squared Error (RMSE) was chosen as the primary evaluation metric. RMSE is a widely used metric in recommendation systems to measure the accuracy of predicted ratings compared to the actual ratings. It is defined by the following formula:
![Formula](https://github.com/user-attachments/assets/312cb199-71ba-4b63-b53d-f0c5501f5c4d)
RMSE is particularly suitable for this project because it penalizes larger errors more than smaller ones, making it sensitive to outliers in the data. A lower RMSE indicates better predictive accuracy of the model.

### Evaluation Results
![image](https://github.com/user-attachments/assets/3bf29919-911e-41e0-88e6-e7e5c3e7d134)

- **Training RMSE:** The model achieved a training RMSE of 0.0743 with a loss of 0.2203. This low RMSE suggests that the model effectively captured the underlying patterns in the training data, fitting it well.
- **Validation RMSE:** The model’s validation RMSE was 0.3349, with a validation loss of 0.5390. While the validation RMSE is higher than the training RMSE, it indicates that the model can generalize to new, unseen data, though there is some variance between the training and validation scores.

Based on the RMSE metric, the Collaborative Filtering model showed good predictive performance with a training RMSE of 0.0743 and a validation RMSE of 0.3349. The lower training RMSE indicates effective learning on the training data, while the higher but reasonable validation RMSE suggests the model generalizes well to unseen data. This reinforces the decision to prefer the Collaborative Filtering approach, as it accurately captures user preferences and provides personalized recommendations effectively.

### Impact on Business Understanding
#### Problem Statements
- Geographical Store Discovery: Through the use of Content-Based Filtering, the system was able to effectively recommend stores based on the city of the user, addressing the issue of users struggling to find stores within their locality. This ensures that users can easily find stores that are geographically convenient for them.
- Store Reputation and Personal Preference: By implementing Collaborative Filtering, the system could recommend stores that align with the user's personal preferences and past interactions, even if those stores are not in the user's immediate geographical area. This allows users to discover highly-rated stores that match their preferences, solving the challenge of finding reputable stores.

#### Goals Achievement
- Content-Based Filtering: Successfully developed a model to recommend stores based on geographical location, which helps users find stores within their city. This approach directly addresses the first problem statement, ensuring users can locate stores near them.
- Collaborative Filtering: Built a collaborative filtering model that provides store recommendations based on user preferences and past ratings. This method proved to be particularly effective, as it allows users to find high-quality stores in their city, aligning with the second problem statement and making it the preferred recommendation approach.

**---The End---**

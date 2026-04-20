# Scenario: Promotion Effectiveness at a Fashion Retail Chain

A fashion retailer operates 50 stores across urban, semi-urban, and rural locations. Each month, the marketing team runs one of five promotions: Flat Discount, BOGO (Buy-One-Get-One), Free Gift with Purchase, Category-Specific Offer, and Loyalty Points Bonus. Stores vary in size, monthly footfall, local competition density, and customer demographics. The company wants to determine which promotion should be deployed in each store each month to maximise the number of items sold.

# B1. Problem Formulation

## (a) Machine Learning Problem Formulation

This business problem can be formulated as a **supervised machine learning regression problem**.

* **Target Variable:**
  `items_sold` — the number of items sold in a store during a specific promotion period.

* **Input Features:**

  * Store attributes: `store_size`, `location_type`, `competition_density`
  * Promotion-related features: `promotion_type`
  * Temporal features: `month`, `day_of_week`, `is_weekend`, `is_festival`
  * Other behavioral indicators (if available): `footfall`, past sales trends

* **Type of Problem:**
  This is a **regression problem** because the target variable is continuous and numerical.

* **Justification:**
  The goal is to estimate the number of items sold under different promotional and store conditions. Since the output is a numeric value rather than a category, regression models are the most appropriate choice.

---

## (b) Why Items Sold is Better than Revenue

Using **items_sold (sales volume)** as the target variable is more reliable than using total revenue for the following reasons:

* Revenue can be heavily influenced by **price changes, discounts, and promotion strategies**, which may distort the actual effectiveness of a promotion.

* Items sold directly reflects **customer demand and response**, making it a more consistent and unbiased measure.

* Some promotions (such as heavy discounts) may increase the number of items sold but reduce revenue per item, leading to misleading conclusions if revenue is used as the target.

* **Broader Principle:**
  This highlights an important principle in machine learning:
  **The target variable must align closely with the actual business objective.**
  Choosing the wrong target can lead to incorrect insights and poor business decisions, even if the model performs well technically.

---

## (c) Alternative Modelling Strategy

Instead of using a single global model across all 50 stores, a more effective approach is to use a **segmented or hierarchical modelling strategy**.

* **Proposed Approach:**

  * Segment stores based on `location_type` (urban, semi-urban, rural) and/or other characteristics
  * Train separate models for each segment
    **OR**
  * Use clustering techniques to group similar stores and build models for each cluster

* **Justification:**

  * Customer behavior, purchasing power, and competition vary significantly across locations
  * The same promotion may perform differently in different store types
  * A single global model may fail to capture these variations and reduce prediction accuracy

* **Benefits:**

  * Improved model performance
  * More personalized promotion strategies
  * Better business decision-making at the store level

---

### Conclusion

By framing this as a regression problem, selecting the correct target variable, and adopting a segmented modelling approach, the retailer can significantly improve the effectiveness of its promotional strategies and maximize overall sales performance.




# B2. Data and EDA Strategy

## (a) Data Joining and Dataset Design

The raw data is available in four separate tables: transactions, store attributes, promotion details, and calendar.

* **Joining Strategy:**

  * Use `store_id` to join **transactions** with **store attributes**
  * Use `promotion_type` (or promotion ID) to join with **promotion details**
  * Use `transaction_date` to join with the **calendar table** (to get weekend and festival flags)

* **Grain of Final Dataset:**

  * The final dataset should have **one row per store per day per promotion**
  * This ensures that each row represents a unique business scenario for prediction

* **Aggregations:**
  Before modelling, the following aggregations should be performed:

  * Total `items_sold` per store per day
  * Average `basket_size` or transaction value
  * Total number of transactions (proxy for footfall)
  * Count or presence of promotions applied

These aggregations help convert raw transactional data into meaningful features for modelling.

---

## (b) Exploratory Data Analysis (EDA)

Before building the model, the following EDA steps should be performed:

1. **Target Distribution (Histogram of items_sold):**

   * Check if the target variable is skewed or normally distributed
   * If highly skewed, consider transformations (e.g., log transformation)

2. **Promotion-wise Performance (Bar Plot):**

   * Compare average `items_sold` across different promotion types
   * Helps identify which promotions are generally more effective

3. **Correlation Heatmap:**

   * Analyze relationships between numerical features
   * Detect multicollinearity and identify strong predictors of sales

4. **Time-based Trends (Line Plot):**

   * Plot `items_sold` over time (daily/weekly)
   * Identify seasonality, trends, and festival spikes

5. **Boxplots by Store Type or Location:**

   * Compare sales distribution across urban, semi-urban, and rural stores
   * Helps understand how location impacts performance

* **Impact on Modelling:**

  * Skewed data → apply transformations
  * Strong correlations → feature selection or dimensionality reduction
  * Seasonal trends → include time-based features
  * Store differences → consider segmented models

---

## (c) Handling Promotion Imbalance

Since 80% of transactions occur without any promotion, the dataset is highly imbalanced.

* **Impact on Model:**

  * The model may become biased toward the "no promotion" scenario
  * It may fail to learn the true impact of different promotions
  * Predictions for promotional scenarios may be less accurate

* **Steps to Address This:**

  * Use **resampling techniques** (oversample promotion cases or undersample non-promotion cases)
  * Apply **feature weighting** or include a strong `promotion_type` signal
  * Evaluate model performance separately for promotional vs non-promotional data
  * Consider building separate models for promotion and non-promotion scenarios

This ensures that the model learns meaningful patterns for all promotion types.


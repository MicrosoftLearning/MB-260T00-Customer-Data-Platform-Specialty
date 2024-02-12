---
lab:
    title: 'Lab 5.2: Predictions'
    module: 'Module 5: Enrich data and predictions with Customer Insights - Data'
---

# Lab 5.2: Predictions
# Module 5: Enrich data and predictions with Customer Insights - Data

Customer Insights offers out of the box models to predict key insights of your business. Transactional churn prediction helps predict if a customer will no longer purchase your products or services in a given time window.

## Objectives

- Use OOB Transaction Churn model to predict customers at risk of churn after a period of time with no purchases.

- Create a segment based on the Intelligence Prediction. 


# Exercise 1 - Transaction Churn Model

## Task 1 - Run the OOB Transactional Churn Model 

1.  If you haven't already, sign into Customer Insights - Data at `https://home.ci.ai.dynamics.com`

2.  Navigate to **Insights** > **Predictions** from the left navigation menu. 

3.  Select the **Create** tab and select **Use this model** on the **Customer churn model** card. 

4.  Select the **Transaction** option and select **Get started**. 

5.  Name the model `OOB eCommerce Transaction Churn Prediction` and verify the **Output entity name** is set to **OOBeCommerceTransactionChurnPrediction**, then select **Next**. 

6.  Define both conditions for the churn model as **60 days**, then select **Next**. 

7.  Under **Customer transaction history**, select **+ Add data**. Select **SalesOrder** as the activity type and then select the **Purchases : eCommerce** entity. Select **Next** and then **Save**. 

8.  Select **Next** to move to the **Additional data (optional)** screen and then select **Next** again. 

9.  On the **Data update schedule** screen select the **Monthly** update setting and select **Next**. 

10. On the **Review** screeen, select **Save and run** and select **Done**. 

    > **Note:** This process may take up to 30 minutes to complete.

11. Monitor the run status, and once the run has succeeded, select the created prediction to see the results. You can find the list of customers and their churn score under **Data** > **Entities** > **Intelligence** > **OOBeCommerceTransactionChurnPrediction**. 

12. Return to **Intelligence > Predictions**. Select the vertical ellipsis (...) menu from your churn model and select **View**. Explore the Training model performance, likelihood to churn chart, and most influential factors. 


### Training Model Performance

The model is graded A, B or C depending on the following conditions: 

- **A** when the model accurately predicted at least 50% of the total predictions, and when the percentage of accurate predictions for customers who churned is greater than the historical average churn rate by at least 10% of the historical average churn rate. 

- **B** when the model accurately predicted at least 50% of the total predictions, and when the percentage of accurate predictions for customers who churned is up to 10% greater than the historical average churn rate of the historical average churn rate. 

- **C** when the model accurately predicted less 50% of the total predictions, or when the percentage of accurate predictions for customers who churned is less than the historical average churn rate. 

### Likelihood to churn (number of customers)

Likelihood of churn shows Groups of customers based on their predicted risk of churn. This data can help you later if you want to create a segment of customers with high churn risk. Such segments help to understand where your cutoff should be for segment membership. 

### Most Influential Factors

There are many factors that are taken into account when creating your prediction. Each of the factors has their importance calculated for the aggregated predictions a model creates. You can use these factors to help validate your prediction results. Or you can use this information later to create segments that could help influence churn risk for customers. 


## Task 2 - Create a Segment of High Churn-Risk Customers

1.  Return to the homepage, `https://home.ci.ai.dynamics.com/`

2.  Go to **Segments**. Select **+ New** and choose **Create from Intelligence**. 

3.  Select the **OOBeCommerceTransactionChurnPrediction** entity: 

    - Field: **ChurnScore** 

    - Operator: **greater than** 

    - Value: `0.6` 

4.  Select **Review**. 

5.  Name the segment `High Risk Transaction Churn`, verify the **Output entity name** is set to **HighRiskTransactionChurn**, and select **Save**. 

6.  **Wait** for the Segment to refresh. 

You now have a segment that is dynamically updated which identifies high churn-risk customers for this transactional business. 


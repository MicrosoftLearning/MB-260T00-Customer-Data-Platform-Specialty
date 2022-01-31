# Module Introduction

## Out of the Box (OOB) models

Customer Insights offers out of the box models to predict key insights of your business. Currently, Customer Insights provides Subscription Churn model that can predict whether your customers are at risk of not using your company's subscription products or services. Many more OOB models to follow.

## Objectives

- Use OOB Subscription Churn model to predict customers at risk of not using Contoso subscription service.

- Create a quick segment using Intelligence.

## Prerequisites

To complete the Customer Insights in a Day course you will need the following

- **Dynamics 365 Marketing** Instance or Trial

- Access to **Power Apps** or a Power Apps Trial

- Access to **Power Automate** or a Power Automate Trial

- Access to **Power BI** or a Power BI Trial

- **Customer Insights** Trial

If you do not have access to the above, you can follow Lab 3 to get setup.

## Approximate Time - 45 mins



# Exercise 1 - Transaction Churn Model

## Task 1 - Run the OOB Transactional Churn Model

1. Go to **Intelligence** > **Predictions**

2. Click **Create** and click **Use model** on the **Customer Churn model** card

	![Picture 264](Static/Lab_4C_Intelligence_image1.jpeg)

3. Select the **Transactional** option and click **Get started**

4. Name the model **OOB eCommerce Transaction Churn Prediction** and the output entity **OOBeCommerceTransactionChurnPrediction** then click **Next**

5. Define the two conditions for the churn model as both **60 days** then click **Next**

	![Picture 266](Static/Lab_4C_Intelligence_image2.jpeg)

6. Under Purchase logs, click **Add data** and select the **Purchases : eCommerce** entity from the **Purchase history entity** list and map the fields as below, then click **Next**

	![Picture 381](Static/Lab_4C_Intelligence_image3.jpeg)

	- Transaction ID: **PurchaseId**

	- Transaction Date: **PurchasedOn**

	- Value of Transaction: **TotalPrice**

	- Unique product ID: **ProductId**

7. Click **Next**

8. The relationship should be setup for you, and you can just click **Save**. If it is not the **Corresponding label** for the **Entity** is **ContactId**. The **Customer Entity** is **Contacts : eCommerce**

9. Click **Next** to move to the **Additional Data** screen, then click **Next** again as we need no setup here

10. On the **Data update schedule** screen select the **Monthly** update setting and click **Next**

11. On the review step click **Save and run** when it completes click **Done**

12. Monitor the run status, and once the run has succeeded, click on the created prediction to see the results. You can find the list of customers and their churn score under **Data** > **Entities** > **ChurnModel**

	![Picture 379](Static/Lab_4C_Intelligence_image4.jpeg)

	![Picture 379](Static/Lab_4C_Intelligence_image4-2.jpeg)

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

1. Go to **Segments**. Select **New** and choose **Create from** > **Intelligence**

	![Picture 524](Static/Lab_4C_Intelligence_image5.jpeg)

2. Select the **OOBeCommerceTransactionChurnPrediction** entity:

	- Field: **ChurnScore**

	- Operator: **greater than**

	- Value: **0.6**

3. Name your segment **High Risk Transaction Churn** and set the Output entity name to **HighRiskTransactionChurn** then click **Save**

4. Refresh the segment to run it

You now have a segment that is dynamically updated which identifies high churn-risk customers for this subscription business.



# Optional - Building OOB Subscription Churn Model

## Task 1 - Ingest the Subscription Data

1. Click **Add Data Source**, then choose from the available methods of ingesting data. Currently, CI provides import data via various data connectors, connect to your own data lake, connect to Common Data Service. For this lab, choose **Import data** and name the source **SubscriptionData**, then click **Next button**

	![Picture 637](Static/Lab_4C_Intelligence_image5-2.jpeg)

	![Picture 637](Static/Lab_4C_Intelligence_image5-3.jpeg)

2. You will be presented with a view of data source connectors that Customer Insights is able to ingest. Take note of the connector types available, including *Common Data Service for Apps*. Select the **Text/CSV** Connector

	![Picture 637](Static/Lab_4C_Intelligence_image6.jpeg)

3. Enter the URL for the Subscribers data set, **https://aka.ms/CI-ILT/SubscriberContacts**, and click **Next**

	![Picture 681](Static/Lab_4C_Intelligence_image7.jpeg)

4. You should now see the data from the source tabulated. Click **Transform data** to configure the datatypes and formats for the data you ingest

	![Picture 683](Static/Lab_4C_Intelligence_image8.jpeg)

5. You will notice that the column heading has appeared in the first row of the data. To correct this, click **Transform** and **Use first row as headers**

	![Picture 685](Static/Lab_4C_Intelligence_image9.jpeg)

6. In the 'Name' field on the right-hand pane, rename your data source from **Query** to **Subscribers**

	![Picture 685](Static/Lab_4C_Intelligence_image9-2.jpeg)

7. Click **Get Data**, then choose **Text/CSV**

	![Picture 685](Static/Lab_4C_Intelligence_image9-3.jpeg)

8. Enter the URL for the Subscriber History data set, **https://aka.ms/CI-ILT/SubHistory**, and click **Next**

9. You should now see the data from the source tabulated. Click **Create** to configure the datatypes and formats for the data you ingest

10. You will notice that the column heading has appeared in the first row of the data. To correct this, click **Transform** and **Use first row as headers**

11. Because we have ingested data from a Text/CSV source, all columns have been defaulted to a 'Text' Data Type. To successfully ingest and model the data, we can set the datatype for non-text columns

	To change the datatype, click the **ABC** icon within the column heading. Update the datatype for the columns listed below.

	| Column Heading | New Data Type |
	| - | - |
	| SubscriptionAmount | Whole Number |
	| SubscriptionEndDate | DateTime |
	| SubscriptioStartDate | DateTime |
	| TransactionDate | DateTime |
	| IsRecurring | True/False |
	| Is_auto_renew | True/False |
	| RecurringFrequencyInMonths | Whole Number |

	![Picture 902](Static/Lab_4C_Intelligence_image10.jpeg)

12. In the 'Name' field on the right-hand pane, rename your data source from **Query** to **SubscriberHistory**

13. Click **Get Data**, then choose **Text/CSV**

	![Picture 902](Static/Lab_4C_Intelligence_image10-2.jpeg)

14. Enter the URL for the Userlog data set, **https://aka.ms/CI-ILT/Userlogs**, and click **Next**

15. You should now see the data from the source tabulated. Click **Create** to configure the datatypes and formats for the data you ingest

16. You will notice that the column heading has appeared in the first row of the data. To correct this, click **Transform** and **Use first row as headers**

17. Because we have ingested data from a Text/CSV source, all columns have been defaulted to a 'Text' Data Type. To successfully ingest and model the data, we can set the datatype for non-text columns

	To change the datatype, click the **ABC** icon within the column heading. Update the datatype for the columns listed below.

	| Column Heading | New Data Type |
	| - | - |
	| TransactionDate | DateTime |
	| TransactionValue | Whole Number |

	![Picture 1003](Static/Lab_4C_Intelligence_image11.jpeg)

18. In the 'Name' field on the right-hand pane, rename your data source from **Query** to **UserLogs**

19. Leave the refresh schedule set to **Manual** and click **Save**

## Task 2 - Unify the Subscription Data with Existing Data

When the data source is finishes loading we need to go through the Unify process. This can take a while as there is a lot of data in the SubscriptonData tables you are importing. The import can also fail if there are network issues because of the large data set as well.

1. Click on **Data** > **Unify** in the left-hand menu

2. Click on **Edit Fields** and check **Subscribers (SubscriptionData)**, then press **Apply**

	![Picture 1003](Static/Lab_4C_Intelligence_image11-2.jpeg)

3. Click on **SubscriptionData Subscribers** in the entities list and select **ContactId** for the Primary Key

4. Click **Save**. Click on the **Match** tab

5. Click the **Edit** button on the **Matched customer records** heading

	![Picture 1003](Static/Lab_4C_Intelligence_image11-3.jpeg)

6. Click **+ Add entity** and add the **Subscribers : SubscriptionData** entity, check **Include all records**, then click **Done**

7. Create a new rule to match **Subscribers : SubscriptionData** and **Contacts : eCommerce** on **ContactId**

	![Picture 1094](Static/Lab_4C_Intelligence_image12.jpeg)

8. Name the rule **ContactId**, click **Done**. Then **Save** and **Run** the match

9. When the match finishes running you can click the **Merge** tab. Everything here is setup as we need it so just click **Run** > **Run Merge and downstream processes** to complete the process. Once the Merge is done running, which can take some time, you can proceed to the next Task

## Task 3 - Building Subscription Churn Model 

1. Go to **Intelligence** > **Predictions**

2. Click **Use model** on the **Customer churn model** card

	![Picture 1166](Static/Lab_4C_Intelligence_image13.jpeg)

3. Select **Subscription** and click **Get started**

4. Enter the Model name: **OOB Subscription Churn Model** and Output entity name **OOBSubscriptionChurnModel** and click **Next**

5. Set the days since subscription ended to 15 days click **Next**

	![Picture 1166](Static/Lab_4C_Intelligence_image13-2.jpeg)

6. Under Subscription history, hit **Add data** and select the **SubscriberHistory: SubscriptionData** entity from the list and map the fields as below and hit **Next**

	- Subscription ID: **SubscriptionID**

	- End Date: **SubscriptionEndDate**

	- Start Date: **SubscriptionStartDate**

	- Transaction Date: **TransactionDate**

	- Is it a recurring subscription: **IsRecurring**

	- Recurrence Frequency: **RecurringFrequencyInMonths**

	![Picture 1166](Static/Lab_4C_Intelligence_image13-3.jpeg)

7. Set up the relationship between **SubscriptionHistory** and **Subscribers** entity on the **CustomerID** and name it **SubHistory**, then click **Save** 

	![Picture 1166](Static/Lab_4C_Intelligence_image13-4.jpeg)

8. Within Customer activities, click on **Add data** and choose **UserLogs** entity from the list and map the fields as below

	- Customer activity entity: **UserLogs : SubscriptionData**

	- Primary key: **CustomerID**

	- Timestamp: **TransactionDate**

	- Event: **TransactionName**

	![Picture 1166](Static/Lab_4C_Intelligence_image13-5.jpeg)

9. Click **Next**

10. Set the activity type to **Usage** and set up relationship between **UserLogs** and **Subscribers** entity as below and hit **Save**

	- Activity type: **Usage**

	- Corresponding label: **CustomerID**

	- Customer entity: **Subscribers : SubscriptionData**

	- Relationship: **Logs**

	![Picture 1166](Static/Lab_4C_Intelligence_image13-6.jpeg)

11. Click **Next** and set training schedule as **Monthly** and click **Next**

12. Review the details and click **Save and Run** and then **Done**

	The model will initiate Activity entity to run for the first time and adds SubscriptionHistory and Userlogs to customer timeline. After that, the model run begins. This can take a long time as we have ingested a large amount of data inside the logs and subscription history.

	You can check the run status in the **System** page. Once the run has succeeded, you can go back to Intelligence and click on the created prediction 'Churn Model' to see the results and you can find the list of customers and their churn score in **Entities** > **ChurnModel**.

	![Picture 1166](Static/Lab_4C_Intelligence_image13-7.jpeg)

	![Picture 1166](Static/Lab_4C_Intelligence_image13-8.jpeg)

### Training Model Performance

The model is graded A, B or C depending on the following conditions:

- A when the model accurately predicted at least 50% of the total predictions, and when the percentage of accurate predictions for customers who churned is greater than the historical average churn rate by at least 10% of the historical average churn rate.

- B when the model accurately predicted at least 50% of the total predictions, and when the percentage of accurate predictions for customers who churned is up to 10% greater than the historical average churn rate of the historical average churn rate.

- C when the model accurately predicted less 50% of the total predictions, or when the percentage of accurate predictions for customers who churned is less than the historical average churn rate.

### Likelihood to churn (number of customers)

Likelihood of churn shows Groups of customers based on their predicted risk of churn. This data can help you later if you want to create a segment of customers with high churn risk. Such segments help to understand where your cutoff should be for segment membership.

### Most Influential Factors

There are many factors that are taken into account when creating your prediction. Each of the factors has their importance calculated for the aggregated predictions a model creates. You can use these factors to help validate your prediction results. Or you can use this information later to create segments that could help influence churn risk for customers.

## Task 4 - Set up a Segment of High Churn-risk Users

Observe that the Workflow upon setup, created an Entity. You can see this within Data -> Entities from the left-hand menu. You will see a new Intelligence section with the entity in it.

Open the Segments section from the left-hand menu. We will manually create a new dynamic segment.

1. Click **New** in the top menu bar. You'll notice there is now an Intelligence options in the **New** > **Create From** section. Choose the new **Intelligence** option.

2. Setup your quick segment with these settings:

	- Entity: **OOBSubscriptionChurnModel**

	- Field: **ChurnScore**

	- Operator: **greater than**

	- Value: **0.6**

	![Picture 1548](Static/Lab_4C_Intelligence_image14.jpeg)

3. Click **Review**

4. Name the segment **High Risk For Subscription Churn** and output entity name **HighRiskForSubscriptionChurn** and click **Save**

	![Picture 1550](Static/Lab_4C_Intelligence_image15.jpeg)

Now you have a segment that is dynamically updated which identifies high churn-risk customers for this subscription business.



# Optional - Customer Lifetime Value (CLV) Prediction Tasks

## Task 1: Configuring the Out of box Customer Lifetime Value prediction

1. In the left-hand menu click on **Intelligence** and then **Predictions**

2. Go to **Create** tab and click on the **Use model** button on the Customer Lifetime Value card. Read through the description in the side-panel and then click on **Get Started**

	![Picture 1550](Static/Lab_4C_Intelligence_image15-2.jpeg)

3. Name the model **OOB eCommerce CLV Prediction** and the output entity name as **OOBeCommerceCLVPrediction**

	![Picture 1550](Static/Lab_4C_Intelligence_image15-3.png)

4. Next, we need to define model preferences for the CLV Model:

	- **Prediction time period**: This setting defines how far into the future do we want to predict customer lifetime value. In this scenario, we will predict CLV for the next 12 months. Therefore, select **12 months or 1 year**.

	- **Active customers**: Specify what **Active customers** mean for your business. Set the historical time frame within which a customer must have had at least one transaction to be considered active. The model will only predict CLV for active customers. From the dropdown, you can choose to either let the model calculate this time period (purchase interval) based on your historical transaction data or you could choose to provide a specific time period. In this scenario, we will **let the model calculate the purchase interval**.

	- **High value customers**: Define High value customers as a percentile of top-paying customers - the model uses this input to provide results that fit your business definition of high value customers. You could choose to rely on the model to define high value customers for your business (the model uses a heuristic rule to derive the percentile of top paying customers for your business) or you could define high value customers in terms of a percentile of top future paying customers. For this scenario, we will **define high value customers as top 30% of active paying customers**.

		![Picture 1550](Static/Lab_4C_Intelligence_image15-4.png)

5. Next, in the **Required data** step, select **Add data**. This is where you map the required customer transaction history data for the model

6. Set the values as defined below, then click **Next**

	- Customer transaction history: **Purchases : eCommerce**

	- Transaction ID: **PurchaseId**

	- Transaction date: **PurchasedOn**
	
	- Transaction amount: **TotalPrice**

	- Product ID: **ProductId**

	![Picture 1823](Static/Lab_4C_Intelligence_image16.jpeg)

7. Join the **Purchases : eCommerce** entity with **Contacts : eCommerce** on **ContactId**, then **Save**. This may already be done for you based on relationships defined in the system already

	![Picture 1825](Static/Lab_4C_Intelligence_image17.jpeg)

8. Click **Next**

9. Next, the **Additional data (optional)** step allows you to add any other customer activity data that would help provide a holistic view of your customers' interactions with your business. Adding key customer interactions like web logs, customer service logs, rewards program history, email click history, etc can improve the accuracy of predictions. Select **Add data** to map additional customer activity data

	![Picture 1825](Static/Lab_4C_Intelligence_image17-2.png)

10. Add the **Reviews : Website** Entity and map the fields from the entity to the corresponding fields required by the Model. Click on **Next** when done

	- Primary key: **ReviewId**

	- Timestamp: **ReviewDate**

	- Event: **ActivityTypeDisplay**

	![Picture 1887](Static/Lab_4C_Intelligence_image18.jpeg)

11. Since we have mapped website reviews data, select the **Choose existing** option under **Activity Type** and select **Review** as the **Activity label** from the dropdown

12. Next, configure the relationship from the **Reviews : Website** entity to the **Contacts : eCommerce** entity by mapping the **UserId** column in the Reviews entity to the **ContactId** column in eCommerceContacts entity as shown below and click on **Save**. This may already be done for you based on relationships defined in the system already

	![Picture 1963](Static/Lab_4C_Intelligence_image19.jpeg)

13. Click on **Next** to set the model Schedule. The model needs to train with certain frequency so that it learns new patterns when there is new data ingested. For this example, select **Monthly** and click on **Next**

14. After reviewing all the details in the next screen, click on **Save and Run**

	**Note**: The model can take some time to finish running.

## Task 2 - Visualize Model Training Results and Explanation

After the model has successfully completed the training and scoring of the data, you can view the Customer Lifetime Value Model Results page by selecting **View** after clicking on the ellipses next to the model prediction name or simply clicking on the model prediction name.

![Picture 1963](Static/Lab_4C_Intelligence_image19-2.png)

### Model Results and Explanation page

![Picture 1963](Static/Lab_4C_Intelligence_image19-3.png)

#### Training Model Performance

![Picture 1963](Static/Lab_4C_Intelligence_image19-4.png)

A, B, or C are possible grades. This grade indicates the performance of the prediction and can help you make the decision to use the results stored in the output entity.

Using the definition of high value customers provided while configuring the prediction, the system assesses how the AI model performed in predicting the high value customers as compared to a baseline model.

Grades are determined based on the following rules:

- **A** when the model accurately predicted at least 5% more high-value customers as compared to the baseline model.

- **B** when the model accurately predicted between 0-5% more high-value customers as compared to the baseline model.

- **C** when the model accurately predicted fewer high-value customers as compared to the baseline model.

Select **Learn about this score** to understand in more detail the underlying model performance metrics.

The **Model rating** pane shows further details about the AI model performance and the baseline model. The **baseline model** uses a non-AI based approach to calculate customer lifetime value which is based primarily on historical purchases made by customers.

The standard formula used to calculate CLV by the baseline model is:

***CLV for each customer*** = *Average monthly purchase made by the customer in the active customer window * Number of months in the CLV prediction period * Overall retention rate of all customers*

The AI model is compared to the baseline model based on two model performance metrics.

![Picture 2119](Static/Lab_4C_Intelligence_image20.jpeg)

- **Success rate in predicting high-value customers**

	This metric shows the difference in predicting highvalue customers using the AI model compared to the baseline model. For example, 33% success rate means that out of all the high-value customers (based on your definition as specified in model preferences), the AI model was able to accurately capture 33%. This is then compared with the success rate of the baseline model (26% in this case) to report the relative change (+24%). The relative change (in percentage) is then used to assign a grade to the model.

- **Error metrics**

	Another metric lets you review the overall performance of the model in terms of error in predicting future values. The overall Root Mean Squared Error (RMSE) metric is a standard way to measure the error of a model in predicting quantitative data. The AI model's RMSE is compared to the RMSE of the baseline model and the relative difference is reported. In this case, the AI model was able to reduce the overall RMSE by 14% as compared to the baseline model.

#### Value of customer by percentile:

![Picture 2119](Static/Lab_4C_Intelligence_image20-2.png)

Using your definition of high-value customers, customers are grouped into **low-value** and **highvalue**, based on their CLV predictions, and shown in the above chart. By hovering over the bars in the histogram, you can see the number of customers in each group and the average CLV of that group. This data can be helpful if you want to create segments of customers based on their CLV predictions.

#### Most influential factors:

![Picture 2119](Static/Lab_4C_Intelligence_image20-3.png)

Numerous factors are considered when creating your CLV prediction based on the input data provided to the AI model. The most influential factors that impacted the CLV predictions at an aggregate level (across all customers) is reported along with their percentage impact on the predictions. You can use these factors to help validate your prediction results.

## Task 3 - Create a segment of high value customers

Running the production model creates a new entity that you can see in **Data** > **Entities**. You can create a new segment based on the entity created by the model.

1. Go to **Segments**. Select **New** and choose **Create from** > **Intelligence**.

2. Select the **OOBeCommerceCLVPrediction** entity and define the segment as follows:

	- Field: **CLVScore**

	- Operator: **greater than**

	- Value: **223**

	![Picture 2239](Static/Lab_4C_Intelligence_image21.jpeg)

3. Click **Review**, name the segment **Customers Predicted over $223 next 12 months** and **Save** the segment.

	You now have a segment that is dynamically updated which identifies high value customers (customers that are predicted to generated more than $223 of revenue in the next 12 months). 

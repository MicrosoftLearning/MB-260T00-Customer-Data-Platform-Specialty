---
lab:
    title: 'Lab 5.3: Subscription Churn Model'
    module: 'Module 5: Enrich data and predictions with Audience insights'
---

# Lab 5.3: Subscription Churn Model
# Module 5: Enrich data and predictions with Audience insights

## Exercise 1 - Ingest and unify the subsription data 
## Task 1 - Ingest the Subscription Data

1. First, we need to import the subscription data as a new data source. Navigate to **Data** in the left column, click **Data sources**, and select **+ Add Data Source**.

2. Choose **Microsoft Power Query** and name the source **SubscriptionData**, then click **Next.**

2. Select the **Text/CSV** Connector.

3. Enter the URL for the Subscribers data set, **https://aka.ms/CI-ILT/SubscriberContacts**, and click **Next**.

4. You should now see the data from the source tabulated. Click **Transform data** to configure the data types and formats for the data you ingest.

5. You will notice that the column heading has appeared in the first row of the data. To correct this, click **Transform** and **Use first row as headers**.

6. In the 'Name' field on the right-hand pane, rename your data source to **Subscribers**.

7. In the top left corner, click **Get Data** to add a new data set for this data source. Choose **Text/CSV**.

8. Enter the URL for the Subscriber History data set, **https://aka.ms/CI-ILT/SubHistory**, and click **Next**.

9. You should now see the data from the source tabulated. Click **Create** to configure the data types and formats for the data you ingest.

10. You will notice that the column heading has appeared in the first row of the data. To correct this, click **Transform** and **Use first row as headers**.

11. Because we have ingested data from a Text/CSV source, all columns have been defaulted to a 'Text' Data Type. To successfully ingest and model the data, we can set the datatype for non-text columns.

	To change the datatype, click the **ABC** icon within the column heading. Update the datatype for the columns listed below.

	| Column Heading | New Data Type |
	| - | - |
	| SubscriptionAmount | Whole Number |
	| SubscriptionEndDate | DateTime |
	| SubscriptionStartDate | DateTime |
	| TransactionDate | DateTime |
	| IsRecurring | True/False |
	| Is_auto_renew | True/False |
	| RecurringFrequencyInMonths | Whole Number |

12. In the 'Name' field on the right-hand pane, rename your data source to **SubscriberHistory**.

13. Click **Get Data**, then choose **Text/CSV**.

14. Enter the URL for the Userlog data set, **https://aka.ms/CI-ILT/Userlogs**, and click **Next**.

15. You should now see the data from the source tabulated. Click **Create** to configure the data types and formats for the data you ingest.

16. You will notice that the column heading has appeared in the first row of the data. To correct this, click **Transform** and **Use first row as headers**

17. Update the datatype for the columns listed below.

	| Column Heading | New Data Type |
	| - | - |
	| TransactionDate | DateTime |
	| TransactionValue | Whole Number |

18. In the 'Name' field on the right-hand pane, rename your data source **UserLogs** if needed. Click **Next.**

19. Leave the refresh schedule set to **Refresh manually** and click **Save**.

## Task 2 - Unify the Subscription Data with Existing Data

When the data source is finished loading we need to go through the Unify process. This can take a while as there is a lot of data in the SubscriptonData tables you are importing. The import can also fail if there are network issues because of the large data set.

1. Click on **Data** > **Unify** in the left-hand menu.

2. Click on **Edit Fields**, check **Subscribers (SubscriptionData)**, and then press **Apply**.

3. Click on **SubscriptionData Subscribers** in the entities list and select **ContactId** for the Primary Key.

4. Click **Save**. Click on the **Match** tab.

5. Click the **Edit** button on the **Matched records details** heading.

6. Click **+ Add** and add the **Subscribers : SubscriptionData** entity. Check **Include all**, then click **Done**

7. Create a new rule by clicking **+Add rule** underneath the SubscriptionData rule. Select **Contacts : eCommerce** for entity and **ContactId** for both fields.

8. Name the rule **ContactId**, click **Done**. Then **Save** and **Run** the match.

9. When the match finishes running you can click the **Merge** tab. Everything here is set up as we need it, so just click **Run** > **Run Merge and downstream processes** to complete the process. Once the Merge is done running, which can take some time, you can proceed to the next task.

## Exercise 2 - Create the subscription churn model

## Task 1 - Create subscription activities for use in the Subscription Churn Model

1. In the left menu, navigate to **Data > Activities.**

2. Click **+ Add Activity.**

3. On the Set up your activity data screen, name the activity **SubscriptionHistory**. Select **SubscriberHistory : SubscriptionData** for Activity entity and select **Subscription ID** as the Primary key.

4. On the Set up your relationships screen, select **Add relationship.** Configure your relationship as the following:

	- Foreign key from SusbcriberHistory : SubscriptionData: **CustomerID**
	- To entity name: **Subscribers : Subscription Data**
	- Relationship name: **SubHistory**

5. Click **Apply** and then click **Next.**

6. On the Unify your customer activity data screen, configure the following:

	- Event activity: CustomerID
	- Timestamp: TransactionDate

7. You can leave the remaining fields blank. Click **Next.**

8. On the Set activity type screen, select **Subscription** for Activity type and select the **Yes** radio button for "Provide semantic mapping...?"

9. Configure the activity type mapping as the following:

	- Transaction ID: CustomerID
	- Transaction date: TransactionDate
	- Subscription ID: SubscriptionID
	- Subscription start date: SubscriptionStartDate
	- Subscription end date: SubscriptionEndDate

10. Leave the remaining field mappings blank and click **Next.**

11. Review your selections and click **Save activity.**

12. Next, we will create the UserLogs activity. Back on the main Activities page, click **+ Add Activity.**

13. On the Set up your activity data screen, type **UserLogs** for Activity name and select **UserLogs : SubscriptionData** as the Activity entity. Select **CustomerID** as the Primary key and click **Next.**

14. On the Set up your relationships screen, click **+ Add relationship**. Configure your relationship as the following:

	- Foreign key from UserLogs : SubscriptionData: **CustomerID**
	- To entity name: **Subscribers : SubscriptionData**
	- Relationship name: **Logs**

15. Click **Apply** and then click **Next.**

16. On the Unify your customer activity data screen, configure the following:

	- Event activity: TransactionName
	- Timestamp: Transactiondate

17. You can leave the remaining fields blank. Click **Next.**

18. On the Set activity type screen, select **Usage** for activity type. Click **Next.**

19. Review your selections and click **Save activity.**

## Task 2 - Build the Subscription Churn Model 

1. Go to **Intelligence** > **Predictions**. 

2. From the **Create** tab, select **Use model** on the **Customer churn model** card.

3. Select **Subscription** and click **Get started**.

4. Enter the Model name: **OOB Subscription Churn Model** and Output entity name **OOBSubscriptionChurnModel** and click **Next**.

5. Set the **Days since subscription ended** to **15 days** and click **Next**.

6. Under Subscription history, hit **Add data** and select **Subscription** for the entity. Under Activities, select **SubscriberHistory : SubscriptionData** and click **Next.**

7. Review the mapped attributes that we mapped in Task 3 and click **Save**.

8. Within Customer activities, click on **Add data** and choose **Usage** for the entity. Under Activities, select **UserLogs : SubscriptionData.**

9. Map the following attributes:

	- Primary key: CustomerId
	- Timestamp: ActivityTime
	- Event activity: ActivityName

9. Click **Save** and then click **Next.**

11. Set the data update schedule as **Monthly** and click **Next**.

12. Review the details, click **Save and Run**, and then **Done**.

The model will initiate Activity entity to run for the first time and adds SubscriptionHistory and Userlogs to customer timeline. After that, the model run begins. This can take a long time as we have ingested a large amount of data inside the logs and subscription history.

You can check the run status in the **System** page. Once the run has succeeded, you can go back to Intelligence and click on the created prediction 'Churn Model' to see the results and you can find the list of customers and their churn score in **Entities** > **ChurnModel**.


### Training Model Performance

The model is graded A, B or C depending on the following conditions:

- A when the model accurately predicted at least 50% of the total predictions, and when the percentage of accurate predictions for customers who churned is greater than the historical average churn rate by at least 10% of the historical average churn rate.

- B when the model accurately predicted at least 50% of the total predictions, and when the percentage of accurate predictions for customers who churned is up to 10% greater than the historical average churn rate of the historical average churn rate.

- C when the model accurately predicted less 50% of the total predictions, or when the percentage of accurate predictions for customers who churned is less than the historical average churn rate.

### Likelihood to churn (number of customers)

Likelihood of churn shows Groups of customers based on their predicted risk of churn. This data can help you later if you want to create a segment of customers with high churn risk. Such segments help to understand where your cutoff should be for segment membership.

### Most Influential Factors

There are many factors that are taken into account when creating your prediction. Each of the factors has their importance calculated for the aggregated predictions a model creates. You can use these factors to help validate your prediction results. Or you can use this information later to create segments that could help influence churn risk for customers.

## Task 3 - Set up a Segment of High Churn-risk Users

Observe that the Workflow, upon setup, created an Entity. You can see this within Data -> Entities from the left-hand menu. You will see a new Intelligence section with the entity in it.

Open the Segments section from the left-hand menu. We will manually create a new dynamic segment.

1. Click **New > Create from** in the top menu. Choose the **Intelligence** option.

2. Set up your quick segment with these settings:

	- Entity: **OOBSubscriptionChurnModel**

	- Field: **ChurnScore**

	- Operator: **greater than**

	- Value: **0.6**

3. Click **Review**.

4. Name the segment **High Risk For Subscription Churn** and output entity name **HighRiskForSubscriptionChurn**. Click **Save**.

Now you have a segment that is dynamically updated which identifies high churn-risk customers for this subscription business.


---
lab:
    title: 'Lab 5.3: Subscription Churn Model'
    module: 'Module 5: Enrich data and predictions with Customer Insights - Data'
---

# Lab 5.3: Subscription Churn Model
# Module 5: Enrich data and predictions with Customer Insights - Data

## Exercise 1 - Ingest and unify the subsription data 
## Task 1 - Ingest the Subscription Data

1.  If you haven't already, sign into Customer Insights - Data at `https://home.ci.ai.dynamics.com`

2.  First, we need to import the subscription data as a new data source. Navigate to **Data** in the left navigation, select **Data sources**, and select **+ Add Data Source**. 

3.  Choose **Microsoft Power Query** and name the source `SubscriptionData`

4.  Select **Next** then select the **Text/CSV** Connector.

5.  Enter the URL for the *Subscribers* data set, `https://aka.ms/CI-ILT/SubscriberContacts` 

6.  Select **Next**. You should now see the data from the source tabulated. Click **Transform data** to configure the data types and formats for the data you ingest.

7.  You will notice that the column heading has appeared in the first row of the data. To correct this, select **Transform** and **Use first row as headers**.

8.  In the **Name** field on the right pane, rename your data source to `Subscribers`

9.  In the top left corner, select **Home** and select **Get Data** to add a new data set for this data source. Choose **Text/CSV**.

10. Enter the URL for the *Subscriber History* data set, `https://aka.ms/CI-ILT/SubHistory`

11. Select **Next**. You should now see the data from the source tabulated. Click **Create** to configure the data types and formats for the data you ingest.

12. You will notice that the column heading has appeared in the first row of the data. To correct this, select **Transform** and **Use first row as headers**.

13. Because we have ingested data from a Text/CSV source, all columns have been defaulted to a 'Text' Data Type. To successfully ingest and model the data, we can set the datatype for non-text columns.

	To change the datatype, select the **ABC** icon within the column heading. Update the datatype for the columns listed below:

	| Column Heading | New Data Type |
	| - | - |
	| SubscriptionAmount | Whole Number |
	| SubscriptionEndDate | DateTime |
	| SubscriptionStartDate | DateTime |
	| TransactionDate | DateTime |
	| IsRecurring | True/False |
	| Is_auto_renew | True/False |
	| RecurringFrequencyInMonths | Whole Number |

14. In the **Name** field on the right-hand pane, rename your data source to `SubscriberHistory`

15. Select **Home** and select **Get Data**, then choose **Text/CSV**. 

16. Enter the URL for the *Userlog* data set, `https://aka.ms/CI-ILT/Userlogs` 

17. Select **Next**. You should now see the data from the source tabulated. Select **Create** to configure the data types and formats for the data you ingest. 

18. You will notice that the column heading has appeared in the first row of the data. To correct this, select **Transform** and **Use first row as headers**. 

19. Update the datatype for the columns listed below.

	| Column Heading | New Data Type |
	| - | - |
	| TransactionDate | DateTime |
	| TransactionValue | Whole Number |

20. In the **Name** field on the right pane, rename your data source to `UserLogs` if needed. Select **Next**. 

21. Leave the refresh schedule set to **Refresh manually** and select **Save**.


## Task 2 - Unify the Subscription Data with Existing Data

When the data source is finished loading we need to go through the Unify process. This can take a while as there is a lot of data in the SubscriptonData tables you are importing. The import can also fail if there are network issues because of the large data set.

1. Select **Data** > **Unify** in the left navigation menu.

2. Select **Edit Fields**, check **Subscribers (SubscriptionData)**, and then press **Apply**.

3. Select **SubscriptionData Subscribers** in the tables list and select **ContactId** for the Primary Key.

4. Select **Save**. Select the **Match** tab.

5. Select the **Edit** button on the **Matched records details** heading.

6. Select **+ Add** and add the **Subscribers : SubscriptionData** entity. Check **Include all**, then click **Done**

7. Create a new rule by selecting **+Add rule** underneath the SubscriptionData rule. Select **Contacts : eCommerce** for table and **ContactId** for both fields.

8. Name the rule `ContactId`, select **Done**. Then **Save** and **Run** the match. 

9. When the match finishes running you can select the **Merge** tab. Everything here is set up as we need it, so just select **Run** > **Run Merge and downstream processes** to complete the process. Once the merge is done running, which can take some time, you can proceed to the next task.


## Exercise 2 - Create the subscription churn model

## Task 1 - Create subscription activities for use in the Subscription Churn Model

1.  In the left menu, navigate to **Data > Activities**. 

2.  Select **+ Add Activity**. 

3.  On the Set up your activity data screen, name the activity `SubscriptionHistory` 

4.  Select **SubscriberHistory : SubscriptionData** for Activity entity and select **SubscriptionID** as the Primary key.

5.  On the Set up your relationships screen, select **+ Add relationship.** Configure your relationship as the following:

	- Foreign key from SusbcriberHistory : SubscriptionData: **CustomerID**
	- To entity name: **Subscribers : Subscription Data**
	- Relationship name: **SubHistory**

6.  Select **Apply** and then select **Next**. 

7.  On the Unify your customer activity data screen, configure the following:

	- Event activity: CustomerID
	- Timestamp: TransactionDate

8.  You can leave the remaining fields blank. Select **Next**.

9.  On the Set activity type screen, select **Subscription** for Activity type and select the **Yes** radio button for "Provide semantic mapping...?"

10. Configure the activity type mapping as the following:

	- Transaction ID: CustomerID
	- Transaction date: TransactionDate
	- Subscription ID: SubscriptionID
	- Subscription start date: SubscriptionStartDate
	- Subscription end date: SubscriptionEndDate
	- Subscription type: SubscriptionType
	- Subscription amount: None
	- Is recurring?: IsRecurring
	- Recurring frequency in months: RecurringFrequencyInMonths

11. Leave the remaining field mappings blank and select **Next**. 

12. Review your selections and select **Save activity**. Then select **Done**. 

13. Next, we will create the UserLogs activity. Back on the main **Activities** page, select **+ Add Activity**.

14. On the **Set up your activity data** screen, type **UserLogs** for Activity name and select **UserLogs : SubscriptionData** as the Activity entity. Select **CustomerID** as the Primary key and select **Next**.

15. On the **Set up your relationships **screen, select **+ Add relationship**. Configure your relationship as the following:

	- Foreign key from UserLogs : SubscriptionData: **CustomerID**
	- To entity name: **Subscribers : SubscriptionData**
	- Relationship name: **Logs**

16. Select **Apply** and then select **Next**.

17. On the **Unify your customer activity data** screen, configure the following:

	- Event activity: TransactionName
	- Timestamp: Transactiondate

18. You can leave the remaining fields blank. Select **Next**.

19. On the **Set activity type** screen, select **Usage** for activity type. Select **Next**.

20. Review your selections and select **Save activity.** Then select **Done**. 


## Task 2 - Build the Subscription Churn Model 

1.  Go to **Insights** > **Predictions**. 

2.  From the **Create** tab, select **Use model** on the **Customer churn model** card.

3.  Select **Subscription** and select **Get started**.

4.  Enter `OOB Subscription Churn Model` for **Model name** and verify that Output table name is set to **OOBSubscriptionChurnModel**, then select **Next**. 

5.  Set the **Days since subscription ended** to `15 days` and select **Next**. 

6.  Under Subscription history, select **Add data** and select **Subscription** for the table. Under Activities, select **SubscriberHistory : SubscriptionData** and select **Next**. 

7.  Review the mapped attributes that we mapped earlier and select **Save**. 

8.  Within Customer activities, select **Add data** and choose **Usage** for the table. Under Activities, select **UserLogs : SubscriptionData.** and select **Next**. 

9.  Map the following attributes:

	- Primary key: CustomerId
	- Timestamp: ActivityTime
	- Event activity: ActivityName

10. Select **Save** and then select **Next**.

11. Set the data update schedule as **Monthly** and select **Next**.

12. Review the details, select **Save and Run**, and then **Done**.

The model will initiate the Activity table to run for the first time and adds **SubscriptionHistory** and **Userlogs** to the customer timeline. After that, the model run begins. This can take a long time as we have ingested a large amount of data inside the logs and subscription history.

You can check the status of queued and refreshing tasks on the **Admin** > **System** page. Once the task status is **Successful**, you can go back to **Insights** and select the created prediction **Churn Model** to see the results and you can find the list of customers and their churn score in **Data** > **Entities** > **ChurnModel**.


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

1.  Open the **Segments** section from the left navigation. We will manually create a new dynamic segment.

2.  Select **New > Create from Intelligence** option.

3.  Set up your quick segment with these settings:

	- Table: **OOBSubscriptionChurnModel**

	- Field: **ChurnScore**

	- Operator: **greater than**

	- Value: `0.6`

4.  Select **Review**. 

5.  Name the segment `High Risk For Subscription Churn` and output table name `HighRiskForSubscriptionChurn`

6.  Select **Save**.

Now you have a segment that is dynamically updated which identifies high churn-risk customers for this subscription business.


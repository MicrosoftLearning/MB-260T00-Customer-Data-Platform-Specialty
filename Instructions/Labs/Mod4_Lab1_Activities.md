---
lab:
    title: 'Lab 4.1: Work with activities'
    module: 'Module 4: Work with Dynamics 365 Customer Insights - Data'
---

# Lab 4.1: Work with activities
# Module 4: Work with Dynamics 365 Customer Insights - Data


## Exercise 1 - Create activities 
The Activities capability helps consolidate customer activities from various data sources. This creates a customer timeline view of all customer interactions against your unified customer profile. Business analysts can configure activities to be displayed on a customer dashboard with a timeline view, which can be embedded in business applications. 

Interactions are any customer touch points - these could include purchases, customer service cases, emails, phone calls, branch visits, web, social activity. In other scenarios interactions could also be data gathered from connected devices, withdrawals or deposits in banking, entry/exist of a premises or area, etc. 

### Task 1 - Add an activity for eCommerce Purchases  

1.  If you haven't already, sign into Customer Insights - Data at `https://home.ci.ai.dynamics.com`

2.  In Customer Insights, expand **Data > Activities** on the left navigation menu and select **+ Configure activities**.

3.  Select the **Purchases : eCommerce** table and select **Add**.

4.  Set the **Activity type** to **SalesOrder**.

5.  Set the **Primary key** to **PurchaseId** and select **Next**.

6.  Enter `OnlinePurchase` for **Activity name**.

7.  Select the following fields:

    - Timestamp: **PurchasedOn**
      
	- Event activity: **ActivityTypeDisplay**

	- Additional detail: **Subject**

    - Show this activity in the timeline on your customer profile? **Yes**.

    - Icon: Select the **shopping bag**.

	- Sales order ID: **PurchaseID** 
	
	- Order date: **PurchasedOn** 
	
	- Sales amount: **TotalPrice** 

8.  Select **Next**. On the **Configure activity relationships** screen, select **+ Add relationship**. 

9.  In the **Add relationship path** pane, set the following values: 

	- Foreign key: **ContactId** 

	- To table name: **Contacts : eCommerce** 
	
	- Relationship name: `eCommPurchasesToContacts` 

10. Select **Apply**. 

11. Select **Next**, review the entries, then select **Create activities**. 

12. **Wait** while the Activities refresh and unify. This may take 5-10 minutes.


### Task 2 - Add an activity for PoSPurchases 

1.  Select **Configure activities**.

2.  Select the **Purchases : PoS** table and select **Add**.

3.  For **Activity type**, select **Create new** from the bottom of the drop-down.

4.  Enter `PoSPurchase` for the **Activity type** then select **Add**.

5.  Set the **Primary key** to **PurchaseId** and select **Next**.

6.  Select the **PoS Purchases** row, enter `PoSPurchase` for **Activity name**.

7.  Select for the following fields:

    - Timestamp: **PurchasedOn**
      
	- Event activity: **ActivityTypeDisplay**

	- Additional detail: **Subject**

    - Show this activity in the timeline on your customer profile? **Yes**.

    - Icon: Select the **shopping bag**.

	- Sales order ID: **PurchaseID** 
	
	- Order date: **PurchasedOn** 
	
	- Sales amount: **TotalPrice** 

8.  Select **Next**.

9.  Select **+ Add relationship** and in the **Add relationship path** pane, set the following values: 

	- Foreign key: **LoyaltyId** 

	- To entity name: Customers : Loyalty 

	- Relationshiop name: `PoSPurchasesToLoyalty` 

10. Select **Apply**.

11. Select **Next**, review your entries, and select **Create activities**. 

12. **Wait** while the Activities refresh and unify. This may take 5-10 minutes.


### Task 3 - Add an activity for Website Reviews 

1.  Select **Configure activities**.

3.  Set up the activity data with the following values: 

	- Activity name: `WebsiteReview` 

	- Entity: **Reviews : Website** 

	- Primary Key: **ReviewId** 

4.  Select **Next**. On the Relationships screen, select **+ Add relationship**. 

5.  In the **Add relationship path** pane, set the following values: 

	- Foreign key: **UserId** 

	- To entity name: **Contacts : eCommerce** 

	- Relationship name: `WebReviewsToContacts` 

6.  Select **Apply**. 

7.  Click **Next**. 

8.  Unify the customer activity data by setting the following values: 

	- Event activity: **ActivityTypeDisplay** 
	
	- Timestamp: **ReviewDate** 
	
	- Additional detail: **ReviewText** 
	
	- Icon: Select the **globe** icon. 
	
	- Show this information in the timeline view on your customer profiles?: Select **Yes**. 
	
9.  Select **Next**. 

10.  Set **Activity type** to **Create new** and enter `WebsiteReview` for the **Activity type name**. 

11. Select **Next**, review your entries, and select **Save activity**. 

12. Select **Done**. 


### Task 4 - Confirm the Activities 

1.  Select **Run** from the toolbar to run the configured activities. Select **Refreshing** to view the Progess details. Once they have completed successfully, select **Customers** from the left navigation menu. 

2.  Search for `Abbie Moss`. 

3.  Select the record to open the detailed view. 

4.  You should now see activities listed for Abbie on the **Activity timeline**. Select **Filter** to narrow down the **Activity types** further. 


## Exercise 2 - Define relationships 

Relationships help you connect entities and generate a graph of your data. Relationships are used when entities share a common identifier (foreign key) that can be referenced from one entity to another. Connected entities enable you to define segments and measures based on multiple data sources. 

For example, **Customer** has a **One to Many** relationship with **PoS Purchases**. (One loyalty scheme customer may make multiple purchases). 

## Task 1 - Define the Relationship Between Unified Profiles and Web Purchases 

First, we need to define the relationship for CustomerPurchasesEcom. 

1.  In Customer Insights, expand **Data** from the left navigation menu and select **Relationships**. 

2.  Select **+ New relationship**.

3.  Enter `CustomerPurchasesEcom` for **Name**.

4.  For **Description**, enter `Online Purchases to Unified Customer Profile`.

5.  Set the **Source details > Entity** to **Purchases: eCommerce** and Cardinality to **Many**.  

6.  Set the **Target details > Entity** to **Customer : CustomerInsights** and Cardinality to **One**. 

7.  Set **Equivalent fields** to **ContactId** for both the **Source** and **Target** fields. 

8.  Select **Save**. 


## Task 2 - Define the Relationship between Unified Profiles and Store Purchases 

Next, we will define the relationship for CustomerPurchasesPOS.

1.  From the left navigation menu, expand **Data** and select **Relationships**. 

2.  Select **+ New relationship**. Name the relationship `CustomerPurchasesPOS`.

3.  For **Description,** write "Point of Sale Purchases to Unified Customers."

4.  Set the **Source details > Entity** to **Purchases : PoS** and Cardinality to **Many**. 

5.  Set the **Target details > Entity** to **Customer : CustomerInsights** and Cardinality to **One**. 

6.  Set **Equivalent fields** to **LoyaltyId** for both **Source** field and **Target** field. 

7.  Select **Save**. 


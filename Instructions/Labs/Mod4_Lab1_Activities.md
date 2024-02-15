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

2.  Select the **Reviews : Website** table and select **Add**.

3.  For **Activity type**, select **Create new** from the bottom of the drop-down.

4.  Enter `WebsiteReview` for the **Activity type** then select **Add**.

5.  Set the **Primary key** to **ReviewId** and select **Next**.

6.  Select the **Reviews** row, enter `WebsiteReview` for **Activity name**.

7.  Select for the following fields:

    - Timestamp: **ReviewDate**
      
	- Event activity: **ActivityTypeDisplay**

	- Additional detail: **ReviewText**

    - Show this activity in the timeline on your customer profile? **Yes**.

    - Icon: Select the **globe**.

	- Sales order ID: **PurchaseID** 
	
	- Order date: **PurchasedOn** 
	
	- Sales amount: **TotalPrice** 

8.  Select **Next**.

9.  Select **+ Add relationship** and in the **Add relationship path** pane, set the following values: 

	- Foreign key: **UserId** 

	- To entity name: Contacts : eCommerce 

	- Relationshiop name: `WebReviewsToContacts`

10. Select **Apply**.

11. Select **Next**, review your entries, and select **Create activities**. 

12. **Wait** while the Activities refresh and unify. This may take 5-10 minutes.


### Task 4 - Confirm the Activities 

1.  Select **Customers** from the left navigation. 

2.  Search for `Abbie Moss`

3.  Select the record to open the detailed view. 

4.  You should now see activities listed for Abbie on the **Activity timeline**. Select **Filter** to narrow down the **Activity types** further. 


## Exercise 2 - Define relationships 

Relationships help you connect entities and generate a graph of your data. Relationships are used when entities share a common identifier (foreign key) that can be referenced from one entity to another. Connected entities enable you to define segments and measures based on multiple data sources. 

For example, **Customer** has a **One to Many** relationship with **PoS Purchases**. (One loyalty scheme customer may make multiple purchases). 

## Task 1 - Define the Relationship Between Unified Profiles and Web Purchases 

First, we need to define the relationship for CustomerPurchasesEcom. 

1.  In Customer Insights, expand **Data** from the left navigation menu and select **Tables**.

2.  Select the **Relationships** tab.

3.  Select **+ New relationship**.

4.  Enter `CustomerPurchasesEcom` for **Name**.

5.  For **Description**, enter `Online Purchases to Unified Customer Profile`

6.  Set the **Source details > Table** to **Purchases: eCommerce**. Set the **Cardinality** to **Many**.  

7.  Set the **Target details > Table** to **Customer : CustomerInsights**. Set the **Cardinality** to **One**. 

8.  Set **Equivalent fields** to **ContactId** for both the **Source field** and **Target field**. 

9.  Select **Save**. 


## Task 2 - Define the Relationship between Unified Profiles and Store Purchases 

Next, we will define the relationship for CustomerPurchasesPOS.

1.  From the left navigation menu, expand **Data** and select **Tables**.

2.  Select the **Relationships** tab. 

3.  Select **+ New relationship**. Name the relationship `CustomerPurchasesPOS`

4.  For **Description,** enter `Point of Sale Purchases to Unified Customers`

5.  Set the **Source details > Table** to **Purchases : PoS**. Set the **Cardinality** to **Many**. 

6.  Set the **Target details > Table** to **Customer : CustomerInsights**. Set the **Cardinality** to **One**. 

7.  Set **Equivalent fields** to **LoyaltyId** for both **Source field** and **Target field**. 

8.  Select **Save**. 


---
lab:
    title: 'Lab 4.1: Work with activities'
    module: 'Module 4: Work with Dynamics 365 Customer Insights'
---

# Lab 4.1: Work with activities
# Module 4: Work with Dynamics 365 Customer Insights


## Exercise 1 - Create activities 
The Activities capability helps consolidate customer activities from various data sources. This creates a customer timeline view of all customer interactions against your unified customer profile. Business analysts can configure activities to be displayed on a customer dashboard with a timeline view, which can be embedded in business applications. 

Interactions are any customer touch points - these could include purchases, customer service cases, emails, phone calls, branch visits, web, social activity. In other scenarios interactions could also be data gathered from connected devices, withdrawals or deposits in banking, entry/exist of a premises or area, etc. 

### Task 1 - Add an activity for eCommerce Purchases  

1. If you haven't already, sign into Customer Insights at https://home.ci.ai.dynamics.com/.

3. Within Customer Insights, Expand **Data > Activities** on the left menu and click **Add Activity.** 

2. On the Activity data screen set the following values: 

	- Activity name: `OnlinePurchase`

	- Entity: Purchases : eCommerce 

	- Primary Key: PurchaseId 

3. Click Next. On the Relationships screen, click **+ Add relationship.** 

4. In the Add relationship path pop-up, set the following values: 

	- Foreign key: ContactId 

	- To entity name: Contacts : eCommerce 
	
	- Relationship name: eCommPurchasesToContacts 

5. Click **Apply** to close the pop-up. 

6. Click **Next.** 

7. On the **Unify your customer activity data** screen, set the following values:

	- Event activity: **ActivityTypeDisplay**
	- Timestamp: **PurchasedOn**
	- Additional detail: **Subject**
	- Icon: Select the **shopping bag.**
	- Show in timeline view?: Yes

8. Click **Next.** 

9. On the Set activity type screen, set the type to **SalesOrder**.

10. Set "Provide semantic mapping for your activity's attributes?" to **Yes.**

11. Fill out the data for activity type field mapping as follows:

	- Sales order ID: PurchaseID
	- Order date: PurchasedOn
	- Sales amount: TotalPrice

12. Click **Next**, review your entries, then click **Save activity.**

13. Click **Done.**

### Task 2 - Add an activity for PoSPurchases 

1. Click Add Activity 

2. On the Activity data screen set the following values: 

	- Activity name: `PoSPurchase`

	- Entity: Purchases : PoS 

	- Primary Key: PurchaseId 

3. Click **Next**. On the Realtionships screen, click **+ Add relationship.**

4. In the Add relationship path pop-up, set the following values: 

	- Foreign key: LoyaltyId 

	- To entity name: Customers : Loyalty 

	- Relationshiop name: PoSPurchasesToLoyalty 

5. Click **Apply** to close the pop-up. 

6. Click **Next.** 

7. On the Unify your customer activity data screen set the following values:

	- Event activity: ActivityTypeDisplay
	- Timestamp: PurchasedOn
	- Additional detail: Subject
	- Icon: Select the **shopping bag**.
	- Show in timeline view?: Yes

8. Click **Next.**

9. On the Set activity type screen, set the type to **Create new** and then enter **PoSPurchase** for the Activity Type Name. 

10. Click **Next**, review your entries, then click **Save activity**. 

11. Click **Done**. 

### Task 3 - Add an activity for Website Reviews 

1. Click **+ Add Activity.** 

2. On the Activity data screen, set the following values: 

	- Activity name: WebsiteReview 

	- Entity: Reviews : Website 

	- Primary Key: ReviewId 

3. Click **Next**. On the Realtionships screen, click **+ Add relationship.** 

4. In the Add relationship path pop-up, set the following values: 

	- Foreign key: UserId 

	- To entity name: Contacts : eCommerce 

	- Relationship name: WebReviewsToContacts 

5. Click **Apply** to close the pop-up .

6. Click **Next.** 

7. On the Unify your customer activity data screen, set the following values:

	- Event activity: ActivityTypeDisplay
	- Timestamp: ReviewDate
	- Additional detail: ReviewText
	- Icon: Select the **internet (circular globe)** icon.
	- Show in timeline view?: Yes
	
8. Click **Next.** 

9. One the Set activity type screen, set the type to **Create new** and then enter **WebsiteReview** for the Activity Type Name. 

10. Click **Next**, review your entries, and then click **Save activity.**

11. Click **Done.**

### Task 4 - Confirm the Activities 

1. Click **Run** on the top to run the configured activities. Once they have completed, click on **Customers** in the left-hand menu. 

2. Search for **Abbie Moss.** 

3. Click on her name to expand her customer card. 

4. You should now see activities listed for Abbie on the timeline. Try using the Filter to view only specific activities. 

## Exercise 2 - Define relationships 

Relationships help you connect entities and generate a graph of your data. Relationships are used when entities share a common identifier (foreign key) that can be referenced from one entity to another. Connected entities enable you to define segments and measures based on multiple data sources. 

For example, **Customer** has a **One to Many** relationship with **PoS Purchases**. (One loyalty scheme customer may make multiple purchases). 

## Task 1 - Define the Relationship Between Unified Profiles and Web Purchases 

First, we need to define the relationship for CustomerPurchasesEcom. 

1. In the left menu under **Data,** click **Relationships.**

3. Click **+ New relationship.**

3. Name the relationship **CustomerPurchasesEcom.**

4. In Description, write "Online Purchases to Unified Customer Profile."

5. Set Source details entity to **Purchases: eCommerce** and Cardinality to **Many.** 

7. Set Target details entity to **Customer : CustomerInsights** and Cardinality to **One.**

7. Set equivalent fields to **ContactId (eCommerce_Contacts)** for both the Source and Target fields. 

9. Click **Save.** 

## Task 2 - Define the Relationship between Unified Profiles and Store Purchases 

Next, we will define the relationship for CustomerPurchasesPOS.

1. From the left menu, click **Data** and then **Relationships.**

2. Click **+ New relationship.** Name the relationship **CustomerPurchasesPOS.**

3. In **Description,** write "Point of Sale Purchases to Unified Customers."

4. Set Source details entity to **Purchases : PoS** and Cardinality to **Many.**

5. Set Target details entity to **Customer : CustomerInsights** and Cardinality to **One.**

6. Set equivalent fields to **LoyaltyId** for both Source field and Target field.

8. Click **Save.**

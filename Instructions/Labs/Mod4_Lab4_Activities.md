---
lab:
    title: 'Lab 4.1: Work with activities'
    module: 'Module 4: Work with Dynamics 365 Audience insights'
---

# Lab 4.1: Work with activities
# Module 4: Work with Dynamics 365 Audience insights

The Activities capability helps consolidate customer activities from various data sources. This creates a customer timeline view of all customer interactions against your unified customer profile. Business analysts can configure activities to be displayed on a customer dashboard with a timeline view, which can be embedded in business applications. 

Interactions are any customer touch points - these could include purchases, customer service cases, emails, phone calls, branch visits, web, social activity. In other scenarios interactions could also be data gathered from connected devices, withdrawals or deposits in banking, entry/exist of a premises or area, etc. 

### Task 1 - Add an activity for eCommerce Purchases  

1. Within Customer Insights, Expand **Data > Activities** on the left menu and click **Add Activity.** 

2. On the Activity data screen set the following values: 

	- Activity name: OnlinePurchase 

	- Entity: Purchases : eCommerce 

	- Primary Key: PurchaseId 

3. Click Next. On the Realtionships screen, click **+ Add relationship.** 

4. In the Add relationship path pop-up, set the following values: 

	- Foreign key: ContactId 

	- To entity name: Contacts : eCommerce 
	
	- Relationship name: eCommPurchasesToContacts 

5. Click **Apply** to close the pop-up. 

6. Click **Next.** 

7. On the **Unify your customer activity data** screen, set the following values:
	- Envent activity: **ActvityTypeDisplay**
	- Timestamp: **PurchasedOn**
	- Additional detail: **Subject**
	- Icon: Select the **shopping bag.**
	- Show in timeline view?: Yes

8. Click **Next.** 

9. On the Set activity type screen, set the type to **SalesOrderLine* and then enter **OnlinePurchase** for the Activity Type Name. 

4. Set "Provide semantic mapping for your activity's attributes?" to **Yes.**

5. Fill out the data for activity type field mapping as follows:

- Order online ID: PurchaseId

- Order date: PurchasedOn

- Product ID: ProductId

- Amount: TotalPrice

10. Click **Next**, review your entries, then click **Save activity.**


### Task 2 - Add an activity for PoSPurchases 

1. Click Add Activity 

2. On the Activity data screen set the following values: 

	- Activity name: PoSPurchase 

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

	- Event activity: AcitivtyTypeDisplay
	- Timestamp: PurchasedOn
	- Additional detail: Subject
	- Icon: Select the **shopping bag.**
	- Show in timeline view?: Yes

8. Click **Next.**

9. One the Set activity type screen, set the type to **Create New** and then enter **PoSPurchase** for the Activity Type Name. 

10. Click **Next**, review your entries, then click **Save activity.** 

  

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

7. On the Unify your customer activity data screen set the following values:

	- Event activity: AcitivtyTypeDisplay
	- Timestamp: ReviewDate
	- Additional detail: ReviewText
	- Icon: Select the **internet (circular globe)** icon.
	- Show in timeline view?: Yes
	
8. Click **Next.** 

9. One the Set activity type screen, set the type to **Create new** and then enter **WebsiteReview** for the Activity Type Name. 

10. Click **Next**, review your entries, and then click **Save activity.**

### Task 4 - Confirm the Activities 

Click **Run** on the top to run the configured activities. Once they have completed, click on **Customers** in the left-hand menu. 

1. Search for **Abbie Moss.** 

2. Click on her name to expand her customer card. 

4. You should now see activities listed for Abbie on the timeline. Try using the Filter to view only specific activities. 

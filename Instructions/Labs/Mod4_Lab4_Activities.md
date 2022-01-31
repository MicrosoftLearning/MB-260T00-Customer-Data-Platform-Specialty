---
lab:
    title: 'Lab 4.4: Work with activities'
    module: 'Module 4: Work with Dynamics 365 Audience insights'
---

# Lab 4.4: Work with activities
# Module 4: Work with Dynamics 365 Audience insights

The Activities capability helps consolidate customer activities from various data sources. This creates a customer timeline view of all customer interactions against your unified customer profile. Business analysts can configure activities to be displayed on a customer dashboard with a timeline view, which can be embedded in business applications. 

 

Interactions are any customer touch points - these could include purchases, customer service cases, emails, phone calls, branch visits, web, social activity. In other scenarios interactions could also be data gathered from connected devices, withdrawals or deposits in banking, entry/exist of a premises or area etc. 

![Picture 17](Static/Lab_4B_Picture17.png)  

 

 

 

  

### Task 1 - Add an activity for eCommerce Purchases 

 

1. Within Customer Insights, Expand Data -> Activities on the left menu and click Add Activity 

2. On the Activity data screen set the following values: 

	- Activity name: OnlinePurchase 

	- Entity: Purchases : eCommerce 

	- Primary Key: PurchaseId 

	![Picture 1928](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image16.jpeg) 

3. Click Next. On the Realtionships screen click Add relationship 

	![Picture 18](Static/Lab_4B_Picture18.png) 

4. In the Add relationship path pop-up set the following values: 

	- Foreign key: ContactId 

	- To entity name: Contacts : eCommerce -  Relationshiop name: 

      eCommPurchasesToContacts 

		![Picture 1934](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image17.jpeg)
 

5. Click Apply to close the pop-up 

6. Click Next 

7. On the **Unify your customer activity data** screen set the following values:
	- Envent activity: **ActvityTypeDisplay**
	- Timestamp: **PurchasedOn**
	- Additional detail: **Subject**
	- Icon: ![Icon](Static/Lab_4B_Picture19.png)


8. Click Next 

9. One the Set activity type screen set the type to Create New and then enter OnlinePurchase for the Activity Type Name. 

	![Picture 2004](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image18.jpeg) 

10. Click Next, review your entries then click Save activity 

  

### Task 2 - Add an activity for PoSPurchases 

 

1. Click Add Activity 

2. On the Activity data screen set the following values: 

	- Activity name: PoSPurchase 

	- Entity: Purchases : PoS 

	- Primary Key: PurchaseId 

	![Picture 2090](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image19.jpeg) 

3. Click Next. On the Realtionships screen click Add relationship 

	![Picture 20](Static/Lab_4B_Picture20.png)

4. In the Add relationship path pop-up set the following values: 

	- Foreign key: LoyaltyId 

	- To entity name: Customers : Loyalty 

	- Relationshiop name: PoSPurchasesToLoyalty 

     ![Picture 2096](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image20.jpeg)

5. Click Apply to close the pop-up 

6. Click Next 

7. On the Unify your customer activity data screen set the following values:
	- Event activity: AcitivtyTypeDisplay
	- Timestamp: PurchasedOn
	- Additional detail: Subject
	- Icon: ![icon](Static/Lab_4B_Picture19.png)

	![Picture 21](Static/Lab_4B_Picture21.png)

8. Click Next 

9. One the Set activity type screen set the type to Create New and then enter PoSPurchase for the Activity Type Name. 

	![Picture 2166](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image21.jpeg) 

10. Click Next, review your entries then click Save activity 

  

### Task 3 - Add an activity for Website Reviews 

 

1. Click Add Activity 

2. On the Activity data screen set the following values: 

	- Activity name: WebsiteReview 

	- Entity: Reviews : Website 

	- Primary Key: ReviewId 

	![Picture 2252](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image22.jpeg) 

3. Click Next. On the Realtionships screen click Add relationship 

	![Picture 22](Static/Lab_4B_Picture22.png)
 

4. In the Add relationship path pop-up set the following values: 

	- Foreign key: UserId 

	- To entity name: Contacts : eCommerce 

	- Relationshiop name: WebReviewsToContacts 
      ![Picture 2258](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image23.jpeg)
 

5. Click Apply to close the pop-up 

6. Click Next 

7. On the Unify your customer activity data screen set the following values:
	- Event activity: AcitivtyTypeDisplay
	- Timestamp: ReviewDate
	- Additional detail: ReviewText
	- Icon: ![icon](Static/Lab_4B_Picture24.png)

	![Picture 21](Static/Lab_4B_Picture21.png) 

 

8. Click Next 

9. One the Set activity type screen set the type to Create New and then enter WebsiteReview for the Activity Type Name. 

	![Picture 2328](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image24.jpeg) 

10. Click Next, review your entries then click Save activity 

  

### Task 4 - Confirm the Activities 

 

Click Run on the top to run the configured activities. Once they have completed click on Customers in the left-hand menu 

 

1. Search for Abbie Moss 

 

2. You should now see activities listed for Abbie on the timeline. Try using the Filter to view only specific activities. 

	![Picture 2369](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image25.jpeg)

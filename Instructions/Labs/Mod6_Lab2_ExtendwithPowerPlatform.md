---
lab:
    title: 'Lab 6.2: Extend with the Power Platform'
    module: 'Module 6: Manage external connections with Dynamics 365 Customer Data Platform'
---

# Lab 6.2: Extend with the Power Platform
# Module 6: Manage external connections with Dynamics 365 Customer Data Platform

Having successfully ingested Contoso Coffee's data sources and created a Unified Customer Profile and calculated key measures, you are now able to leverage the insight you have generated to empower different personas within Contoso Coffee over different platforms. 

## Power Automate Extensibility 
Contoso wants to capture in-store interactions with their customers. You are charged with enabling Contoso Retail staff to capture 'Customer Check-In' activities and deliver personalized recommendations to customers. 

In this module, you will create a custom 'Check In' activity within Dynamics 365 to store details of customer store visits. You will enable Contoso Retail staff to capture these check ins using a planned 'Greeter App' and Power Automate, including details of the subjects discussed with the customer. 

In this Module you will create the custom 'Check In' activity and configure a Flow to capture a customer check in, to be triggered from a planned 'Greeter App'. 

In this module you will also create a Flow to generate personalized recommendations that can be surfaced within Dynamics 365 or the Greeter App using Insight Cards. 

## Power App Extensibility 

Contoso want to deliver personalized service and recommendations to customers who visit their retail stores and coffee shop's and capture details of customers visiting their stores. To do this, they have decided to empower their Contoso Coffee Retail staff with a greeter app, empowering staff to have a more informed conversation with customers and deliver personalized service and recommendations. 

As Project Manager for Contoso Coffee, you will create a Greeter App using Power Apps for Contoso retail staff who will be able to look-up unified customer profiles, capture customer check-ins and deliver personalized recommendations to customers. 

## Objectives 

- Create a Power Automate to configure 'Churn Customers Surge Alert' 

- Create Contoso Coffee Greeter App using PowerApps 

- Connect app with Customer Insights Unified Profile 

 
# Exercise 1 - Power Automate
In this task you will create a Flow, which will be triggered in a later Module from a PowerApp by Contoso Retail staff who interact with Contoso Coffee Customers, in order to capture a record of that customer having visited. 

1. Navigate to [make.powerapps.com](make.powerapps.com) and sign in if prompted. Select your Customer Insights environment on top right from the drop down. 

3. From the left hand menu, click **Flows.** (If prompted, click **Get started.**)

4. Click **+ New flow** and then select **Instant cloud flow** from the dropdown.

5. Click **Skip**. 

6. Name your flow on the top by double clicking on **Untitled** as **ChurnCustomersSurgeAlert**. 

7. Within the "Search connectors and triggers" search bar, search for Dynamics 365 Customer Insights. In the triggers box, find **Triggers a flow when a segment threshold is crossed (preview)** and select it.

9. You may be signed into your Customer Insights instance automatically, or you may need to sign in manually. After you've been authenticated, select your instance from the drop down. **Note**: Be sure to set the threshold to a number slightly larger than the current number of members in your segment so the trigger is hit later when we change the segment setting. 

	- Segment : **HighRiskTransactionChurn** 

	- Threshold: **1200** 

10. Click **+ New step**. In the "Search connectors and actions" search bar, search for **Send an email (V2)**, select it. You may be signed into Outlook automatically, or you may need to sign in manually using your M365 credential.

11. Enter the following: 

	- **To**: Email address 

	- **Subject**: Churn Customers Surge Alert!

	- **Body**: Customers in segment HighRiskForChurn has crossed the threshold. Review the customer list. 

12. Click **Save**.

13. To test your Power Automate flow, go back to your Customer Insights environment and edit your **High Risk For Churn** segment condition as ChurnScore greater than 0.5 instead of 0.6 which adds some more customers to your segment and triggers this Power Automate. 

You should receive an email once the segment is refreshed. 

# Exercise 2 - Power App

To create the Contoso Coffee Greeter App from this lab, you will import a template app and connect the App to Customer Insights and Flow. 

## Task 1 - Import the Greeter App Template 

1. Sign-In to https://make.powerapps.com and select your Customer Insights environment if it is not already selected.

2. Click **Apps** in the left-hand menu, and then click **Import Canvas App** from the top menu bar. 

3. Click the **Upload** button and select the **CustomerInsightsGreeterApp.zip** included with the module content, then **Upload**. 

4. On the next page, select **Import**. If **Import** is grayed out and **Import Setup** says Update, then click **Update** under **Import Setup** and change to **Create as new**. 

5. Once the package has completed its import, click **Apps** in the left menu. You should see your imported app listed. 


6. Click the '...' icon next to its name and select **Edit** to load the app in Edit Mode. (If you are prompted with a Welcome pop-up, click **Get started** and/or **Skip.**)


## Task 2 - Connect to Data Source(s) 

In this task, we will use the Customer Insights Connector to connect the Greeter Power App to your Customer Insights Instance. 

1. In the top menu bar, click **View** then select **Data Sources**. 

3. In the **Data** menu that opens on the right, click **+ Add data source**.

5. Click **New Connection** and search for the **Dynamics 365 Customer Insights** connector.
 
7. Select the connector and then click **Connect**. (You may get a pop-up here - click **Got it** to skip.) If prompted, sign in with your credentials.

5. Select **Customer** and **UnifiedActivity**. Type **Customer_Measure** into the Enter custom table name box and check the corresponding box. Then click **Connect**.

6. You should see three new tables listed as data sources. Congratulations! You have established a connection to Customer Insights within your Power App. 

## Task 3 - Configure the Customer Search Screen 

In this task you are going to connect Customer Insights data to the Customer Search and Customer Profile screens within the greeter app. This will enable Contoso Coffee Retail staff to find and view customer information when they greet them in store. 

1. Within the Greeter Power App in Edit mode, open the **CustomerSearch_Screen screen** via the Tree View. 

2. From within the Tree View, select **gallery_Customers**. 

3. In the right-hand screen, switch to the **Advanced** tab. Select **Items** from within the Property drop down and set the value to: 

	**SortByColumns(Search(Customer, TextSearchBox1.Text, "FullName"), "Loyalty_Customers_LoyaltyId")** 

	This is connecting to the **Customer** data entity we created the previous Task. The data for this gallery is being pulled from the Unified Customer Profile. There is a formula attached to Items property to filter using the search bar text. 

4. You are going to update the Customer gallery to show a customer's Full Name, email address and Contoso Club ID. 

	With the gallery_Customers gallery still selected, sreturn to the **Properties** tab. Select **Fields > Edit** .


	| Property| Value |
	| - | - |
	| **Layout**| **Title, Subtitle and body** |
	| **Field**(click Edit)| lbl_CustomerName - **FullName** |
	| **Field**(click Edit)| lbl_CustomerNo - **Loyalty_Customers_LoyaltyId** |
	| **Field**(click Edit)| lbl_email - **EMail** |

	You should now see that the Customer Gallery is populated with the names, email and loyalty scheme IDs of Contoso Coffee customers, using our Unified Profiles from Customer Insights. 

5. Next, we will setup the Customer Search screen to show some key info from the customer's profile when the greeter selects them in the gallery. 

6. Within the Tree View, select **lbl_Email** (outside of the gallery) and set the **Text** Property of the label by clicking the **Text** box and then copy/pasting the following into the formula bar at the top of the app: 
 
`gallery_Customers.Selected.EMail`

6. Within the Tree View select **lbl_FullName** and set the **Text** Property of the label by clicking the **Text** box and then copy/pasting the following into the formula bar at the top of the app:

`gallery_Customers.Selected.FullName`

7. Within the Tree View select **lbl_CustomerAddress**  and set the **Text** Property of the label by clicking the **Text** box and then copy/pasting the following into the formula bar at the top of the app:

`Concatenate(gallery_Customers.Selected.StreetAddress, " 
", gallery_Customers.Selected.City," 
", gallery_Customers.Selected.State, " 
", gallery_Customers.Selected.PostCode, " 
", gallery_Customers.Selected.Country)`
 
8. Finally, within the Tree View select the **img_CustomerProfile** image and set the **Image** Property of the label by clicking the **Image** box and then copy/pasting the following into the formula bar at the top of the app:

`gallery_Customers.Selected.Headshot`
 
Congratulations, you have now configured the Customer Search screen within the Greeter App. In the next Task, we will configure different aspects of the Customer Profile Screen. 


## Task 4 - Configure the Customer Profile Screen 

Here we will embed the same Customer Profile data as we did in the Customer Search screen, before moving on to embed a unified view of interactions as well as KPIs and recommendations. 

1. With the Power App in Edit mode, select the **CustomerProfile_Screen** from the Tree View on the left menu. 

2. First, you'll add customer information from the Unified Profile as per the Customer Search Screen. 

- Within the Tree View select **lbl_emailAddress**. Set the **Text** property (the same way we did in Task 3) to:

`gallery_Customers.Selected.EMail`


- Select **lbl_CustomerFullname** and set the **Text** Property of the label to:

`gallery_Customers.Selected.FullName`

- Within the Tree View select **lbl_LoyaltyID** and set the **Text** property of the label to:

`gallery_Customers.Selected. Loyalty_Customers_LoyaltyId`

 

- Within the Tree View select **lbl_Cust_Address** and set the **Text** property of the label to:
 
`Concatenate(gallery_Customers.Selected.StreetAddress, " 
", gallery_Customers.Selected.City," 
", gallery_Customers.Selected.State, " 
", gallery_Customers.Selected.PostCode, " 
", gallery_Customers.Selected.Country)`

 
3. Finally, within the Tree View select the **img_CustomerProfileImage** and set the Image property to:

`gallery_Customers.Selected.Headshot`

# Task 5 - Embed Unified Activities 

In this task we will embed a unified timeline of activities ingested into Customer Insights within the Customer Profile Screen. This will give Contoso Coffee retail staff visibility of any recent interactions. 
 
1. Within the Greeter Power App in Edit mode, open the **CustomerProfile_Screen screen** via the Tree View and select the **gallery_UnfiedTimeLine**. 


2. With the gallery selected, click the **Advanced** tab in the right pane and select the **Items** property. Enter the following within the formula bar to filter all Unified Customer Activity records to only display the top 100 for the current Customer Profile.
 
`FirstN(Filter(UnifiedActivity, CustomerId = gallery_Customers.Selected.CustomerId),100)`

3. Set the properties shown by selecting them within the tree under the gallery_UnifiedTimeLine and setting the Text property.

- **Title2**: `ThisItem.Title`   
- **Subtitle2**: `Text(DateTimeValue(ThisItem.ActivityTime, "en-US"), DateTimeFormat.ShortDate)` 

## Task 6 - Embed KPIs to Profile Page 

In this task you will embed key customer KPIs that we calculated as 'Customer Measures' in Lab 4A. Namely, Total Club Points (Loyalty Scheme Points) and **Customer Lifetime Spend.** 

Contoso Club Loyalty Points 

1. Within the Greeter Power App in Edit mode, open the **CustomerProfile_Screen screen** via the Tree View and select the gallery **gallery_ClubPoints**. 
 
2. Set the Items value using the property selector to the below value: 

	`Filter(Customer_Measure, CustomerId = gallery_Customers.Selected.CustomerId)`

3. Expand the **gallery_ClubPoints** and select **lbl_Points** inside the gallery. Select the **Text** property from the drop down. Set the formula as follows to display the contacts corresponding TotalClubPoints: 
 
	`ThisItem.TotalClubPoints` 

### Contoso Lifetime Value / Spend 

1. Within the Greeter Power App in Edit mode, open the **CustomerProfile_Screen** screen via the Tree View and select the gallery **gallery_CLTV**. 

2. Set the **Items** value using the property selector to: 

	`Filter(Customer_Measure, CustomerId = gallery_Customers.Selected.CustomerId)`

3. Expand the **gallery_CLTV gallery** and select **lbl_CLTV** inside the gallery. Select the **Text** property from the drop down and set the formula as follows to display the contacts corresponding LifetimeSpend: 


	`ThisItem.LifetimeSpend`

From the File menu, click Save and Publish.  

## Task 7 - Test & Explore the Greeter App Experience 

Congratulations! You have now configured a simple greeter app for Contoso Coffee Retail staff. In this task, you will explore the Greeter App experience 

1. In a browser tab, navigate to https://make.powerapps.com. If required, sign in.
 
2. Click **Apps** in the left-hand menu, and then run your **Contoso Coffee Greeter App** by selecting it and clicking **Play** on the top. 

3. Imagine you are a member of Contoso Coffee Retail staff and you greet them within the store.

- Look up Abbie Moss' record (LOYID_1000) 
- Open Abbie Moss' record: 

	- **Review Activity History** 
   	- **Review Abbie's Club Balance and Lifetime Value** 
	- Combining her purchase history with insight on her 'Current Points' and 'Lifetime Value', you are able to ascertain that Abbie is both a frequent and high-value customer. 



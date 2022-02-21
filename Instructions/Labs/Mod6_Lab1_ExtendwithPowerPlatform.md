---
lab:
    title: 'Lab 6.1: Extend with the Power Platform'
    module: 'Module 6: Manage external connections with Dynamics 365 Customer Insights'
---

# Lab 6.1: Extend with the Power Platform
# Module 6: Manage external connections with Dynamics 365 Customer Insights

Having successfully ingested Contoso Coffee's data sources and created a Unified Customer Profile and calculated key measures, you are now able to leverage the insight you have generated to empower different personas within Contoso Coffee over different platforms. 

## Power BI Extensibility 
The Customer Insights Power BI Connector enables you to use the unified data that you have unlocked through the data configuration process within Microsoft Power BI to further analyze and uncover insight. 

From customer details such as roles and locations, to communication details such as email addresses and phone numbers, to unique key performance indicators (KPIs) you might have defined using the Measures page (such as Customer Lifetime Spend or Engagement Score), many insights can be uncovered. 

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

# Exercise 1 - Power BI

## Task 1: Configure Power BI Desktop

1. If you do not have Power BI Desktop installed, navigate to [https://aka.ms/pbidesktopstore](https://aka.ms/pbidesktopstore) to download and install Power BI app. If you experience issues installing Power BI Desktop using Microsoft Store, try standalone installer that can be downloaded from [https://aka.ms/pbiSingleInstaller](https://aka.ms/pbiSingleInstaller).

2. Open Power BI Desktop.
2. If you signed in into Power BI Desktop previously, select **File | Sign out** 
3. Sign in if prompted or select **File | Sign in** to sign in.  
5. Select **Sign up for Power BI** and follow the prompts to complete the sign up.
6. Open the PowerBI template .pbix file from the lab assets in Power BI Desktop. Make sure you are logged in with the admin account for your tenant. 

2. Click **Get Data** and click more and search for the **Dynamics 365 Customer Insights (Beta)** connector.
		
3. Select the connector and click **Connect**. 

4. If presented with a notice, relating to connecting to Third Party Service, click **Continue**. 

5. Connect to your Customer Insights instance using your credentials. Once connected, you will be presented with the **Navigator page**. Here you will see all the Entities, Measures and Unified Activity data objects that you are able to consume within Power BI. 
	![Picture4](Static/Lab_6_Picture4.png) 
6. Expand and select the following tables and then click **Load** 

**Measures**: 
- AverageStorePurchaseValue 
-  AverageWebPurchaseValue 
- Customer_Measure 

**Entities**: 

- Customer 
- eCommerce_Purchases 
- PoS_posPurchases UnifiedActivity: 
**UnifiedActivity**
- UnifiedActivity

## Task 2 - Add visualizations

In this task, you'll add some simple visualizations to the report. 

### Average Store and Web Purchase Values 

1. Add a **Card Control** from the **Visualizations** panel to the left side of the report. 

2. With the card control selected, drag the **AverageWebPurchaseValue** sum from **AverageWebPurchaseValue** to the **Fields** list. 
 
3. With the card control selected, click the **Format** button properties: 
	- Data Label: **Color = White** 
	- Category: **Off** 
	- Title: **On** 
	- Title: **Title Text = 'Average Online Purchases ($)'** 
	- Title: **Font Color = White** 
	- Title: **Text Size = 14 pt** 
 
4. Select the Data Card, displaying **Average Web Purchase ($)** that you've just created and copy and paste to add another data card onto the Canvas. 
	- Update the title to **Average Store Purchases ($)** 
	- Change the fields to **AverageStorePurchaseValue** 
 

### Store + Web Purchases by Month 

Contoso Coffee wants to look for seasonality within their sales figures for both online and instore sales. 

1. Make sure you don't have either of the Cards you've added selected, then add a **Stacked Area Chart** from the **Visualizations** panel next to the 'Average Online Purchases ($)' card. 
 

2. With the new chart selected, add the following under Fields: 
	- **Axis** add **PurchasedOn** from **eCommerce_Purchases** 
	   -  **Note**: remove all but month once you add it.
	- **Values** add **TotalPrice** from **eCommerce_Purchases** 

3. With the graph selected, click the **Format** button and set the following properties: 
	- X axis: **Color = White**
    - Y axis: **Color = White** 
	- Title: **Title Text = Online Purchases** 
	- Title: **Font Color = White** 
	- Title: **Text Size = 14 pt** 

4. Select the Stacked Area Chart visualization, Copy & Paste another copy. Edit the Data and formatting as follows: 
	- **Axis** add **PurchasedOn (Month)** from **PoS_posPurchases**
	- **Values** add **TotalPrice** from **PoS_posPurchases** 

5. Update the title of your new chart to **Store Purchases**.

 

### Activity Types by Volume 

1. Make sure you don't have either of the Cards or charts you've added selected and add a Pie Chart **from** the **Visualizations** panel to the left side of the report. 

2. With the Pie Chart selected, drag the following values from the **UnifiedActivity** object. 

	- Details:**Title**

	- Values: **ActivityTypeDisplay** 
	    - which will turn into **Count of ActivityTypeDisplay** when added 

	- In filters pane, check **Select all** then uncheck the blank values line for Title. 

3. With the pie chart selected, click the **Format** button and set the following properties: 

	- Legend: **On** 
	- Legend: **Color = White** 
	- Title: **Font Color = White** 
	- Title: **Text Size = 14 pt** 
	- Detail Labels: **Color = White** 
	- Background: **On** 
	- Background: **Black** 
	- Background: **Transparency: 80%** 

### Activity Types by Month 

1. Add a Line Chart **from** the **Visualizations** panel on to the report. 

2. With the Line Chart selected, drag the following values from the **UnifiedActivity** object to the **Fields** 

	- Axis: **StartTime** 
      - Note: remove all but month once you add it 
	- Legend: **ActivityTypeDisplay** 
	- Values: **ActivityTypeDisplay**
	    which will turn into **Count of ActivityTypeDisplay** when added 

3. With the Line Chart selected, click the **Format** button and set the following properties: 
	- Legend: **Color = White** 
	- X axis: **Color = White** 
	- Y axis: **Color = White** 
	- Title: **Color = White** 
	- Background: **On** 
	- Background: **Black** 
	- Background: **Transparency: 80%** 
 

## Task 3 - Review Dashboard 

Review your Power BI dashboard. This is a simple example, but insights could become much more complex with a more detailed report.

This simple report highlights: 

- Average Online Purchase value is higher than In Store 
- There is a higher volume of In Store Purchases vs Online 
- There may be some seasonal trends as sales drop around March and increase again from September. 
 
 
# Exercise 2 - Power Automate
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

	- **To**: Email address (you can use a personal email address or your M365 credential email address) 

	- **Subject**: Churn Customers Surge Alert!

	- **Body**: Customers in segment HighRiskForChurn has crossed the threshold. Review the customer list. 

12. Click **Save**.

13. To test your Power Automate flow, go back to your Customer Insights environment and edit your **High Risk Transaction Churn** segment condition as ChurnScore greater than 0.5 instead of 0.6 which adds some more customers to your segment and triggers this Power Automate. 

You should receive an email once the segment is refreshed. 

# Exercise 2 - Power App

To create the Contoso Coffee Greeter App from this lab, you will import a template app and connect the App to Customer Insights and Flow. 

## Task 1 - Import the Greeter App Template 

1. Sign in to https://make.powerapps.com and select your Customer Insights environment if it is not already selected.

2. Click **Apps** in the left-hand menu, and then click **Import canvas app** from the top menu bar. 

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

	`SortByColumns(Search(Customer, TextSearchBox1.Text, "FullName"), "Loyalty_Customers_LoyaltyId")`

4.This is connecting to the **Customer** data entity we created the previous Task. The data for this gallery is being pulled from the Unified Customer Profile. There is a formula attached to Items property to filter using the search bar text. 

4. You are going to update the Customer gallery to show a customer's Full Name, email address and Contoso Club ID. With the gallery_Customers gallery still selected, return to the **Properties** tab. Select **Fields > Edit** .

	- lbl_CustomerName: `FullName`
	- lbl_CustomerNo: `Loyalty_Customers_LoyaltyId`
	- lbl_email - `EMail`

5. You should now see that the Customer Gallery is populated with the names, email and loyalty scheme IDs of Contoso Coffee customers, using our Unified Profiles from Customer Insights. 

5. Next, we will setup the Customer Search screen to show some key info from the customer's profile when the greeter selects them in the gallery. 

6. Within the Tree View, select **lbl_Email** (outside of the gallery) and set the **Text** Property of the label by clicking the **Text** box and then copy/pasting the following into the formula bar at the top of the app: 
 
	`gallery_Customers.Selected.EMail`

6. Within the Tree View select **lbl_FullName** and set the **Text** Property of the label by clicking the **Text** box and then copy/pasting the following into the formula bar at the top of the app:

	`gallery_Customers.Selected.FullName`

7. Within the Tree View select **lbl_CustomerAddress**  and set the **Text** Property of the label by clicking the **Text** box and then copy/pasting the following into the formula bar at the top of the app:

	`Concatenate(gallery_Customers.Selected.StreetAddress, " ", gallery_Customers.Selected.City," ", gallery_Customers.Selected.State, " ", gallery_Customers.Selected.PostCode, " ", gallery_Customers.Selected.Country)`
 
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
 
	`Concatenate(gallery_Customers.Selected.StreetAddress, " ", gallery_Customers.Selected.City," ", gallery_Customers.Selected.State, " ", gallery_Customers.Selected.PostCode, " ", gallery_Customers.Selected.Country)`

 
3. Finally, within the Tree View select the **img_CustomerProfileImage** and set the Image property to:

	`gallery_Customers.Selected.Headshot`

# Task 5 - Embed Unified Activities 

In this task we will embed a unified timeline of activities ingested into Customer Insights within the Customer Profile Screen. This will give Contoso Coffee retail staff visibility of any recent interactions. 
 
1. Within the Greeter Power App in Edit mode, open the **CustomerProfile_Screen screen** via the Tree View and select the **gallery_UnifiedTimeLine**. 

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



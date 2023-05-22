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

Contoso wants to capture in-store interactions with their customers. You are charged with enabling Contoso Retail staff to capture 'Customer Check In' activities and deliver personalized recommendations to customers. 

In this module, you will create a custom 'Check In' activity within Dynamics 365 to store details of customer store visits. You will enable Contoso Retail staff to capture these check ins using a planned 'Greeter App' and Power Automate, including details of the subjects discussed with the customer. 

In this Module you will create the custom 'Check In' activity and configure a Flow to capture a customer check in, to be triggered from a planned 'Greeter App'. 

In this module you will also create a Flow to generate personalized recommendations that can be surfaced within Dynamics 365 or the Greeter App using Insight Cards. 


## Power Apps Extensibility 

Contoso want to deliver personalized service and recommendations to customers who visit their retail stores and coffee shop's and capture details of customers visiting their stores. To do this, they have decided to empower their Contoso Coffee Retail staff with a greeter app, empowering staff to have a more informed conversation with customers and deliver personalized service and recommendations. 

As Project Manager for Contoso Coffee, you will create the 'Greeter App' using Power Apps for Contoso retail staff who will be able to look up unified customer profiles, capture customer check ins and deliver personalized recommendations to customers. 


## Objectives 

- Create a Power Automate to configure 'Churn Customers Surge Alert' 

- Create Contoso Coffee Greeter App using PowerApps 

- Connect app with Customer Insights Unified Profile 


# Exercise 1 - Power BI

## Task 1: Configure Power BI Desktop 

1.  If you do not have Power BI Desktop installed, navigate to [https://aka.ms/pbidesktopstore](https://aka.ms/pbidesktopstore) to download and install Power BI app. 

    If you experience issues installing Power BI Desktop using Microsoft Store, try standalone installer that can be downloaded from [https://aka.ms/pbiSingleInstaller](https://aka.ms/pbiSingleInstaller). 

2.  Open Power BI Desktop. 

3.  If you were already signed into Power BI Desktop previously, select **File | Sign out**. 

4.  Select **Get started**. Sign in if prompted or select **File | Sign in** to sign in using your M365 credential. 

5.  Open the **PowerBI_template.pbix file** from the **Lab Resources** folder in Power BI Desktop. Make sure you are logged in as an admin account for your tenant. 

6.  Select **Get data** from the toolbar and choose **More...** in the drop-down. Search for the **Dynamics 365 Customer Insights (Beta)** connector.
		
7.  Select the connector and select the **Connect** button. 

8.  If presented with a notice relating to connecting to Third Party Service, select **Continue**. 

9.  Select **Sign in** to connect to your Customer Insights instance using your credentials and select **Connect**. Once connected, you will be presented with the **Navigator page**. Here you will see all the Entities, Measures and Unified Activity data objects that you are able to consume in Power BI. 

10. Expand and select the following tables:  

    **Entities**: 

    - Customer 
    - eCommerce_Purchases 
    - PoS_posPurchases 

    **Measures**: 
    - AverageStorePurchaseValue 
    -  AverageWebPurchaseValue 
    - Customer_Measure 

    **UnifiedActivity**:
    - UnifiedActivity

11. Select **Load**. 


## Task 2 - Add visualizations

In this task, you'll add some simple visualizations to the report. 

### Average Store and Web Purchase Values 

1.  Add a **Card** control from the **Visualizations** pane. Resize the Card control to take up the left side of the Report canvas. 

2.  With the card control selected, expand the **AverageWebPurchaseValue** table in the **Data** pane and drag the **Σ AverageWebPurchaseValue** sum to the **Fields** list. 

3.  With the card control selected, select the **Format your visual** button from the **Visualizations** pane on the right. Edit the following properties: 

    - Visual > Callout value > Color: **White** 

    - Visual > Category label: **Off** 

    - General > Title: **On** 
    
    - General > Title > Text: `Average Online Purchases ($)` 

    - General > Title > Text color: **White** 
    
    - General > Title > Text Size: **14 pt** 
 
    - General > Effects > Background: **On** 

    - General > Effects > Background: Color = **Black** 

4.  Select the Data Card displaying **Average Web Purchase ($)** that you've just created and copy and paste to add another data card onto the Canvas. Move it to the right of the canvas. 
 
    - Update the **Title > Text** to `Average Store Purchases ($)` 

    - Change the **Fields** to **Σ AverageStorePurchaseValue**. 


### Store + Web Purchases by Month 

Contoso Coffee wants to look for seasonality within their sales figures for both online and in-store sales. 

1.  Make sure you don't have either of the Cards you've added selected, then add a **Stacked Area Chart** from the **Visualizations** pane next to the **Average Online Purchases ($)** card. 

2.  With the new chart selected, add the following under Fields: 
	
    - **X-Axis**: Add **PurchasedOn** from **eCommerce_Purchases** 

    -  **Note**: remove all but **Month** once you add it.

    - **Y-Axis**: Add **Σ TotalPrice** from **eCommerce_Purchases** 

3.  With the graph selected, select **Format your visual** and set the following properties: 

    - X-axis > Values: **Color = White**

    - Y axis > Values: **Color = White** 

    - General > Title: **Text** = `Online Purchases` 

    - General > Title: **Text color = White** 

    - General > Title: **Text size = 14 pt** 

    - General > Effects > Background: **On** 

    - General > Effects > Background: Color = **Black** 

4.  Select the **Stacked Area Chart** visualization, select copy & paste it below. Edit the Data and formatting as follows: 

    - **X-axis**: Add **PurchasedOn (Month)** from **PoS_posPurchases**

    - **Y-axis**: **TotalPrice** from **PoS_posPurchases** 

5.  Update the **Title** of your new chart to `Store Purchases`.


### Activity Types by Volume 

1.  Make sure you don't have either of the Cards or Charts you've added selected and add a **Pie chart** from the **Visualizations** pane. 

2.  With the **Pie chart** selected, drag the following values from the **UnifiedActivity** object: 

    - Details: **Title**. 

    - Values: **ActivityTypeDisplay**, which will turn into **Count of ActivityTypeDisplay** when added. 

3.  With the pie chart selected, select the **Format your visual** button and set the following properties: 

    - Visual > Legend: **On** 

    - Visual > Legend > Text: **Color = White** 

    - Visual > Detail labels > Values: **Color = White** 

    - General > Title > Text: `Activity Types by Volume` 

    - General > Title: **Text color = White** 

    - General > Title: **Font size = 14 pt** 

    - General > Effects > Background: **On** 

    - General > Effects > Background: Color = **Black** 


### Activity Types by Month 

1.  Add a **Line chart** from the **Visualizations** panel on to the report. 

2.  With the **Line chart** selected, drag the following values from the **UnifiedActivity** object to the **Fields**: 

    - X-axis: **StartTime** 

    > **Note:** Remove all but Month once you add StartTime.
 
    - Legend: **ActivityTypeDisplay** 

    - Y-axis: **ActivityTypeDisplay**, which will turn into **Count of ActivityTypeDisplay** when added. 

3.  With the Line Chart selected, select the **Format your visual** button and set the following properties: 

    - Visual > Legend > Text: Color = **White** 

    - Visual > X-axis > Values: **Color = White** 

    - Visual > Y-axis > Values: **Color = White** 

    - General > Title > Text: `Activity Types by Month` 

    - General > Title: **Font size = 14 pt** 

    - General > Title > Text color: **White** 

    - General > Effects > Background: **On** 

    - General > Effects > Background: Color = **Black** 


## Task 3 - Review Dashboard 

Review your Power BI dashboard. This is a simple example, but insights could become much more complex with a more detailed report. 

This simple report highlights: 

- Average Online Purchase value is higher than in Store. 

- There is a higher volume of In Store Purchases vs Online. 

- There may be some seasonal trends as sales drop around March and increase again from September. 


# Exercise 2 - Power Automate

In this task you will create a Flow, which will be triggered in a later Module from a PowerApp by Contoso Retail staff who interact with Contoso Coffee Customers, in order to capture a record of that customer having visited. 

1.  Navigate to `https://make.powerapps.com` and sign in if prompted. Select the **Marketing Trial** environment from the drop-down menu at the top right of screen. 

2.  From the left navigation menu, select **Flows**. (If prompted, confirm the **Country** and select **Get started**.) 

3.  Select **+ New flow** and then select **Instant cloud flow** from the drop-down.

4.  Select **Skip**. 

5.  Name your flow at the top by double-clicking on **Untitled** and entering `ChurnCustomersSurgeAlert` 

6.  Within the **Search connectors and triggers** search bar, search for `Dynamics 365 Customer Insights`. In the triggers box, find **Triggers a flow when a segment threshold is crossed (preview)** and select it.

7.  You may be signed into your Customer Insights instance automatically, or you may need to sign in manually. After you've been authenticated, select your instance from the drop-down. 

    > **Note**: Be sure to set the threshold to a number slightly larger than the current number of members in your segment so the trigger is hit later when we change the segment setting. 

    - Instance: **YourName CI ILT Lab** 

    - Segment: `HighRiskTransactionChurn` 

    - Threshold: `1200` 

8.  Select **+ New step**. In the **Search connectors and actions** search bar, search for `Send an email (V2)`, and select it. You may be signed into Outlook automatically, or you may need to sign in manually using your M365 credential. 

9.  Enter the following: 

    - **To**: Email address (you can use a personal email address or your M365 credential email address) 

    - **Subject**: `Churn Customers Surge Alert!`

    - **Body**: `Customers in segment HighRiskForChurn has crossed the threshold. Review the customer list.` 

10. Select **Save**. 

11. To test the Power Automate flow, go back to your Customer Insights environment and edit your **High Risk Transaction Churn** segment condition as ChurnScore greater than `0.5` instead of 0.6 which adds some more customers to your segment and should trigger this Power Automate flow. 

    You should receive an email once the segment is refreshed. 


# Exercise 2 - Power App

To create the Contoso Coffee 'Greeter App' from this lab, you will import a template app and connect the App to Customer Insights and Flow. 

## Task 1 - Import the Greeter App Template 

1.  Sign in to `https://make.powerapps.com` and select the **Marketing Trial** environment, if it is not already selected. 

2.  Select **Apps** in the left navigation menu, and then select **Import canvas app** from the command bar. 

3.  Select the **Upload** button and select the **CustomerInsightsGreeterApp.zip** included in the Lab Resources, then select **Upload**. 

4.  Select **Import**. 

    > **Note:** If **Import** is grayed out and **Import Setup** says Update, then select **Update** and change it to **Create as new**. 

5.  Once the package has imported, select the **Open app** link. 

    > **Note:** If you are prompted with the Welcome pop-up, select **Get started** and/or **Skip**. 


## Task 2 - Connect to Data Source(s) 

In this task, we will use the Customer Insights Connector to connect the 'Greeter App' to your Customer Insights instance. 

1.  From the command bar, select **Add data**. 

2.  Select the **Dynamics 365 Customer Insights** connector. 

3.  Select the **Customer** and **UnifiedActivity** tables. Enter `Customer_Measure` into the **Enter custom table name** box and check the corresponding box. Then select **Connect**. 

4.  You should see three new tables added as data sources. Close the **Data** pane.

Congratulations! You have established a connection to Customer Insights from the Power App. 


## Task 3 - Configure the Customer Search Screen 

In this task you are going to connect Customer Insights data to the Customer Search and Customer Profile screens within the greeter app. This will enable Contoso Coffee Retail staff to find and view customer information when they greet them in store. 

1.  With the 'Greeter App' open in Edit mode, open and expand the **CustomerSearch_Screen** screen in the **Tree View**. 

2.  Select **gallery_Customers**. 

3.  In the right-hand screen, switch to the **Advanced** tab. Select **Items** from within the Property drop down and set the value to: 

    `SortByColumns(Search(Customer, TextSearchBox1.Text, "FullName"), "Loyalty_Customers_LoyaltyId")`

    This is connecting to the **Customer** data entity from the previous task. The data for this gallery is being pulled from the **Unified Customer Profile**. There is a formula attached to the **Items** property to filter using the search bar text. 

4.  You are going to update the **Customer gallery** to show a customer's Full Name, Email address and Contoso Club ID. With the **gallery_Customers** gallery still selected, return to the **Properties** tab. Select **Fields > Edit**. 

    - lbl_CustomerName: `FullName`

    - lbl_CustomerNo: `Loyalty_Customers_LoyaltyId`

    - lbl_email - `EMail`

    You should now see that the Customer Gallery is populated with the full names, emails and loyalty scheme IDs of Contoso Coffee customers, using the Unified Customer Profiles from Customer Insights. 

5.  Next, we will setup the **Customer Search** screen to show some key info from the customer's profile when the greeter selects them from the gallery. 

6.  In the Tree View, select **lbl_Email** (outside of the gallery) and set the **Text** Property of the label by selecting the **Text** box and then copy/pasting the following into the formula bar at the top of the app: 
 
    `gallery_Customers.Selected.EMail`

7.  In the Tree View, select **lbl_FullName** and set the **Text** property of the label by selecting the **Text** box and then entering the following formula into the formula bar at the top of the app: 

    `gallery_Customers.Selected.FullName`

8.  In the Tree View, select **lbl_CustomerAddress** and set the **Text** Property of the label by selecting the **Text** box and then entering the following formula into the formula bar at the top of the app:

    `Concatenate(gallery_Customers.Selected.StreetAddress, " ", gallery_Customers.Selected.City," ", gallery_Customers.Selected.State, " ", gallery_Customers.Selected.PostCode, " ", gallery_Customers.Selected.Country)`
 
9.  Finally, within the Tree View select the **img_CustomerProfile** image and set the **Image** Property of the label by select the **Image** box and then entering the following into the formula bar at the top of the app:

	`gallery_Customers.Selected.Headshot`
 
Congratulations, you have now configured the **Customer Search** screen in the Greeter App. In the next task, we will configure different aspects of the Customer Profile Screen. 


## Task 4 - Configure the Customer Profile Screen 

Here we will embed the same Customer Profile data as we did in the Customer Search screen, before moving on to embed a unified view of interactions as well as KPIs and recommendations. 

1.  With the Power App open in Edit mode, select and expand the **CustomerProfile_Screen** screen from the **Tree View** on the left navigation menu. 

2.  First, you'll add customer information from the Unified Profile as per the CustomerSearch_Screen screen. From the **Tree View**, select **lbl_emailAddress**. Set the **Text** property to the following formula: 

    `gallery_Customers.Selected.EMail` 

3.  Select **lbl_CustomerFullname** and set the **Text** property to: 

    `gallery_Customers.Selected.FullName` 

 4.  In the **Tree View**, select **lbl_LoyaltyID** and set the **Text** property to: 

    `gallery_Customers.Selected.Loyalty_Customers_LoyaltyId` 

 5.  In the **Tree View**, select **lbl_Cust_Address** and set the **Text** property to: 
 
    `Concatenate(gallery_Customers.Selected.StreetAddress, " 
    ", gallery_Customers.Selected.City," 
    ", gallery_Customers.Selected.State, " 
    ", gallery_Customers.Selected.PostCode, " 
    ", gallery_Customers.Selected.Country)` 
 
6.  Finally, in the **Tree View**, select the **img_CustomerProfileImage** and set the **Image** property to: 

    `gallery_Customers.Selected.Headshot` 


# Task 5 - Embed Unified Activities 

In this task we will embed a unified timeline of activities ingested into Customer Insights within the Customer Profile Screen. This will give Contoso Coffee retail staff visibility of any recent interactions. 
 
1.  With the Greeter Power App open in Edit mode, open and expand the **CustomerProfile_Screen** screen from the **Tree View** and select the **gallery_UnifiedTimeLine**. 

2.  With the gallery selected, select the **Advanced** tab in the right pane and select the **Items** property. Enter the following in the formula bar to show the top 100 Unified Customer Activity records for the current Customer Profile. 
 
    `FirstN(Filter(UnifiedActivity, CustomerId = gallery_Customers.Selected.CustomerId),100)` 

3.  Expand the **gallery_UnifiedTimeLine** gallery and select the **Title2** label. Set the **Text** property to:

    `ThisItem.Title`   
	
4.  From the **Tree view**, select the **Subtitle2** label and set the **Text** property to:

    `Text(DateTimeValue(ThisItem.ActivityTime, "en-US"), DateTimeFormat.ShortDate)` 


## Task 6 - Embed KPIs to Profile Page 

In this task you will embed key customer KPIs that we calculated as 'Customer Measures' in Lab 4A. Namely, **Total Club Points (Loyalty Scheme Points)** and **Customer Lifetime Spend**. 

### Contoso Club Loyalty Points 

1.  With the 'Greeter App' open in Edit mode, open and expand the **CustomerProfile_Screen** screen from the **Tree view** and select the gallery **gallery_ClubPoints**. 
 
2.  On the **Advanced** Tab, set the **Items** property to: 

    `Filter(Customer_Measure, CustomerId = gallery_Customers.Selected.CustomerId)` 

3.  Expand the **gallery_ClubPoints** gallery and select the **lbl_Points** label inside the gallery. Select the **Text** property from the drop-down. Set the formula as follows to display the contacts corresponding TotalClubPoints: 
 
    `ThisItem.TotalClubPoints` 


### Contoso Lifetime Value / Spend 

1.  With the 'Greeter App' open in Edit mode, open and expand the **CustomerProfile_Screen** screen from the **Tree view** and select the gallery **gallery_CLTV**. 

2.  Set the **Items** value using the property selector to: 

    `Filter(Customer_Measure, CustomerId = gallery_Customers.Selected.CustomerId)`

3.  Expand the **gallery_CLTV gallery** and select **lbl_CLTV** inside the gallery. Select the **Text** property from the drop down and set the formula as follows to display the contacts corresponding LifetimeSpend: 

    `Concatenate("$",ThisItem.LifetimeSpend)`

4.  From the command bar, select **Save** and **Publish**. Select **Publish this version**. 

Congratulations! You have now configured a simple greeter app for Contoso Coffee Retail staff. 


## Task 7 - Test & Explore the Greeter App Experience 

In this task, you will explore the Greeter App experience. 

1.  In a new browser tab, navigate to `https://make.powerapps.com`. If required, sign in and make sure to select the **Marketing Trial** environment. 

    > **Note:** By default the environment selected is **Contoso (default)**. 
 
2.  Select **Apps** from the left navigation menu, and then run your **Contoso Coffee Greeter App** by selecting it and selecting **Play** from the toolbar. To give location permissions to the app, select **Allow**. 

3.  Imagine you are a member of Contoso Coffee Retail staff and you greet customers in the store. 

    - Select **Customer Search** and search for `Abbie Moss` (LOYID_1000) 

    - Open Abbie Moss' record. 

    - Review the **Activity** gallery. 

    - Combining their purchase history with insights on their **Current Points** and **Lifetime Value**, you are able to ascertain that Abbie is both a frequent and high-value customer. 


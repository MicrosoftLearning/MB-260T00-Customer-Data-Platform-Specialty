---
lab:
    title: 'Lab 6.2: Extend with the Power Platform'
    module: 'Module 6: Manage external connections with Dynamics 365 Customer Data Platform'
---

# Lab 6.2: Extend with the Power Platform
# Module 6: Manage external connections with Dynamics 365 Customer Data Platform

Having successfully ingested Contoso Coffee's data sources and created a Unified Customer Profile and calculated key measures, you are now able to leverage the insight you have generated to empower different personas within Contoso Cofee over different platforms. 

## Power BI Extensibility 
The Customer Insights Power BI Connector enables you to use the unified data that you have unlocked through the data configuration process within Microsoft Power BI to further analyze and uncover insight. 

From customer details such as roles and locations, to communication details such as email addresses and phone numbers, to unique key performance indicators (KPIs) you might have defined using the Measures page (such as Customer Lifetime Spend or Engagement Score), many insights can be uncovered. 
![Picture1](Static/Lab_6_Picture1.png) 

## Power Automate Extensibility 
Contoso want to capture in-store interactions with their customers. You are charged with enabling Contoso Retail staff to capture 'Customer Check-In' activities and deliver personalized recommendations to customers. 

In this Module you will create a custom 'Check In' activity within Dynamics 365 to store details of customer store visits. You will enable Contoso Retail staff to capture these check ins using a planned 'Greeter App' and Power Automate, including details of the subjects discussed with the customer. 

In this Module you will create the custom 'Check In' activity and configure a Flow to capture a customer check in, to be triggered from a planned 'Greeter App'. 

In this module you will also create a Flow to generate personalized recommendations that can be surfaced within Dynamics 365 or the Greeter App using Insight Cards. 

## Power App Extensibility 

Contoso want to deliver personalized service and recommendations to customers who visit their retail stores and coffee shop's and capture details of customers visiting their stores. To do this, they have decided to empower their Contoso Coffee Retail staff with a greeter app, empowering staff to have a more informed conversation with customers and deliver personalized service and recommendations. 

![Picture 225](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image1.jpeg)As Project Manager for Contoso Coffee, you will create a Greeter App using Power Apps for Contoso retail staff who will be able to look-up unified customer profiles, capture customer check-ins and deliver personalized recommendations to customers. 

## Objectives 

- Connect Power BI to Customer Insights 

- Visualise Customer Insights Data 

- Create a Power Automate to configure 'Churn Customers Surge Alert' 

- Create Contoso Coffee Greeter App using PowerApps 

- Connect app with Customer Insights Unified Profile 

## Prerequisites 

To complete the course you will need the following 

- **Dynamics 365 Marketing** Instance or Trial 
- Access to **Power Apps** or a Power Apps Trial 
- Access to **Power Automate** or a Power Automate Trial 
- Access to **Power BI** or a Power BI Trial 
- **Customer Insights** Trial 

If you do not have access to the above, you can follow Lab 3 to get setup. 

# Approximate Time:  90 min  
# Exercise 1 - Power BI
## Task 1 - Connect to Customer Insights 

1. Open the PowerBI template .pbix file from the lab assets in Power BI Desktop. Make sure you are logged in with the admin account for your tenant. (Top right) 

2. Click **Get Data** and click more and search for the **Dynamics 365 Customer Insights (Beta)** connector.

	![Picture2](Static/Lab_6_Picture2.png) 
	![Picture3](Static/Lab_6_Picture3.png) 		
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

![Picture5](Static/Lab_6_Picture5.png)

 

## Task 2 - Add Visualizations 

In this task, you'll add some simple visualizations to the report. 

### Average Store and Web Purchase Values 

1. Add a **Card Control** from the **Visualizations** panel to the left side of the report. 
	![Pictuer6](static/Lab_6_Picture6.png)

2. With the card control selected, drag the **AverageWebPurchaseValue** sum from **AverageWebPurchaseValue** to the **Fields** list. 
	![Pictuer7](static/Lab_6_Picture7.png)
 
3. With the card control selected, click the **Format** button properties: 
	- Data Label: **Color = White** 
	- Category: **Off** 
	- Title: **On** 
	- Title: **Title Text = 'Average Online Purchases ($)'** 
	- Title: **Font Color = White** 
	- Title: **Text Size = 14 pt** 
![Pictuer8](static/Lab_6_Picture8.png)
 
4. Select the Data Card, displaying **Average Web Purchase ($)** that you've just created and copy and paste to add another data card onto the Canvas. 
	- Update the title to **Average Store Purchases ($)** 
	- Change the fields to **AverageStorePurchaseValue** 

You should now have a screen that looks like this. 

![Picture 485](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image2.jpeg) 

 

  

### Store + Web Purchases by Month 

Contoso Coffee wants to look for seasonality within their sales figures for both online and instore sales. 

1. Make sure you don't have either of the Cards you've added selected, then add a **Stacked Area Chart** from the **Visualizations** panel next to the 'Average Online Purchases ($)' card. 
	![Pictuer9](static/Lab_6_Picture9.png)
 

2. With the new chart selected, add the following under Fields: 
	- **Axis** add **PurchasedOn** from **eCommerce_Purchases** 
	   -  **Note**: remove all but month once you add it 

	- **Values** add **TotalPrice** from **eCommerce_Purchases** 

	![Picture 551](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image3.jpeg) 

3. With the graph selected, click the **Format** button  
	and set the following properties: 
	- X axis: **Color = White**
    - Y axis: **Color = White** 
	- Title: **Title Text = Online Purchases** 
	- Title: **Font Color = White** 
	- Title: **Text Size = 14 pt** 
	![Pictuer10](static/Lab_6_Picture10.png)

4. Select the Stacked Area Chart visualization, Copy & Paste another copy. Edit the Data and formatting as follows: 
	- **Axis** add **PurchasedOn (Month)** from **PoS_posPurchases**
	- **Values** add **TotalPrice** from **PoS_posPurchases** 

5. Update the title of your new chart to **Store Purchases** 

   Your dashboard will now look like this: 
	![Picture 627](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image5.jpeg) 

 

### Activity Types by Volume 

1. Make sure you don't have either of the Cards or charts you've added selected and add a Pie Chart **from** the **Visualizations** panel to the left side of the report. 

 ![Pictuer11](static/Lab_6_Picture11.png)

2. With the Pie Chart selected, drag the following values from the **UnifiedActivity** object. 

	- Details:**Title**

	- Values: **ActivityTypeDisplay** 
	    - which will turn into **Count of ActivityTypeDisplay** when added 

	- In filters pane, check **Select all** then uncheck the blank values line for Title. 

![Picture 737](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image6.jpeg) 
![Pictuer12](static/Lab_6_Picture12.png)

3. With the pie chart selected, click the **Format** button and set the following properties: 
	![Picture 739](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image7.jpeg)
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
	![Pictuer13](static/Lab_6_Picture13.png)
 
2. With the Line Chart selected, drag the following values from the **UnifiedActivity** object to the **Fields** 

	- Axis: **StartTime** 
      - Note: remove all but month once you add it 
	- Legend: **ActivityTypeDisplay** 
	- Values: **ActivityTypeDisplay**
	    which will turn into **Count of ActivityTypeDisplay** when added 

3. With the Line Chart selected, click the **Format** button ![Picture 840](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image8.jpeg) and set the following properties: 
	- Legend: **Color = White** 
	- X axis: **Color = White** 
	- Y axis: **Color = White** 
	- Title: **Color = White** 
	- Background: **On** 
	- Background: **Black** 
	- Background: **Transparency: 80%** 

	![Pictuer14](static/Lab_6_Picture14.png)
 

## Task 3 - Review Dashboard 

Review your Power BI dashboard. This is simple example, pulling data from Customer Insights, further insight could be uncovered with more complex example. 

This simple report highlights: 

- Average Online Purchase value is higher than In Store 
- There is a higher volume of In Store Purchases vs Online 
- There may be some seasonal trends as sales drop around March and increase again from September. 
	![Pictuer34](static/Lab_6_Picture34.png)
 
# Exercise 2 - Power Automate
In this task you will create a Flow, which will be triggered in a later Module from a PowerApp by Contoso Retail staff who interact with Contoso Coffee Customers, in order to capture a record of that customer having visited. 

1. In a new Browser tab, navigate to https://flow.microsoft.com 

2. Select the right environment on top right from the drop down. 

3. From the left hand menu, click **Create**. 

4. Click **Instant cloud flow** 

5. Click **Skip**. 

6. Name your flow on the top by double clicking on **Untitled** as **ChurnCustomersSurgeAlert** 

7. With in the PowerAutomate search bar, search for Dynamics 365 Customer Insights and select it. With in triggers, select the **Triggers a flow when segment threshold is crossed**. 

	![Pictuer15](static/Lab_6_Picture15.png)

8. If prompted start trial for Power Automate. 

9. Sign in if prompted. Select your instance from the drop down. 

- Segment : **HighRiskTransactionChurn** 

- Threshold: **1200** 

**Note**: Be sure to set the threshold to a number slightly larger than the current number of members in your segment so the trigger is hit later when we change the segment setting. 

10. Click **New step**. In the Choose an action step, search for **Send an email (V2)**, select it and sign in with your outlook account and accept the consent if prompted. 



11. Enter the following: 

	**To**: Email address 

	**Subject**: Churn Customers Surge Alert !!! 

	**Body**: Customers in segment HighRiskForChurn has crossed the threshold. Review the customer list. 

12. Click **Save** 

13. To test your PowerAutomate, go back to your Customer Insights environment and edit your **High Risk For Churn** segment condition as ChurnScore greater than 0.5 instead of 0.6 which adds some more customers to your segment and triggers this Power Automate. 

You should receive an email once the segment is refreshed. 

# Exercise 3 - Power App

To create the Contoso Coffee Greeter App from this lab, you will import a templated app and connect the App to Customer Insights and Flow. 


## Task 1 - Import the Greeter App Template 

1. Sign-In to https://make.powerapps.com and select the environment in which you are working (This should be the same environment that you used to create your Flows in the previous Lab). 

	![Pictuer16](static/Lab_6_Picture16.png)

2. Click **Apps** in the left-hand menu, and then click **Import Canvas App** from the top menu bar. 

	![Picture 1131](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image9.jpeg)

3. Click the **Upload** button and select the **CustomerInsightsGreeterApp.zip** included with the module content, then **Upload**. 

4. On the next page, select **Import**. If **Import** is grayed out and **Import Setup** says Update, then click **Update** under **Import Setup** and change to **Create as new**. 

	![Pictuer6](static/Lab_6_Picture17.png)

5. Once the package has completed its import, click **Apps** in the left menu, you should see your imported app listed. 

	![Picture 1191](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image10.jpeg)

6. Click the '...' icon next to its Name and select **Edit** to load the app in Edit Mode. 

	![Picture 1193](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image11.jpeg) 

## Task 2 - Connect to Data Source(s) 

In this task, we will use the Customer Insights Connector, to connect the Greeter Power App to your Customer Insights Instance. 

1. In the top menu bar, click **View** then select **Data Sources** 
2. In the **Data** menu that opens on the right, click **Add data source** 
3. Click **New Connection** and search for the **Dynamics 365 Customer Insights** connector 
4. Select the connector and then click **Connect**. If prompted, sign-in with your credentials for your Customer Insights 

	![Picture 1255](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image12.jpeg) 

5. Select **Customer, UnifiedActivity** and type **Customer_Measure** into the Enter custom table name box. Then click **Connect** 
	![Pictuer18](static/Lab_6_Picture18.png)
  

6. You should see these three tables listed as data connections within your Greeter App. 

	![Picture 1298](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image13.jpeg)
	
	Congratulations! You have established a connection to Customer Insights within your Power App. 

## Task 3 - Configure the Customer Search Screen 

In this task you are going to connect Customer Insights data to the Customer Search and Customer Profile screens within the greeter app. This will enable Contoso Coffee Retail staff to find and view customer information when they greet them in store. 

1. Within the Greeter Power App in Edit mode, open the **CustomerSearch_Screen screen** via the Tree View 

	![Picture 1296](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image14.jpeg) 

2. From within the Tree View, select **gallery_Customers**. 

	![Picture 1352](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image15.jpeg) 

3. Select **Items** from within the Property drop down and set the value to: 

	**SortByColumns(Search(Customer, TextSearchBox1.Text, "FullName"), 
	"Loyalty_Customers_LoyaltyId")** 

	This is connecting to the **Customer** data entity we created the previous Task. The data for this gallery is being pulled from the Unified Customer Profile. There is a formula attached to Items property to filter using the search bar text. 

4. You are going to update the Customer gallery to show customers Full Name, email address and Contoso Club ID. 

	With the gallery_Customers gallery selected, set the properties shown by clicking **Fields>Edit** under **Properties** as shown below... 
	![Pictuer19](static/Lab_6_Picture19.png)

	| Property| Value |
	| - | - |
	| **Layout**| **Title, Subtitle and body** |
	| **Field**(click Edit)| lbl_CustomerName - **FullName** |
	| **Field**(click Edit)| lbl_CustomerNo - **Loyalty_Customers_LoyaltyId** |
	| **Field**(click Edit)| lbl_email - **EMail** |

	You should now see that the Customer Gallery is populated with the names, email and loyalty scheme IDs of Contoso Coffee customers, using our Unified Profiles from Customer Insights. 

5. Next, we will setup the Customer Search screen to show some key info from the customers profile when the greeter selects them in the gallery. 

	**Note**: The **Text** property of any control can be selected by first selecting the respective control and picking the **Text** property from the drop down on the top. We will do these changes throughout the lab. 
	![Pictuer20](static/Lab_6_Picture20.png)

	Within the Tree View select **lbl_Email** (outside of the gallery) and set the **Text** Property of the label to **gallery_Customers.Selected.EMail** 
	![Pictuer21](static/Lab_6_Picture21.png)


6. Within the Tree View select **lbl_FullName** and set the **Text** Property of the label to **gallery_Customers.Selected.FullName** 

7. Within the Tree View select **lbl_CustomerAddress** and set the **Text** property of the label to 

	**Concatenate**(**gallery_Customers.Selected.StreetAddress, "** 
	**", gallery_Customers.Selected.City,"**
	**", gallery_Customers.Selected.State, "**
	**", gallery_Customers.Selected.PostCode, "** 
	**", gallery_Customers.Selected.Country)** 
	![Pictuer22](static/Lab_6_Picture22.png)
 
8. Finally, within the Tree View select the **img_CustomerProfile** image and set the Image property to **gallery_Customers.Selected.Headshot** 
![Pictuer23](static/Lab_6_Picture23.png)
 
	Congratulations, you have now configured the Customer Search screen within the Greeter App. In the next Task, we will configure different aspects of the Customer Profile Screen. 


## Task 4 - Configure the Customer Profile Screen 

Here we will embed the same Customer Profile data as we did in the Customer Search screen, before moving on to embed a unified view of interactions as well as KPIs and recommendations. 

1. With the Power App in Edit mode, select the **CustomerProfile_Screen** from the Tree View on the left menu. 
	![Pictuer24](static/Lab_6_Picture24.png)
 

2. First, you'll add customer information from the Unified Profile as per the Customer Search Screen. 

- Within the Tree View select **lbl_emailAddress** and set the **Text** Property of the label to **gallery_Customers.Selected.EMail** 

	![Picture 1647](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image16.jpeg) 

- Within the Tree View select **lbl_CustomerFullname** and set the **Text** Property of the label to **gallery_Customers.Selected.FullName** 


- Within the Tree View select **lbl_LoyaltyID** and set the **Text** property of the label to **gallery_Customers.Selected. Loyalty_Customers_LoyaltyId** 

 

- Within the Tree View select **lbl_Cust_Address** and set the **Text** property of the label to 

	**Concatenate(gallery_Customers.Selected.StreetAddress, "** 

	**", gallery_Customers.Selected.City,"** 

	**", gallery_Customers.Selected.State, "**

	**", gallery_Customers.Selected.PostCode, "** 

	**", gallery_Customers.Selected.Country)** 

 
3. Finally, within the Tree View select the **img_CustomerProfileImage image** and set the Image property to **gallery_Customers.Selected.Headshot** 

 

# Task 5 - Embed Unified Activities 

In this task we will embed a unified timeline of activities ingested into Customer Insights within the Customer Profile Screen. This will give Contoso Coffee retail staff visibility of any recent interactions. 

 
1. Within the Greeter Power App in Edit mode, open the **CustomerProfile_Screen screen** via the Tree View and select the **gallery gallery_UnfiedTimeLine** 

	![Picture 1733](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image17.jpeg) 

2. With the gallery selected, select the **Items** property from the property drop-down and enter the following within the formula bar to filter all Unified Customer Activity records to only display the top 100 for the current Customer Profile 

 
	**FirstN(Filter(UnifiedActivity, CustomerId = gallery_Customers.Selected.CustomerId),100)** 

 

3. Set the properties shown by selecting them within the tree under the gallery_UnifiedTimeLine and setting the Text property using the Property dropdown 

	| **Title2**| **ThisItem.Title** |   
	| - | - |
	| **Title2**| **ThisItem.Title** |   
	| **Subtitle2**| **Text(DateTimeValue(ThisItem.ActivityTime, "DateTimeFormat.ShortDate)** Use your own locale.| en| -US"), |
	| |


## Task 6 - Embed KPIs to Profile Page 

In this task you will embed key customer KPIs that we calculated as 'Customer Measures' in Lab 4A. Namely, Total Club Points (Loyalty Scheme Points) and **Customer Lifetime Spend.** 

Contoso Club Loyalty Points 

1. Within the Greeter Power App in Edit mode, open the **CustomerProfile_Screen screen** via the Tree View and select the gallery **gallery_ClubPoints** 
 
2. Set the Items value using the property selector to the below value: 

 
	**Filter(Customer_Measure, CustomerId = gallery_Customers.Selected.CustomerId)** 

 
3. Expand the **gallery_ClubPoints** and select **lbl_Points** inside the gallery. Select the **Text** property from the drop down. Set the formula as follows to display the contacts corresponding TotalClubPoints: 
 

	**ThisItem.TotalClubPoints** 

### Contoso Lifetime Value / Spend 

1. Within the Greeter Power App in Edit mode, open the **CustomerProfile_Screen** screen via the Tree View and select the gallery **gallery_CLTV** 

2. Set the **Items** value using the property selector to: 


	**Filter(Customer_Measure, CustomerId = gallery_Customers.Selected.CustomerId)**

 
3. Expand the **gallery_CLTV gallery** and select **lbl_CLTV** inside the gallery. Select the **Text** property from the drop down and set the formula as follows to display the contacts corresponding LifetimeSpend: 


	**ThisItem.LifetimeSpend** 

From the File menu, click Save and Publish.  

## Task 7 - Test & Explore the Greeter App Experience 

Congratulations! You have now configured a simple greeter app for Contoso Coffee Retail staff. In this task, you will explore the Greeter App experience 

1. In a browser tab, navigate to https://make.powerapps.com. If required sign-in. 

 
2. Click **Apps** in the left-hand menu, and then run your **Contoso Coffee Greeter App** by selecting it and clicking **Play** on the top. 
	![Pictuer25](static/Lab_6_Picture25.png)
 

3. Imagine you are a member of Contoso Coffee Retail staff and you greet them within the store... 

- Look up Abbie Moss' record (LOYID_1000) 

 

- Open Abbie Moss' record: 

	- **Review Activity History** 

	Note that you can identify Abbie's recent purchase history, and that she has made several in-store purchases of brew-at-home coffee. 

    **Review Abbie's Club Balance and Lifetime Value** 

	- Combining her purchase history with insight on her 'Current Points' and 'Lifetime Value', you are able to ascertain that Abbie is both a frequent and high-value customer. 


# Optional - Connect PowerAutomate, PowerApps and CI
## Task 1 - Import the 'Customer Check-In' Activity Solution 

The first task is to create a Custom Activity Type within Dynamics 365 that can be used to store details of 'Customer Check Ins' when customers visit Contoso Coffee stores and cafes. 

We will use a pre-created activity solution. 

1. In a browser window, browser to https://make.powerapps.com 

2. In the top right-hand corner, select the Environment in which you have been working. 
	![Pictuer26](static/Lab_6_Picture26.png)
 
	Note: This will be the environment containing your Dynamics 365 Instance where you previously deployed the Dynamics 365 Customer Insights Card Add-In 

3. Select **Solutions** from the left-hand menu 

4. On the Solutions page, choose **Import** at the top of the page 

5. Click **Choose File** and select the **CheckIn Activity Solution**., which can be found with your CI ILT course Materials. 

	**CheckInActivity_<versionnumber>_managed.zip** 

6. Click **Next**, then **Import** 

	Once published, you will have a solution named **CheckIn Activity.** 

 
## Task 2 - Create the 'Check-In' Flow 

In this task you will create a Flow, which will be triggered in a later Module from a PowerApp by Contoso Retail staff who interact with Contoso Coffee Customers, in order to capture a record of that customer having visited. 

1. In a new Browser tab, navigate to https://flow.microsoft.com 

2. Select the environment you used for Task 1 (Installing the Check-In Solution). 

	To do this, click your name in the top right-hand corner and select the environment from the drop down. 

3. From the left hand menu, select **My Flows**

4. Click **New - Instant cloud flow** 

	![Picture 2099](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image18.jpeg) 

  

5. On the Build an Instant Flow page, choose **PowerApps** and name your Flow **Contoso Coffee Check-In** and click **Create.** 

	![Picture 2153](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image19.jpeg) 

6. Click on **New Step** 

	![Picture 2155](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image20.jpeg) 

7. In the Choose an action step, search for **Microsoft Dataverse** and choose the action **Add a new row** 

8. For Table Name choose **Contoso Check-Ins**, and for Subject use **Check-In @ Contoso Boutique**

	![Picture 2206](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image21.jpeg) 

 

9. Set the **Activity Party Attribute Name 1** to **8** for "regarding"

	You can find the type references here: https://docs.microsoft.com/enus/dynamics365/customerengagement/onpremises/developer/activityparty-entity 

10. Set the **Activity Party Attribute Value 1 to /contacts()** 

11. Place your cursor inside the parens you just typed, then in the pop-up on the Dynamic content tab select **Ask in PowerApps** 

	![Picture 2208](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image22.jpeg) 

12. Click Show advanced options and complete the following attributes as below: 

	| Attribute| Value |
	| - | - |
	| Actual Start| Click **Expression** and use the expression: utcNow() This will populate the 'Actual Start Date' with the current Date+Time at the point of capture. |
	| Contoso Club| Select enter custom value, then **Ask in PowerApps** within Dynamic content tab |
	| Contoso Subscription| **Ask in PowerApps** (you may need to click See more) |
	| Description| **Ask in PowerApps** (you may need to click See more) |
	| Personalised Recommendation| Ask in PowerApps (you may need to click See more) |
	| Start Date| Click **Expression** and use the expression: **utcNow()** This will populate the 'Start Date' with the current Date+Time at the point of capture. |

13. Click Save 

We will connect this flow with a Greeter Power App to enable Contoso Retail staff to capture customer check-ins. 

  

# Task 3 - Creating and testing the 'Recommendations' Flow 

Now we will create a simple Flow that will generate some sample Action Cards for us to consume within the Power App and Dynamics 365, which will represent intelligent insights for personalization such as a product recommendation. 

**Note: At the time of writing Power Apps, Power Automate and Power BI connectors for Customer Insights are in BETA and so have limited connectivity. Going forward, it will be possible to generate Action Cards using Customer Insights Measures, Segments or from an Intelligent Prediction using Machine Learning.** 

In this example, we will simulate the creation of these cards using a simple Flow trigger. 

1. In a new Browser tab, navigate to https://flow.microsoft.com 

2. Select the environment you used for Task 1 (Installing the Check-In Solution). 

	To do this, click your name in the top right-hand corner and select the environment from the drop down. 

3. From the left hand menu, select **My Flows** 

4. Click **New - Instant cloud flow** 

5. On the Build an Instant cloud flow page, choose **Manually Trigger a Flow** and name your Flow **Contoso Coffee Recommendations** then click **Create**. 

6. Click **New step** and search for the Dynamics 365 Sales Insights connector. Then choose the **Create card for Assistant V3 (Preview)** action. 
	![Pictuer27](static/Lab_6_Picture27.png)
 
7. If prompted, sign-in using your tenants admin credentials and grant permissions to the app.  

8. Populate the properties on the step as below (be sure to click Show Advanced) 

	| Property| Value |
	| - | - |
	| **Environment**| <Dynamics 365 Instance used through-out this lab> |
	| **Card Name**| Product Recommendation |
	| **Card Header**| Product Recommendation: Cold Brew Coffee |
	| **Card Text**| Personalised Recommendation for Contoso Coffee Cold Brew (Segmentation) for **Abbie Moss**. Be careful if you copy/paste the text and remove any line breaks. |
	| **Primary Action Type**| Open Url |
	| **Display Entity**| contacts |
	| **Display Record ID**| The GUID for Abbie Moss .The easiest way to get the url is to open your Dynamics application and view the contact Abbie Moss. You can copy the Contact ID from the url |
	| **Primary Action Text**| Make Recommendation |
	| **Primary Action URL**| https://ciilt.crm.dynamics.com/main.aspx?appid=f2dda973-61e5-ea11-a817-000d3a1ab14b&pagetype=entityrecord&etn=contact&id= .The easiest way to get the url is to open your Dynamics application and view the contact **Abbie Moss**. You can remove the Contact ID from the url |


9. **Save** your Flow and then click **Test** to run your Flow. 

 
# Task 4 - Viewing the Recommendation Card Created by the Flow 

 
Because we are using Dynamics 365 Customer Service we can not see the results directly in the contact view within Dynamics. To do this we would need a license for Dynamics 365 Sales. What we can do is open the **Sales Activity Social Dashboard** to see the action card we just created. 

1. Open you Dynamics instance by connecting to https://ciilt.crm.dynamics.com/ replacing the tenant with your tenant name, and logging in with your tenant admin account. 

2. Click on the Dynamics application dropdown in the menu 
	![Pictuer28](static/Lab_6_Picture28.png)

3. Select **Dynamics 365 - Custom** from the list 

	![Picture 2637](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image23.jpeg) 

  

4. This opens the **Sales Activity Social Dashboard** view. In this view you will see the **Relationship Assistant section**, which should now contain a **Product Recommendation** card created by the Power Automate flow we created and tested in the last step. Click on it to see more details. 

	![Pictuer29](static/Lab_6_Picture29.png)

We will also see the recommendations on Power Apps where we will surface the recommendations from the underlying CDS entity where they are stored. 

 

## Task 5 - Connect Customer Check-In Flow 

In this task, you will connect the **Customer Check-In Flow** to your greeter app so that Contoso Coffee Retail staff are able to capture the visit of a customer & details of topics/conversations they have had with customer. 

1. Within the Greeter Power App in Edit mode, open the **CustomerProfile_Screen screen** via the Tree View and select the button **btn_CheckIn** 
![Pictuer30](static/Lab_6_Picture30.png)

With the button **btn_CheckIn** selected, select the **On Select** property in the **Property** drop-down and set the value to **UpdateContext({showCheckIn:true})** 

2. Expand the **CheckInDialog** group 

![Picture 2748](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image24.jpeg) 

3. Select the **btn_CheckInDialog** 

4. Select the **OnSelect** property from the dropdown 

5. Click the **Action** item in the top menu. 

6. On the Action menu, click **Power Automate**. In the Data fly-out that appears, select your **Contoso Coffee CheckIn** Flow that you created in the earlier lab. 
![Pictuer31](static/Lab_6_Picture31.png)
 
7. You should notice that you're prompted to complete the Flow's parameters within the formula bar. When you created the Flow in the Power Automate Lab, we determined that several attribute values would be asked for when the Flow was executed. Here we can pass these values as parameters to fulfill this need. 

- Contoso Club (Boolean), Contoso Subscription (Boolean), Description (Text), Personal Recommendations (Boolean, Regarding (Contacts GUID) 

	Function should read as below: 

	**'ContosoCoffeeCheck-In'.Run( gallery_Customers.Selected.D365_Contacts_contactid, tgl_ContosoClub, tgl_subscription, tgl_recommendations, DetailInput);**

	**UpdateContext({showCheckIn:false});** 

	**Navigate(CustomerProfile_Screen, Fade);** 

 


## Task 6 - Surface Personalised Recommendations 

Dynamics 365 includes the ability to create 'Insight Cards'. These cards highlight to users, timely, actionable insights gathered from Dynamics 365, Office 365 and LinkedIn - Three huge stores of business, interaction and relationship data that center around customers. 

It is now possible to define and generate custom Insight Cards using Power Automate based on insights you obtain from other sources. 

With Customer Insights, allowing you to generate insight through **Measures** and **Segments** as well as extend Customer Insights using **Azure Machine Learning** to make **predictions** such as next steps, churn or propensity to take up an offer - These are all insights that you may wish to drive an action with a customer. 

![Picture 2890](Static/Lab_6_Extend_the_Solution_with_Power_Platform_image25.jpeg)

In this task, we will surface the Insight 

Cards generated during Power Automate Module, within the Greeter App, allowing the Contoso Retail staff to have a more focused, personalized interaction with their customer. 


### Configure the Recommendations Gallery 

1. Create a connection to **Common Data Service** (Dynamics 365). To do this, click **View** in the top menu bar and then Data Sources. 

2. In the **Data** menu that appear to the right of your canvas, select Add data source 

3. Click **New connection,** then search for the Common Data Service connector. Select the connector and click Connect. 

4. In the **Choose an entity** page, select **Action Cards** then click Connect 


### Set the Recommendations Gallery to display Insight Cards associated to the current contact 

1. Within the Greeter Power App in Edit mode, open the **CustomerProfile_Screen** screen via the Tree View and select the gallery **gallery_Recommendations** 

2. Select the **Items** property from the property drop-down, then set the formula to return only Insight Cards relating to the current Customer Profile as below: 

	**Filter('Action Cards', regardingobjectid = gallery_Customers.Selected.D365_Contacts_contactid && 'CardType ENUM' <> 32)** 

3. In the tree view, expand the **gallery_Recommendations** and select **Title1.** Set its Text value to Th**isItem.Title.** 

 

4. In the tree view, expand the **gallery_Recommendations** and select **Subtitle1.** Set its Text value to **ThisItem.'Card Description'.** 

5. **Save** and **Publish** your App. 

	You should now see that the 'Recommendations Gallery' contains some example Recommendations using the Insight Cards you generated in previous module, using Power Automate. 
	![Pictuer32](static/Lab_6_Picture32.png)
 

## Task 7 - Test & Explore the Greeter App Experience  

Congratulations! You have now configured a simple greeter app for Contoso Coffee Retail staff. In this task, you will explore the Greeter App experience 

1. In a browser tab, navigate to https://powerapps.microsoft.com. If required sign-in. Click Apps in the left-hand menu, and then run your Contoso Coffee Greeter App 
![Pictuer33](static/Lab_6_Picture33.png)
  

2. Imagine you are a member of Contoso Coffee Retail staff and you greet customers within the store... 

3. Look up Abbie Moss' record (LOYID_1000) 

4. Open Abbie Moss' record: 

	- Review Activity History 

	- Note that you can identify Abbie's recent purchase history, and that she has made several in-store purchases of brew-at-home coffee. 

	- Review Abbie's Club Balance and Lifetime Value 

	- Combining her purchase history with insight on her 'Current Points' and 'Lifetime Value', you are able to ascertain that Abbie is both a frequent and high-value customer.   

	- Review recommendations made for Abbie 

	- Looking at her personalized recommendations, you see that there is a recommendation for Abbie to take-up the 'Cold Brew Coffee' offer. This is Contoso Coffee's new Cold Brew coffee, which you can recommend to Abbie. 

5. Finally, you click the 'Customer Check-In' button 

6. This allows you to capture Abbie's visit to the store as well as details of the recommendations you discussed with Abbie and captures this detail against her record in Dynamics 365 as an activity. 

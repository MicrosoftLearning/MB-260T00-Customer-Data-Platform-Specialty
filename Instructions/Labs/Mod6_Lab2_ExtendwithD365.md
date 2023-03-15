---
lab:
    title: 'Lab 6.2: Extend with the Dynamics 365 apps'
    module: 'Module 6: Manage external connections with Dynamics 365 Customer Insights'
---

# Lab 6.2: Extend with the Dynamics 365 apps
# Module 6: Manage external connections with Dynamics 365 Customer Insights

Having successfully ingested Contoso Coffee's data sources and created a Unified Customer Profile and calculated key measures, you are now able to leverage the insight you have generated to empower different personas within Contoso Cofee.

## Empower Customer Service Advisers/Marketing team

As Project Manager for Contoso Retail, you need to empower Contoso Coffee Customer Service/Marketing Advisors to deliver the best possible experience to customers, in order to achieve the best possible customer satisfaction (CSAT) scores.

In this Module you will deliver insights to Contoso's existing Customer Service/Marketing application including: Unified Profile, KPIs and Active Segments from Customer Insights.

To do this you will configure the Customer Insights Customer Card Add-In to embed unified and enriched customer data from Customer Insights on the Contact form within Dynamics 365 for Customer Service/Marketing.

## Objectives

- Configure Customer Insights Customer Card Add-In

- Configure Customer Insights card controls in Dynamics 365 Customer Service/Marketing

- Exporting segments and orchestrating customer journey with exported segments in Dynamics 365 Marketing

# Exercise 1 - Ingest the Dynamics Contacts

The Customer Insights Cards embedded within Dynamics 365 utilize the Contact ID from Dynamics to identify which profile data to display. In this task you will consume Contact data from Dynamics 365 into Dynamics 365 Customer Insights and unify it with the existing dataset from earlier modules. 

**Note:** This step is not one you would normally have to take if you were using Dynamics 365 as a data source to begin with. Since we did not start with contacts from Dynamics we will artificially have to ensure that we have similar contacts in Dynamics for the lab to work. 


## Task 1 - Import Contacts into Dynamics 365

First, we will setup some sample Contacts within Dynamics 365 for you to ingest and match against your existing profiles in Customer Insights. 

1.  In a browser, navigate to `https://aka.ms/ppac` and select **Environments**. Open the **Marketing Trial** environment. 

2.  Select the **⚙️ Settings** icon in the top right-hand corner, then select **Advanced Settings**. 

3.  Select the chevron next to **Settings** in the menu bar. Then select **Data Management** under the **System** heading.

4.  On the Data Management page, select **Imports**.

5.  In the menu bar, select **Import Data** to launch the data import wizard.

6.  Select **Choose File** and choose the **ContosoCoffee_D365Contacts** Excel spreadsheet from the Lab Resources folder, then select **Next** until you get to the **Map Record Types** screen. 

7.  Select **Contact** from the **Record Types** drop-down and select **Next**.

8.  On the **Map Fields** screen, select **Ignore** for **Full Name** then select **Next**, then **Next**, then **Submit** and **Finish**. 

9.  Monitor the progress of your import using the **Refresh** button on the top right of the grid. 

10. Wait for the import to complete successfully. 

11. Re-open the **Marketing** app and navigate to the **Outbound Marketing** area.

    > **Note:** To change area, use the drop-down menu found in the bottom left-hand corner. 

12. From the left navigation menu, select **Contacts** from the **Customers** section. 

13. You should now have a record for **Abbie Moss**. 


## Task 2 - Ingest the contacts into Customer Insights

Now we will ingest the Dynamics 365 contacts as an additional data source within Customer Insights. 

1.  In a new tab, navigate to `https://home.ci.ai.dynamics.com`.

2.  Select **Data** > **Data sources** from the left navigation menu. 

3.  Select **+ Add data source** from the command bar. 

4.  Choose **Microsoft Dataverse** and name the Data Source `D365`. 

5.  For **Server address**, you will need the **Environment URL**. 

    To get this, navigate to `https://aka.ms/ppac` and select **Environments**. Select the **Marketing Trial** environment. Right-click and copy the **Environment URL**. 
    
6.  Select **Next**. 

7.  In the list of entities, choose **Contact**. Then select **Save**. It may take a few minutes to complete the upload. 

    This is not a **Power Query** connector, so there is no option to transform the data. Specific fields cannot be selected, everything will be ingested. Fields can be selected during the **Unify** phase to ensure the unified profile doesn't get bloated with too many additional columns. 


## Task 3 - Unification

### Select source fields

1.  Expand **Data** and select **Unify** from the left navigation menu and select **Edit** on the **Source fields** tile. 

2.  Select the **Select entities and fields** button. Collapse **Customers (Loyalty)** and **Contacts (eCommerce)**.

3.  Expand the **contact (D365)** entry. Search for and select the following fields: 

	- address1_city

	- address1_country

	- address1_county

	- address1_line1

	- address1_line2

	- address1_postalcode

	- address1_stateorprovince

	- contactid

	- emailaddress1

	- firstname

	- fullname

	- gendercode

	- lastname

4.  Select **Apply**. Select **Add**. 

5.  Select **D365 contact** from the **Entities** list. Customer Insights has automatically mapped some of the attributes. 

5.  Select **contactid** as the Primary Key. 

6.  Select **Next**. 


### Create matching rule

1.  Select **Next** to skip to the **Matching conditions** step. 

2.  You will see a warning that **contact : D365** requires a new rule to match records. Select **+ Add rule** and set it up as follows: 

    - Entity: **Contacts : eCommerce**, Field: **EMail**

    - Entity: **contact : D365**, Field: **emailaddress1**

    - Leave **Normalize** blank.

    - Set the **Match precision** to: **Medium**

    - Name: `Email Match` 

3.  Select **Done**. 

4.  Click **Save and close**. 

5.  Select **Unify** from the toolbar and select **Unify customer profiles and dependencies**. 

6.  Wait for the **Unify** process to complete. 


# Exercise 2 - Embed Customer Insights into Dynamics 365

So far, we have ingested data from Dynamics 365 into Customer Insights. The customer records in Customer Insights and the contacts in Dynamics 365 are linked using the contact id as Primary Key. 

## Task 1 - Install the Customer Insights Customer Card Add-in

The first step is to install the Customer Insights Customer Card Add-In. This add-in will enable you to embed Unified Profiles and Insights from Customer Insights directly within an existing Dynamics 365 experience for Contoso Coffee Customer Service Advisors. 

1.  Navigate to `https://make.powerapps.com` and select your Dynamics 365 Marketing instance from the **Environment** drop-down. 

2.  Select **Solutions** from the left navigation menu. 

3.  Select **Open AppSource** from the command bar. Remove the Power Platform filter from the search. 

4.  Search for `Customer Insights` in AppSource. Select **Customer Insights Customer Card Add-in** from the results. Select **Get it now**. (You may be prompted to sign-in.)

5.  Select **Get it now** again.

6.  You will be re-directed to the Power Platform admin center to complete the package install. Select the **Marketing Trial** environment from the drop-down. Then check the two privacy related boxes and select **Install**. 

7.  This will begin the installation process. You can check the status of the install on the page that opens. Select **Refresh** to update the page. 

    > **Note:** If it shows as **Update available** in the **Status** column, select **Update available** then check the box and select the **Update** button. 

8.  Once installation is complete, you can close this browser tab and navigate to the **Solutions** area on `https://make.powerapps.com`, where you should see the **Dynamics 365 Customer Insights Customer Card Add-In** installed. 

9.  Select **Switch to Classic** from the command bar. 

10. Double-click the **CustomerInsightsCustomerCard** Solution. You should see the **Configuration** page. If not, select **Configuration** from the left menu. 

11. Select **Login with your org credentials** and sign-in with your account used for **Customer Insights**. 

    > **Note:** You may need to "allow pop-ups" in the browser.

12. Once connected, select the **YourName CI ILT Lab** Customer Insights instance from the drop-down. 

13. From the drop-down for **Dynamics contact id**, select the attribute from your customer profile that represents the Dynamics 365 Contact Id: **System.Customer.D365.contact.contactid**.

    > **Note**: Step 4 refers to the **Dynamics 365 account id field** field which we are not using. Leave this as **Please select**. This will be used in the future for B2B scenarios.

14. Select **Save Configuration**.


## Task 2 - Add Security Roles

For users to configure the Customer Insights content embedded in the Dynamics 365 model-driven forms, you will need to assign the appropriate Security Role. 

1.  Navigate to `https://aka.ms/ppac` and select **Environments** from the left navigation menu. 

2.  Select the **Marketing Trial** environment and go to **Settings**. 

3.  Expand **Users + permissions** and select **Users**. 

4.  Select your user account (unless you've made changes, it will be **MOD Administrator**), and select **Manage security roles**. 

5.  Select the **Customer Insights Card Customizer** role and select **Save**. 


## Task 3 - Add the Customer Insights Customer Card Controls to the Contact Form

We will now configure the Dynamics 365 Model-drive Contact Main form, used by Contoso Coffee Customer Service Advisors (CSAs) to display the embedded Cards and data from Customer Insights.

1.  Navigate to `https://make.powerapps.com` and select **Marketing Trial** from the Environment drop-down. 

2.  Select **Apps** on the left navigation menu. 

3.  Select the **... More Commands** menu on the **Marketing** app and select **Edit**. 

4.  Scroll down the **Pages** pane in the PowerApps App Designer and expand **Contact**, select **Contact forms**. 

5.  In the **Contact forms** pane, select the ✏️ **Edit** button on the **Contact Main Form**. 

6.  In the PowerApps Form Editor, from the command bar; select **Save As** from the drop-down. 

7.  Save a copy of this form, setting the **Name** and **Description** to `Contact with Customer Insights`. Select **Save**. 

8.  Add three new sections by selecting the **Components** from the left menu, and dragging three **1-column section** components on to the form. Name them - `CUSTOMER INSIGHTS TIMELINE`, `KPI` and `CUSTOMER DETAILS` in the **Properties** pane. 

9.  Add a table column to each new section, any table column will do, in this example we've added the **Address 1: City** table column to all three sections. Uncheck **Show only unused table columns** to see the used ones. Once you've added them be sure to check the **Hide Label** setting in the **Properties** pane. 

10. Move the **CUSTOMER INSIGHTS TIMELINE**, **KPI** and **CUSTOMER DETAILS** section to the middle column of the form. Remove the pre-existing **Timeline** section. 

11. Select **Save** in the top right hand corner and select **Publish**. 

12. To finish the configuration of the form, the Classic experience is required. Select **Save** in the top right, then select **Switch to classic** from the ... menu. 

13. Double-click the **Address 1: City** table column in the **CUSTOMER INSIGHTS TIMELINE** section and select the **Controls** tab. 

14. Select **Add Control...** Scroll down the list and choose **Customer Insights Timeline Control** and select **Add**. 

15. Set the control to appear on **Web**, **Phone** and **Tablet** and check **Hide Default Control**. Select **OK**. 

16. Repeat these steps for the **KPI** and **CUSTOMER DETAILS** sections; adding the **Customer Insights Measures Control** to the KPI section and the **Customer Insights Customer Details Control** to the Customer Details section. 

17. Select **Save** and select **Publish**. Close the tab. 

18. Back on the model-driven **App Designer**, select the **Contact with Customer Insights** form and select **Add**. 

    > **Note:** You may need to refresh the page and select **Contact forms** again before it shows. 

19. Remove the **Contact Main Form**. Select **Publish**. 


## Task 4 - Test the changes in the Model-driven App 

1.  In a new tab, navigate to `https://make.powerapps.com` and select **Apps** from the left navigation menu. 

1.  Open the **Marketing** app. 

1.  Select **Contacts** from the left navigation menu, in the **Outbound Marketing** area. 

1.  Open the Contact record for **Abbie Moss**. 

1.  You should now see that the three **Customer Insights Cards** embedded in the form. **KPI** and **Customer Details** controls can be configured further. Edit the cards as follows: 

    - **CUSTOMER INSIGHTS TIMELINE:** No configuration required. This should display a unified set of ingested activities from Customer Insights, you can filter the list by **Activity Type**. 

    - **KPI:** Select ✏️ **Edit** on the KPI controls. Search for and add **Total Club Points**, **Lifetime Spend**, and **Average Store Purchase**. Remove **Average activity duration**. Select **Save**. 

    - **CUSTOMER DETAILS:** The customer detail control should display some key information from the Unfiied Customer Profile. Optional: You can change the fields if you wish. 

Congratulations! You have successfully completed the objectives of this module, providing Contoso Coffee Customer Service Advisors with visibility of all customer touchpoints & KPIs. 


# Exercise 3 - Extending the Value of Customer Insights with Dynamics 365 Marketing

One of the integrations Customer Insights has is with Dynamics 365 Marketing. With Dynamics 365 Marketing you can setup customer journeys based on lists of customers. There are three steps to the process. 

- Configure an Export Destination in Customer Insights 

- Export the segments to Dynamics 365 Marketing 

- Create a Customer Journey in Marketing from the Segment(s) 

## Task 1 - Configure an Export Destination

1.  Navigate to `https://home.ci.ai.dynamics.com`, sign in with your administrator account if needed. 

1.  Select **Data > Exports** from the left navigation menu. Select **+ Add export**

1.  On the **Set up export** pane, select **+ Add a connection** and select **Dynamics 365 Marketing (Outbound)** from the list. 

1.  Enter `Dynamics 365 Marketing` for **Display name** and enter the Marketing Trial environment URL for **Server address** and select **Sign in**. 

1.  Select the **I agree** box and select **Save**. 

1.  Enter `Dynamics 365 Marketing` for **Display name** 

1.  Note the field to indicate which Customer Insights field matches your Dynamics Contact ID, this is important as it provides the link between the Customer Insights customer and the Dynamics Contact. Select **CustomerId**. 

1.  Select the **SummerPromotion** segment.

1.  On the **Save** drop-down, select **Save and run**.

    > **Note:** The export should complete with warnings. Only customer profiles that are mapped to a contact record in Dynamics 365 Marketing will be part of the Segment in Dynamics. 


## Task 2 - Adding a Segment to an Existing Export Destination

If you have already configured an export destination and then create new segments there is an easy way to add those new segments to your existing export. In this task we'll go in and add the **High Value Online Customers** segment to the export we just created.

1.  Select **Segments** from the left navigation menu. 

1.  Select the **Show more** vertical ellipse next to the **High Value Online Customers** segment. Then select **Manage exports**. Select the **Dynamics 365 Marketing** export and select **+ Add segment** (or select the + icon). Select **Run**. 

    The segments are now ready to be consumed in Dynamics 365 Marketing. 


## Task 3 - Using the Segment to Orchestrate a Customer Journey

We are now ready to consume the segments which Customer Insights has exported to our Dynamics 365 Marketing instance. For this example, we are going to create a **New** journey based on the **High Value Online Customers** segment. The Customer Journey will send out a Monthly Newsletter to the High Value Online Customers. 

### Review the Segments

1.  Navigate to `https://make.powerapps.com` and select **Apps** from the left navigation menu. 

1.  Open the **Marketing** app. Change the **area** to **Outbound Marketing**. 

1.  Select **Segments** in the left navigation menu, under the **Customers** section. 

1.  Open the **HighValueOnlineCustomers** segment. 

1.  To use a segment in a Customer Journey you must first mark it as 'Live'. Select **Go live** from the command bar. 

1.  Wait for the **Status reason** to change to **Live**. 


### Create the Newsletter Email

1.  Select **Marketing emails** in the left navigation menu, under the **Marketing execution** section. 

1.  Select **+ New** from the command bar. 

1.  From the **Marketing email templates** select the **1 column** template. 

1.  You are welcome to customize anything in the newsletter you'd like, but for this lab we really don't need to customize anything. 

1.  Select **Add a subject** and enter `Monthly Customer Newsletter`. 

1.  Double-click on the title text next to **Draft** and enter `High Value Monthly Newsletter`. 

1.  Select **Save**. 

1.  Select **Go live**. Wait for the **Status reason** to change to **Live**. 


### Create the Customer Journey

1.  Select **Customer journeys** from the left navigation menu. 

2.  Select **+ New** from the command bar. 

3.  Select the **Monthly Newsletter** template. 

4.  To rename the Journey, select the **More Header Editable Fields** drop-down menu in the Header. Enter `High Value Customers (Monthly Newsletter)` for **Name**. 

5.  Select the **Set audience** link in the first tile on the Journey canvas. 

6.  In the **Audience** pane, enter `High` in the **Look for Segment** box and select the **HighValueOnlineCustomers** segment from the list. 

7.  Select **Save** from the command bar. 

8.  Select **Choose an email** from the tile before **End**.

9.  In the **Send an email** pane, enter `High` and select the **High Value Monthly Newsletter** email. 

10. Select the **General** tab and set the **End date and time** a year from today. 

11. Select **Save** and select **Go live** from the command bar. 

You are done! You have just created a Customer Journey in Dynamics 365 Marketing based on a Segment of customers which you brought in from Dynamics 365 Customer Insights.


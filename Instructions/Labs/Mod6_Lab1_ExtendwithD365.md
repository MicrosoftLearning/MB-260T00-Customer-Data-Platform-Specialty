---
lab:
    title: 'Lab 6.1: Extend with the Dynamics 365 apps'
    module: 'Module 6: Manage external connections with Dynamics 365 Customer Data Platform'
---

# Lab 6.1: Extend with the Dynamics 365 apps
# Module 6: Manage external connections with Dynamics 365 Customer Data Platform

Having successfully ingested Contoso Coffee's data sources and created a Unified Customer Profile and calculated key measures, you are now able to leverage the insight you have generated to empower different personas within Contoso Cofee.

## Empower Customer Service Advisers/Marketing team

As Project Manager for Contoso Retail, you need to empower Contoso Coffee Customer Service/Marketing Advisors to deliver the best possible experience to customers, in order to achieve the best possible customer satisfaction (CSAT) scores.

In this Module you will deliver insights to Contoso's existing Customer Service/Marketing application including: Unified Profile, KPIs and Active Segments from Customer Insights.

To do this you will configure the Customer Insights Customer Card Add-In to embed unified and enriched customer data from Customer Insights on the Contact form within Dynamics 365 for Customer Service/Marketing.

## Objectives

- Configure Customer Insights Customer Card Add-In

- Configure Customer Insights card controls in Dynamics 365 Customer Service/Marketing

- Exporting segments and orchestrating customer journey with exported segments in Dynamics 365 Marketing

## Prerequisites

To complete the Customer Insights in a Day course you will need the following:

- **Dynamics 365 Marketing Instance** or Trial

- Access to **Power Apps** or a Power Apps Trial

- Access to **Power Automate** or a Power Automate Trial

- Access to **Power BI** or a Power BI Trial

- **Microsoft Azure** Trial

- **Customer Insights** Trial

If you do not have access to the above, you can follow Lab 3 to get setup.

## Approximate Time:  60 mins



# Exercise 1 - Ingest the Dynamics Contacts


The Customer Insights Cards embedded within Dynamics 365 utilize the Contact ID from Dynamics to identify which profile data to display. In this task you will consume Customer data from Dynamics 365 into Dynamics 365 Customer Insights and Map, Match and Merge it with the existing data-set from Lab 1.

**Note:** This step is not one you would normally have to take if you were using Dynamics 365 as a data source to begin with. Since we did not start with contacts from Dynamics we will artifically have to ensure that we have similar contacts in Dynamics for the lab to work.

## Task 1 - Import Contacts into Dynamics 365

First, we will setup some sample Contacts within Dynamics 365 for you to ingest and match against your existing profiles in Customer Insights. You will need these contacts for later modules.

1. In a browser, login to your Dynamics 365 instance and open the **Marketing** app

2. Click the **Settings Cog** ![Picture 292](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image1.jpeg) in the top right-hand corner, then **Advanced Settings**

3. On the page that loads, click the chevron next to **Settings** in the menu bar. Then select **Data Management** under the **System** heading

	![Picture 292](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image1-2.png)

4. On the *Data Management* page, click **Imports**

	![Picture 298](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image2.jpeg)

5. In the menu bar, select **Import Data** to launch the data import wizard.

6. Under **Choose File** select the **ContosoCoffee_D365Contacts**. (from the course content), then click **Next** until you get to the **Map Record Types** screen

7. Select **Contact** from the **Record Types** dropdown and click **Next**

	![Picture 391](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image3.jpeg)

8. On the **Map Fields** page, select **Ignore** for **Full Name** then click **Next**, then **Next** then **Submit** and **Finish** (You could also map **Full Name** to **Address1:Name**)

	![Picture 391](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image3-2.png)

9. You can monitor the progress of your import, using the refresh button on the top right of the grid. - Ensure that your import completes successfully

	![Picture 391](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image3-3.png)

10. Reopen the **Marketing** app and navigate to **Contacts**

11. You should now have a record for **Abbie Moss**

## Task 2 - Ingest the contacts into Customer Insights

Now we will ingest the Dynamics 365 contacts as an additional data source within Customer Insights. Switch back to your Customer Insights tab or re-open https://home.ci.ai.dynamics.com

1. Click **Data** > **Data Sources** in the left hand menu

2. Click **Add Data Source** on the top left of the page

3. Choose **Connect to a Common Data Service** and name the Data Source **D365**, Click **Next**

4. On the **Enter Common Data Service details** screen, We will need to put in the URL to our Dynamics Dataverse (CDS) instance. To get this go back to your Dynamics Marketing site in a new tab (or if you have it open switch back to it). Copy the beginning of the URL. You will have something like this: https://ORGNAME.crm.dynamics.com

	Enter that URL into the **Server address** box and click **Sign In**. Sign In with the credentials that you use to access Dynamics 365. You may get a consent prompt like below, if you do this will require that you are the Dynamics 365 admin or tenant admin and if you are not then you will be prompted to log in with those credentials, and check the box to give consent for CI to access the Dynamics environment (but only as the user setting up the connection, and with their permissions).

	![Picture 461](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image4.jpeg)

5. Click **Next**

6. In the list of entities find and select **Contact**. Then click **Save**

	Because this is not a Power Query connector we do not get the option to transform the data. We also cannot choose the fields we want, and will get them all. We can controil which fields are added to our unified profile during the Map/Match/Merge phase to ensure we don't bloat our unified profile.

## Task 3 - Go through Unification

### Map

1. Click **Unify** &#8594; **Map**

2. Under **Entities** click **Edit fields**

	![Picture 577](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image5.jpeg)

3. Epxand the **Contact (D365)** entry. We only want specific fields pulled through, so let's only check the following fields (search is your friend here as the Dynamics entity has a LOT of fields):

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

4. Click **Apply**. Click on the **D365 : contact** tile in the entities list. As when you ingested Loyalty and eCommerce data, you should see that Customer Insights has intelligently mapped the attributes to the Common Data Model types

5. Confirm that **contactid** was set as the Primary Key, or set it

	![Picture 577](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image5-2.png)

6. Click **Save** on the top left

### Match

1. Click the **Match** tab

2. Click **Edit** in the top right of the **Match Order** table

3. Click **Add Entity** and select **Contacts : D365** and check **Include All Records** and then click **Done**

	![Picture 672](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image6.jpeg)

4. You will see that this new addition requires a new rule. Click **Create New Rule** and set it up as follows:

	![Picture 674](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image7.jpeg)

	- Entity: **Contacts : eCommerce**

	- Field: **Email**

	- Entity: **Contact : D365**

	- Field: **emailaddress1**

	- Leave the Normalize blank

	- Set the Match precision to **Medium**

	- Rule Name: **Email Match**

5. Click **Done**

6. Click **Save** and then **Run**

### Merge

1. Click on the **Merge** tab

2. You should see that Contactid from Dynamics 365 has been added to the list of Keys (Keys tab) that will make up the Unified Profile

3. You can **optionally** add any attributes which have all been excluded and identify them as 'Merge' attributes where an attribute already exists (e.g. First Name, Last Name, Full Name, Gender and gerndercode_display)

4. Click **Save** and then **Run** > **Run merge and downstream processses** (or just Run if you made no changes)



# Exercise 2 - Embed Customer Insights into Dynamics 365

We have already ingested data from Dynamics 365 into Customer Insights. The customer records in Customer Insights and the contacts in Dynamics 365 are linked with the help of contact id with in Dynamics 365.

## Task 1 - Install the Customer Insights Customer Card Add-in

The first step is to install the Customer Insights Customer Card Add-In, that will enable you to embed Unified Profile and Insight from Customer Insight, directly within an existing Dynamics 365 experience for Contoso Coffee Customer Service Advisors.

1. Navigate to https://make.powerapps.com and select your Dynamics 365 for Customer Service instance from the **Environment** drop down

	![Picture 674](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image7-2.png)

2. Once selected, click **Solutions** on the left-hand menu

3. Click **Open AppSource** from the top of the page

	![Picture 674](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image7-3.png)

4. On the AppSource window that opens, search **Customer Insights**. You should see **Customer Insights Customer Card Add-in** in the results, click on it. Then click **Get it now**

	![Picture 674](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image7-4.png)

5. Complete your details on the **One more thing...** page. Including **Name**, **email**, and **Phone Number**. Then provide your consent and click **Continue**

6. You will be taken back to the Power Apps console where you will configure the add-in. First, select your environment from the dropdown. Then check the two boxes and click the **Install** button

	![Picture 674](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image7-5.png)

7. This will begin the installation process. You can check the status of the install on the page that opens. (You may need to refresh it for updates). If you see **Update available** in the status column click that text, then check the box and click the **Update** button

	![Picture 961](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image8.jpeg)

8. Once installation is complete, you can close this browser tab and return to the **solutions** area on https://make.powerapps.com, where you should see the **Dynamics 365 Customer Insights Customer Card Add-In** installed

	![Picture 961](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image8-2.png)

9. Click **Switch to Classic** at the top of the page

10. Double click the **CustomerInsightsCustomerCard** solution. You should see the **Configuration** Page. If not, click **Configuration** from the left menu

	![Picture 961](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image8-3.png)

11. Click **Login with your org credentials** and sign-in with your account used for **Customer Insights**. Note: If you don't see the login dialog you may need to "allow Pop-ups" in your browser

	![Picture 961](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image8-4.png)

12. Once connected, select your Customer Insights Instance in the drop down

13. From the drop-down for **contact id** select the attribute from your customer profile that represents the Dynamics 365 Contact Id. (**System.Customer.D365.Contacts.contactid**)

	![Picture 961](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image8-5.png)

	**Note**: There is now a field for **Dynamics 365 account id field** which we are not using, you may leave this as "please select". This will be used in the future for B2B scenarios.

14. Click **Save Configuration**

## Task 2 - Add Security Roles

For users to configure the Customer Insights content embedded within the Dynamics 365 form, you will need to assign them the appropriate Security Role.

Next you will need to assign the **Customer Insights Customizer** role: Assign this role to the users who will customize the content to be shown on the card for the whole organization.

1. Open the **Marketing app** in Dynamics 365 instance. Click the Cog ![Picture 1081](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image9.jpeg) in the top righthand corner then **Advanced Settings**. This should open Dynamics 365 classic Web App in a new tab

2. Click the arrow next to settings and choose '**Security**'

	![Picture 1081](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image9-2.png)

3. Click **Users**

4. Select your user account (and any others that you wish to be able to view or edit Customer Insights Cards). Click **Manage Roles**

	![Picture 1081](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image9-3.png)

5. Add the **Customer Insights Card Customiser** role as shown below. And click **OK**

	![Picture 1081](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image9-4.png)



## Task 3 - Add the Customer Insights Customer Card Controls to the Contact Form

We will now configure a Dynamics 365 Contact form, used by Contoso Coffee CSA's to display the embedded Cards and from Customer Insights.

1. Navigate to https://make.powerapps.com/ and select your Dynamics 365 for Customer Service instance from the Environment drop down

2. Click **Apps** on the left menu. You will be shown a list of apps installed into your Dynamics / CDS instance

For the next steps we suggest you edit the **Marketing** app, but you can alternatively use the **Sales Hub** or a custom **Model Driven App** if you do not have this available. It will be important to know which you edit as that is where you'll need to look for the new form later.

3. Click the **More Commands '...'** button for the **Marketing** app and click **Edit**

	![Picture 1081](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image9-5.png)

4. You should now see the PowerApps App Designer has opened.

	Scroll down and expand the **Forms** menu for the **Contact** entity.

	![Picture 1175](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image10.jpeg)

5. Ensure that the default Contact form (**Contact** or **Contact for Interactice Experience**) is selected on the right and click the edit button (pencil) to edit the form. The button will appear when you hover over the form in the components list

	![Picture 1219](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image11.jpeg)

6. You should now be presented with the new PowerApps Form editor, on the top right select **Save As** from the dropdown

	![Picture 1221](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image12.jpeg)

7. Save a copy of this form, setting the name to **Contact with Customer Insights**. Then click **Save**

	![Picture 1221](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image12-2.png)

8. Add three new sections by clicking **Components** menu option on the left, and dragging three **1-One Column Section** components on to the form. Name them - **CUSTOMER INSIGHTS TIMELINE**, **KPI** and **DEMOGRAPHICS** in the right hand properties pane

	![Picture 1221](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image12-3.png)

9. Add a field to each new section, any field will do, in this example we've added the **Address 1: City** field to all three sections. Uncheck the 'Show only unused fields' to see the used ones. Once you've added them be sure to check the **Hide Label** setting

	![Picture 1279](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image13.jpeg)

10. Now let's save our form and finish it in the 'classic' experience. Click **Save** in the top right, then click **Switch to Classic**

	![Picture 1281](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image14.jpeg)

11. Double Click the field you added in the **CUSTOMER INSIGHTS TIMELINE** section and click on the **Controls** tab

	![Picture 1318](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image15.jpeg)

12. Click **Add Control...** Scroll down the list and choose **Customer Insights Timeline Control** then click **Add**

	![Picture 1318](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image15-2.png)

13. Set the control to appear on **Web**, **Phone** and **Tablet** and check the **Hide Default Control** checkbox

	![Picture 1318](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image15-3.png)

14. Repeat steps **11** and **12** for the fields added into the **KPI** and **DEMOGRAPHICS** section, adding the **Customer Insights Measure Control** to KPI section and the **Customer Insights Demographic Control** to the Demographics section

15. Move the **KPI** section to the top of **Related** section and **DEMOGRAPHICS** under **KPI** section. Now remove **Related** and pre existing **Timeline** sections as below

	![Picture 1318](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image15-4.png)

16. Click **Save and Close**

17. Back on the **App Designer**, select to add your new **Customer Insights** form to the **Marketing** app. Note that you may need to reload the page and select the contact forms before it shows up

	![Picture 1435](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image16.jpeg)

18. Click **Save** in the top right hand corner and then **Publish**

## Task 4 - Confirm the Changes in the Model Driven App 

1. Now open your **Dynamics 365 Marketing** instance

2. Navigate to the **Contacts** via the left hand menu. Open the Contact record for **Abbie Moss** and select your new **Customer Insights** form using the form selector

	![Picture 1487](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image17.jpeg)

3. You should now see that the three Customer Insights you embedded in the form render. KPI and Demographics control's can be configured. You may need to edit the cards to select the correct fields to show

	**Timeline:**

	No configuration required. This should display a unified set of ingested activities from Customer Insights.

	![Picture 1487](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image17-2.png)

	**Demographic**

	The demographic control should display some key information from the Unfiied Customer Profile. Click the **Edit** button to customize the information that appears.

	![Picture 1487](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image17-3.png)

	Turn on the **Segments**. Add any additional fields that you believe may be helpful to a Customer Service Advisor.

	**KPIs**

	Click **Edit** on the KPI controls. Here you are able to select from any of the Customer Measures that you created earlier. Add your Customer Measures to give the Contoso Coffee CSA visibility. (**Total Club Points, Lifetime Spend(&#036;)** and **Average Store Purchase(&#036;)** )

	![Picture 1487](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image17-4.png)

	![Picture 1487](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image17-5.png)

	Your final Contact form should appear similar to that above.

Congratulations! You have successfully completed the objectives of this module, providing Contoso Coffee Customer Service Advisors with visibility of all customer touchpoints & KPIs.



# Exercise 3 - Extending the Value of Customer Insights with Dynamics 365 Marketing

One of the integrations Customer Insights has is with Dynamics 365 Marketing. With Dynamic 365 Marketing you can setup customer journeys based on lists of customers. There are three steps to the process.

- Configure an Export Destination in Customer Insights

- Export the segments to Dynamics 365 Marketing

- Create a Customer Journey in Marketing from the Segment(s)

## Task 1- Configure an Export Destination

1. Navigate to https://home.ci.ai.dynamics.com

2. Log in with your administrator account

3. Click on **Admin** > **Export Destinations** in the left-hand menu. You can find various destinations that are available in Customer Insights. Click **Set up** on **Dynamics 365 Marketing**

	![Picture 1487](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image17-6.png)

4. You will be presented with a dialog to configure your export destination to **Dynamics365 Marketing**. Enter the display name and your Marketing instance address and sign in with your account

	Note the field to indicate which Customer Insights field matches your Dynamics Contact ID, this is important as it provides the link between the customer Insights customer and the Dynamics Contact. In our case this is the field I've chosen, yours should be similar). Your finished dialog will look something like this:

	![Picture 1487](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image17-7.png)

	It is also important to note that you will either need to authenticate with the Global Tenant Admin account, or they will need to be present to consent to the access of the system using the service admin account you log in with.

5. Click **Next**

6. You can now choose which Segments you want to export. We will add one Segment here and in the next Task we'll see how to add new segments to an existing export. Click the **Summer Promo** segment and click **Save**

	![Picture 1487](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image17-8.png)

**NOTE:** If you get an error when saving follow these steps and then try to create the export again

1. Go to portal.azure.com - you need to login as tenant admin

2. Search for **Enterprise Applications**

3. Click on **All Applications** in the left menu

4. Search for **Customer Insights Dynamics 365 For Sales Export**

5. Click on **Permissions** on the left menu

6. Click on the **Grant admin consent for Microsoft**

Finally, let's export the segment to Dynamics Marketing. Click the **Export** button by clicking the three dots beside the destination to individually export to your destinations or you can click on **Export all** in the top menu to initiate export to all the destinations that are configured.



## Task 2 - Adding a Segment to an Existing Export Destination

If you have already configured an export destination and then create new segments there is an easy way to add those new segments to your existing export. In this task we'll go in and add the **High Value Online Customers** segment to the export we just created.

1. Click **Segments** in the left-hand menu

2. Click the vertical ellipse next to the **HighValueOnlineCustomer** segment. Then click **Add to** > **My Marketing Instance** (or whatever you named your export destination)

![Picture 1886](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image18.jpeg)

3. Click on **System** > **Export Destinations** > **My Export Destinations** in the left-hand menu

4. Click **Export all** in the top menu bar

	This concludes the lab. You are now ready to consume the segments in Dynamics 365 Marketing which is incorporated as an additional section which you can do later.

## Task 3 - Using the Segment to Orchestrate a Customer Journey

We are now ready to consume the segments which Customer Insights has exported to our Dynamics 365 Marketing instance. For this example, we are going to create a **New** journey based on our **High Value Online Customers** segment. This journey will be one that sends out our Monthly Newsletter to our High Value Customers.

### Review the Segments

1. Log into your Dynamics instance at https://ORGNAME.crm.dynamics.com

2. Open the **Marketing** application

	![Picture 1963](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image19.jpeg)

3. Click on **Segments** in the left-hand menu, in the **Customers** section

4. Click on the **HighValueOnlineCustomers** segment to open it. You will notice that it lists the contacts who are members of this segment

	![Picture 1959](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image20.jpeg)

5. To use the Segment in a marketing journey you must first mark it as 'Live'. Click the **Go Live** button in the top menu bar to accomplish this. Once the status for the segment change to **Live** you can continue

	![Picture 1961](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image21.jpeg)

### Create the Newsletter Email

1. Click on **Marketing emails** in the left-hand menu

2. Click **New** in the top menu bar

3. In the template selection pop-up click on **Filter**, then in the **Purpose** filter it to **Newsletter** and then select any of the newsletter options and click on **Select**

	![Picture 1961](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image21-2.png)

4. You are welcome to customize anything in the newsletter you'd like, but for this lab we really don't need to customize anything

5. Let's give this email a subject, **Monthly Customer Newsletter**

	![Picture 1961](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image21-3.png)

6. Our email needs a name. Click on the dropdown next to **Draft** in the top right and in the pop-up enter **High Value Monthly Newsletter** in the name field

	![Picture 1961](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image21-4.png)

7. We are now done with our email. The final thing we need to do is **Save** it and then click the **Go Live** button

8. Before moving on we will wait for the email to go live. Click on **Marketing emails** in the left-hand menu and wait for the email to switch from "Go live" to "Live". (You may need to click the **Refresh** button to see it update. It can take a few minutes)

### Create the Customer Journey

1. Click on **Customer journeys** in the left-hand menu

2. Click on **New** in the top menu

3. Click on the **Monthly Newsletter** template. We'll use the defaults of sending every 30 days for 12 months so just click **Select**

	![Picture 1961](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image21-5.png)

4. First let's name our Journey by clicking on the dropdown in the top right and setting the Name field to **High Value Customers (Monthly Newsletter)**. Also change Is Recuring to **Yes**

	![Picture 2133](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image22.jpeg)

5. Next, we will tell the system which segment we want to use. Click the **Set audience** link

	![Picture 2172](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image23.jpeg)

6. In the Audience pop-out that opens type **High** in the segment lookup box and select the **HighValueOnlineCustomers** segment from the list

	![Picture 2174](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image24.jpeg)

7. Click **Save** in the top menu

8. Next, we need to configure the email. Click on the +sign between the Start and End indicator and click the **Send and email** option

	![Picture 2217](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image25.jpeg)

9. In the **Send an email** pop-out type in **High** and select the **High Value Monthly Newsletter** email we created previously

	![Picture 2219](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image26.jpeg)

10. The final step before we can publish our journey is to set the timeframe. Click on the **General** tab and set the **End date and time** to be just over 1 year from today

	![Picture 2219](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image26-2.png)

11. We also need to set the recurrence count to 12 and interval to 30

	![Picture 2255](Static/Lab_5_Extend_the_Solution_with_Dynamics_365_image27.jpeg)

12. Click **Save** and then go back to **Designer** tab and hit **Go live** in the top menu

You are done! You have just created a Customer Journey in Dynamics 365 Marketing based on a Segment of customers which you brought in from Dynamics 365 Customer Insights.

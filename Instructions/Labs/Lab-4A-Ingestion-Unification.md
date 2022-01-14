# About the Hands-on Lab

Unlike traditional approaches for realising a 360degree view of the customer with a large amount of coding involved, Dynamics 365 Customer Insights (CI) is a finished SaaS solution which allows you to adopt an agile project management approach and deliver value in a matter of weeks. 

By attending this Hands-on Lab, you will learn stepby-step how to set up, configure and use Dynamics 365 Customer Insights. To bring this to life, we are looking at a typical customer analytics project for our example company, Contoso Coffee. 

We will introduce the business pain points, goals and 

high-priority use cases that Contoso has identified around their customer data initiative, and then realise a working prototype solution today. 

 
# Lab Scenario: Contoso Coffeee
 

![Picture 230](Static/Lab_4A_image2.jpeg)Contoso Coffee produce high-quality coffee and coffee machines, which they retail through channels including new Contoso Retail Stores in premium locations, premium food resellers and the Contoso Coffee Web 

Site. 

Contoso plan to further expand their offerings with 

Contoso Cafes and a new Connected Coffee Machine which can trigger refill orders and alert Contoso service about any issues. 

This new offering will help them to build direct relationship with their customers and learn more about how customers consume their products 

 

 

 

## Business Objective 

Contoso wish to own and build a meaningful, direct relationship with all consumers to deliver an exceptional, personalised customer experience through relevant communications, personalised recommendations, and services. 

Increase customer attraction and retention by making customers feel valued through experiences that customers love. 

 

## Challenges 

Transactional Relationship 

Their existing business model means that they lack a direct relationship with their customers. 

Data Silos 

They are unable to deliver personalised customer experiences. 

  

## Existing Data Landscape 

Fractured Customer Data 

![Picture 288](Static/Lab_4A_image3.jpeg)With multiple systems, Contoso has multiple records for the same person. This causes a disjointed experience to the customer who expects to be treated as one person regardless of the channel they are transacting upon. 

Multiple Platforms 

The architecture at Contoso has evolved through acquisition and legacy systems meaning that data can reside in not only different systems, but different platforms across multiple clouds and on premise. 

Non-Customer Data 

Contoso are drawing correlations between noncustomer data and the impact it has on customer experiences, including data from third parties such as weather data. 

 

## Contoso Coffee Customer Insights Project 

Contoso management is tasking IT and Line of Business teams with the following: 

- Establish a customer data hub combining all customer related data from siloed sources. 

- Realise a unified Contoso Customer profile. 

- Provide a 360-degree view of the customer for service agents (embedded into D365 for Service) as well as store managers (through Power BI).. 

- Deliver a Contoso Coffee Greeter App (through PowerApps), to enable in store retail staff to deliver personalised service and recommendations. 

- Automate various business processes like email alert when customers churn rate surges using Power Automate. 

 

## Contoso Coffee Customer Insights Project 

You have been selected as the project manager for the implementation of Dynamics 365 Customer Insights at Contoso Coffee. As an experienced project manager, you devise the following plan: 

1. Create a Customer Insights environment 

2. Ingest data from highest priority data sources from within the business 

	- Point-of-Sale (POS) 

	- Loyalty Data 

	- Ecommerce Customers and Web Purchases 

	- Subscription data (optional and will happen in the intelligence module lab) 

	- Dynamics 365 CRM (Will be done in the Dynamics module labs) 

	- Contoso Hotel data (Optional and will be done in the Advanced module lab) 

 

3. Configure and realise a unified customer profile from ingested data 

 

4. Configure business and customers measures in Customer Insights to identify customers with higher than average spend in store and online. 

 

5. Build sample customer segments for Marketers to deliver personalised and targeted marketing communications 

 

6. Configure Customer Insights contact cards and embed into Dynamics 365 to empower Contoso Customer Service Advisors 

 

7. Create Power BI dashboard for Store Managers 

 

8. Create Greeter App with PowerApps for Contoso Coffee retail staff, empowering them to deliver personalised service 

 

9. Use Microsoft Power Automate to capture Customer check ins at Contoso retail stores and deliver personalised recommendations to Contoso Retail staff 

 

10. Demo Customer Insights prototype to group of pilot users and gather feedback 

 

 

# Module Introduction

## Lab pre-requisites: 

Before you can start this exercise, you must have completed Lab 3 to setup your environment. 

 

## Data Ingestion & Unification 

As Project Manager for Contoso Retail, you will create a unified customer profile by ingesting key sources of customers data and following the Map, Match and Merge process. 

## Creating Relationships 

You will create different kinds of relationships to help join the different datasets together which help support other areas of Customer Insights which use these relationships to traverse the data sets. 

## Measure Calculation 

You will calculate previously unobtainable key Business and Customer KPIs including 

Lifetime Spend, Club Points Balance, Average in Store and Average Online Purchase values. 

## Objectives 

- Ingest siloed data sources 

- Follow Map, Match and Merge to create a Unified Profile 

- Create the required Relationships between data sets 

- Create the Measures (KPIs) we want to track 

 

 

# Approximate Time to Complete -  90mins 

# Familiarize yourself with Customer Insights

In this task, you will explore the pre-configured Demo environment to familiarize yourself with Customer Insights Hub. 

1. Sign-into Customer Insights at https://home.ci.ai.dynamics.com 

 

2. In the Environment selector in the top right-hand corner, select the Demo Environment 

	![Picture 1](Static/Lab_4A_picture1.png)

3. On the Home Page, note how the key Insights are highlighted: 

 

	- KPIs (Business Measures), including Average Online Spend Per Customer and Average Churn Score. 

		![Picture 544](Static/Lab_4A_image4.jpeg) 

- Audience Enrichment pulled in from Microsoft proprietary data (including Microsoft Bing). Enrich Customer Profiles and Audience segments to unlock affinities for brands and interest categories that may be like your customers, by matching demographic data. 

	![Picture 606](Static/Lab_4A_image5.jpeg) 

- Segments - customers grouped into cohorts based on demographic, transactional, or behavioural customer attributes. Using segmentation, you can target promotional campaigns, sales activities, and customer support actions to achieve your business goals. 

	![Picture 608](Static/Lab_4A_image6.jpeg) 

- Check this out: links to Customer Insights documentation and help on core topics such as data ingestion, Map, Match and Merge and Segmentation 

	![Picture 610](Static/Lab_4A_image7.jpeg) 

4. Explore the left-hand menu options to familiarise yourself with the navigation. 

 

**Home**: Home Page 

 

**Customers**: View cards for unified Customer Profiles 

 

**Segments**: Define Segments: Cohorts of Customers based on similar demographic, transactional or behavioural attributes. Use these for targeted marketing, utilising previously siloed data. 

 

**Measures**: Define key Business and Customer KPIs. 

Such as Customer Lifetime Value, Average Purchase Value and Frequency, CSAT and identify high-value customers. 

 

**Intelligence**: Here you can leverage the existing Out of the Box (OOB) models or add custom Azure machine learning models to make predictions with your unified customer data 

 

**Data**: Ingest siloed demographic, transactional of behavioural data. Map, match and merge into a Unified Customer Profile. View your entities and define activity types and their relationships to your customers. 

 

**Enrichment**: Go beyond your unified profile and enrich customer profiles with Microsoft Proprietary Data from the Microsoft Graph. Unlock data on affinities for hundreds of brands and dozens of interest-categories. These affinities are extracted for profiles that might be like your customers. 

 

**Admin**: Administer Roles, Permissions, APIs and Export Destinations for Customer Segments. 

 

 

 
# Exercise 1 - Data Ingestion

In this lab you will become familiar with ingesting data from multiple sources. As Project Manager for Contoso Retail, you have already identified that key sources of data include eCommerce Customers, Online Purchases, in-store Point of Sales Purchases, data from Contoso Retail Loyalty Card scheme, Subscription data, Contoso Hotel data and Contacts from your Dynamics 365 CRM. 

Although Customer Insights has connectors to 35+ data sources and applications (including Dynamics 365 & the Common Data Service for Apps), for this lab you will be using the 'Text/CSV' connector. 

## Data Sources 


| Entity| Description| Connection |
| - | - | - |
| eCommerceContacts| Extract of Customers who have made an online purchase| https://aka.ms/CI-ILT/Contacts |
| LoyaltyScheme| Extract of Customers who've signed-up for the Contoso Retail Loyalty Card Scheme| https://aka.ms/CI-ILT/LoyaltySchemeCustomers |
| OnlinePurchases| Extract of purchases made via the Contoso Retail Website| https://aka.ms/CI-ILT/OnlinePurchases |
| POSPurchases| Extract of in-store purchase detail| https://aka.ms/CI-ILT/POSPurchases |
| WebsiteReviews| Online Website Reviews from online users| https://aka.ms/CI-ILT/WebReviews |


 

  

## Data Source Model 


 ![Picture 815](Static/Lab_4A_image8.jpeg) 

Note: Some of this data will be ingested in later labs 

  

## Task 1 -  Ingest Customer Data from eCommerce Platform 

 

1. Sign-in to Customer Insights (http://home.ci.ai.dynamics.com) and select your Environment from the drop-down in the top right-hand corner. 

	![Picture 865](Static/Lab_4A_image9.jpeg) 

2. Within Customer Insights, expand Data on the left menu and click Data Sources 

 

3. Click Add Data Source, then choose from the available methods of ingesting data. Currently, CI provides import data via various data connectors, connect to your own data lake, connect to Common Data Service. For this lab, choose Import data and name the source eCommerce, then click Next button 

	![Picture 2](Static/Lab_4A_picture2.png)

4. You will be presented with a view of data source connectors that Customer Insights is able to ingest. Take note of the connector types available, including Common Data Service for Apps. Select the Text/CSV Connector. 

	![Picture 912](Static/Lab_4A_image10.jpeg) 

5. Enter the URL for eCommerce Contacts data set, https://aka.ms/CI-ILT/Contacts, and click Next. 

	![Picture 914](Static/Lab_4A_image11.jpeg) 

6. You should now see the data from the source tabulated. Click Transform data to configure the datatypes and formats for the data you ingest. 

	![Picture 916](Static/Lab_4A_image12.jpeg) 

7. You will notice that the column heading has appeared in the first row of the data. To correct this, click Transform and Use first row as headers. 

	![Picture 1007](Static/Lab_4A_image13.jpeg) 

8. Because we have ingested data from a Text/CSV source, all columns have been defaulted to a 'Text' Data Type. To successfully ingest and model the data, we can set the datatype for non-text columns. 

To change the datatype, click the ABC icon within the column heading. Update the datatype for the columns listed below. 

| Column Heading| New Data Type |
| - | - |
| DateOfBirth| Date |
| CreatedOn| Date |
| Income| Currency |


![Picture 1013](Static/Lab_4A_image14.jpeg)


9. In the 'Name' field on the right-hand pane, rename your data source from Query to Contacts and hit Next. Click Save. 

  
	![Picture 3](Static/Lab_4A_picture3.png)

Congratulations! - You have now successfully created your first data source with a data set! 

 
 

Note: Column names can only contain letters, numbers, and underscores. They cannot contain a space and must begin with a letter. If you have data where column name(s) have a space or do not begin with a letter you will want to fix that either within Power Query or before the data is brought into Customer Insights. 

 

As we talked about in the session, a data source can contain more than one data set to help group data sets that have a relationship together. In this case because we have two data sets from the eCommerce site, we will group them into the same data source. 

 

While you are still in the Power Query screen for the eCommerce : Contacts data set let's click the Get Data button in the ribbon bar to add another data set to this same eCommerce data source. 

 
![Picture 4](Static/Lab_4A_picture4.png)
 

We'll continue importing the next data set in the next task. 

 

  

# Task 2 - Ingest Online Purchase Data 

 

In this next task, we will ingest Online Purchase data, representing purchases made via the Contoso Coffee website. If you have just completed the previous task, skip to step 4. 

1. Within Customer Insights, expand Data on the left menu and click Data Sources 

 

2. You should see your eCommerce data source. Select it and click either the three vertical dots and choose Edit or click directly on the pen icon. 

	![Picture 1125](Static/Lab_4A_image15.jpeg) 

3. You should be presented with the view of the eCommerce Contacts data that you ingested in Task 1. In the action menu, click Get Data. 

	![Picture 5](Static/Lab_4A_picture5.png) 

4. You will be presented with a view of data source connectors that Customer Insights is able to ingest, select the Text/CSV Connector. 

 

5. Enter the URL for the Online Purchases data, https://aka.ms/CI-ILT/OnlinePurchases, and click Next and then Create. 

 
6. As you did in Task 1, click on Use first row as headers or you can click on Transform tab and click Use first row as headers. 

	![Picture 6](Static/Lab_4A_picture6.png) 

	Once completed, update the datatypes for the following columns

	| Column Heading| New Data Type |
	| - | - |
	| PurchasedOnh| Date |
	| TotalPrice| Currency |
    ![Picture 7](Static/Lab_4A_picture7.png) 
7. Name your query Purchases and click Save. 

	![Picture 8](Static/Lab_4A_picture8.png) 
 

  

## Task 3 - Ingest Customer Data from Loyalty Scheme 

 

1. Within Customer Insights, expand Data on the left menu and click Data Sources 

 

2. Click Add Data Source, then choose from the available methods of ingesting data. Currently, CI provides import data via various data connectors, connecting to your own data lake, or connecting to the Common Data Service. For this lab, choose Import data and click Next and name the source Loyalty, then click Next. 

	![Picture 9](Static/Lab_4A_picture9.png) 
  

3. You will be presented with a view of data source connectors that Customer Insights is able to ingest. Take note of the connector types available, including Common Data Service. Select the Text/CSV Connector. 

	![Picture 1313](Static/Lab_4A_image16.jpeg) 

4. Enter the URL for the Loyalty Customer data, https://aka.ms/CI-ILT/LoyaltySchemeCustomers and click Next and click Transform data. 

	![Picture 1315](Static/Lab_4A_image17.jpeg) 

5. You should now see the data from the source tabulated. Here you can configure the datatypes and formats for the data you ingest. 

 

You will notice that the column heading has appeared in the first row of the data. To correct this, click Transform and then Use First Row as Headers or click it directly from the Home tab. 

![Picture 1317](Static/Lab_4A_image18.jpeg) 

 

6. Because we have ingested data from a Text/CSV source, all columns have been defaulted to a ‘Text’ Data Type. To successfully ingest and model the data, we can set the datatype for non-text columns. 

 
To change the datatype, click the ABC icon within the column heading. Update the datatype for the columns listed below. 

| Column Heading| New Data Type |
| - | - |
| DateOfBirth| Date |
| RewardPoints| Whole Number |
| CreatedOn| Date |


![Picture 1403](Static/Lab_4A_image19.jpeg)

 

7. In the 'Name' field on the right-hand pane, rename your data source from Query to Customers and click Save. 

![Picture 10](Static/Lab_4A_picture10.png)
  

 

# Task 4 - Ingest Customer Data from Point of Sale Purchases  

 

1. Within Customer Insights, expand Data on the left menu and click Data Sources 


Click Add Data Source, choose Import data and name the source PoS, then click Next 

![Picture 11](Static/Lab_4A_picture11.png)

2. You will be presented with a view of data source connectors that Customer Insights is able to ingest. Take note of the connector types available, including Common Data Service. Select the Text/CSV Connector. 

![Picture 1455](Static/Lab_4A_image20.jpeg) 

3. Enter the URL for the Point of Sale Purchases, https://aka.ms/CI-ILT/POSPurchases, and click Next and click Transform data 

	![Picture 12](Static/Lab_4A_picture12.png)

4. You should now see the data from the source tabulated. Here you can configure the datatypes and formats for the data you ingest. 

 

	You will notice that the column heading has appeared in the first row of the data. To correct this, click Use First Row as Headers from Home or click Transform and then Use First Row as Headers. 

	![Picture 1553](Static/Lab_4A_image21.jpeg) 

5. Because we have ingested data from a Text/CSV source, all columns have been defaulted to a ‘Text’ Data Type. To successfully ingest and model the data, we can set the datatype for non-text columns. 

 

To change the datatype, click the ABC icon within the column heading. Update the datatype for the columns listed below. 

| Column Heading| New Data Type |
| - | - |
| PurchasedOn| Date |
| TotalPrice| Currency |
| RewardPointsAdded| WholeNumber |

![Picture 13](Static/Lab_4A_picture13.png)
 


6. In the Name field on the right-hand pane, rename your data source from Query to Purchases and click Save. 

	![Picture 14](Static/Lab_4A_picture14.png)

 


# Task 5 - Ingest Customer Data from Website Reviews 

 

1. Within Customer Insights, expand Data on the left menu and click Data Sources 

 

2. Click Add Data Source, choose Import data and name the source Website, then click Next. 

	![Picture 15](Static/Lab_4A_picture15.png)
 

3. You will be presented with a view of data source connectors that Customer Insights is able to ingest. Take note of the connector types available, including Common Data Service. Select the Text/CSV Connector. 

	![Picture 1641](Static/Lab_4A_image22.jpeg) 

 

4. Enter the URL for the Website Reviews, https://aka.ms/CI-ILT/WebReviews, click Next and then click Transform data. 

	![Picture 16](Static/Lab_4A_picture16.png)
 

5. You should now see the data from the source tabulated. Here you can configure the datatypes and formats for the data you ingest. 

 

You will notice that the column heading has appeared in the first row of the data. To correct this, click Use First Row as Headers from Home or click Transform and then Use First Row as Headers. 

![Picture 1730](Static/Lab_4A_image23.jpeg) 

6. Because we have ingested data from a Text/CSV source, all columns have been defaulted to a ‘Text’ Data Type. To successfully ingest and model the data, we can set the datatype for non-text columns. 

To change the datatype, click the ABC icon within the column heading. Update the datatype for the columns listed below. 

| Column Heading| New Data Type |
| - | - |
| ReviewRating| Whole Number |
| ReviewDate| Date |

![Picture 17](Static/Lab_4A_picture17.png)



7. In the Name field on the right-hand pane, rename your data source from Query to Reviews and click Save. 

	![Picture 18](Static/Lab_4A_picture18.png)



# Exercise 2 - Data Unification

Having ingested the raw data from your data sources into entities you will now begin the Map, Match, Merge process to create a single Unified Customer Profile by merging data from each customer profile source. 

To do this you will first map your ingested entities against a standard model and select the Primary Key for each of your profiled entities. Following the completion of this you will then create your Match Rule that will be used to match contacts from all customer entities. 

Finally, running the Merge process will create a single set of unique Customers having matched profiles from all customer entities using your match rules. 

Your objective is to find out how many unique customer profiles Contoso Retail has across various data sources. 

 

## Task 1 - Map contacts to common data types 

 

1. Map contacts from eCommerce and Loyalty data to common data types. In the left menu click Unify -> Map -> Select Entities 

 

Select the entities that represent the customer profile - Contacts (eCommerce), Customers (Loyalty) then click Apply 

![Picture 1858](Static/Lab_4A_image24.jpeg) 

 

2. You will now be presented with the mappings of your source entity against standard model types. You can review the types in the table. 

 

You must choose a 'Primary Key' for each entity you have ingested. The primary key must be a unique reference. For eCommerce Contacts select ContactId as the Primary Key. 

![Picture 1906](Static/Lab_4A_image25.jpeg) 

3. Our eCommerce Contacts data contains a column named Email Subscriber which will be mapped to an incorrect type, Identity.Service.Email because of the name. Open the dropdown for this field and select the empty option (nothing/blank). If we do not do this then the system default to merging this field with the Email fields which we do not want. You will also need to do this for Income which may get mapped to Identity.Service.Phone 

	![Picture 19](Static/Lab_4A_picture19.png)

4. Select Loyalty Customers under 'Entities' and set LoyaltyID as the Primary Key.

	![Picture 1960](Static/Lab_4A_image26.jpeg) 

5. Our Loyalty data contains a column named RewardPoints which will be mapped to an incorrect type, Measurement.Duration because of the name/type. Open the dropdown for this field and select the empty option (nothing/blank). 

 

6. Then click Save in the top left-hand corner. 

 

7. Click Match 

	![Picture 1962](Static/Lab_4A_image27.jpeg) 

## Task 2 - Specify Match Order 

 

For the next stage, we must select the order in which to merge the profiles. You will be able to merge attributes to ensure that the unified profiles are complete as well as the priority of which sources to use for those attributes. 

 

1. If you haven't already, Click Match in the top menu on the page. 

	![Picture 2026](Static/Lab_4A_image28.jpeg) 

2. You should select the most complete or accurate profile source as the Primary. Click Match Set Order 

 

3. In the Primary drop-down list select Contacts : eCommerce as the primary Source and choose to Include all records 

 

4. In the Entity 2 drop-down list select Customers : Loyalty and choose to include all records. 

	![Picture 2028](Static/Lab_4A_image29.jpeg) 

5. Click Done   

## Task 3 - Create a Match Rule 

 

In this step, you will create a simple rule used to match records together. Rules can consist of single (e.g. based on ID) or multiple conditions (e.g. Full Name, Postcode, Date of Birth). 

 

For further details on Match Rules, please see Customer Insights documentation. 

1. Click Add rule or click the + button to the right of the 'needs rule' indicator. 

![Picture 2092](Static/Lab_4A_image30.jpeg) 

2. Add your first condition using FullName 

	- For entity Contacts : eCommerce select FullName - For entity Customers : Loyalty select FullName - Leave the Normalize blank. 

	- Set Precision Level to Basic and Precision value to High 

	![Picture 2094](Static/Lab_4A_image31.jpeg) 

3. Enter the name FullName, Email for the new rule. 

 

4. Add a second condition for email address by clicking Add Condition 

	- For entity Contacts : eCommerce select Email - For entity Customers : Loyalty select Email - Leave the Normalize blank. 

	- Set Precision Level to Basic and Precision value to High 

 

Your match rule should now appear like the below. Click Done. 

![Picture 2153](Static/Lab_4A_image32.jpeg) 

5. In the top left-hand corner click Save and then Run. 

Customer Insights is now matching customer data from all your sources of customer information - to identify how many unique customer profiles you would have based on your rules 

How Many Unique Customers do you have when combining your datasets? 

## Task 4 - Precision

In Task 3, we used High Precision in the match-rule against Full Name. In this task, you will adjust the precision level, to create a higher number of matches, by including matches of a lower confidence (resulting in lower number of unique profiles). 

 

Notes on Precision - Exact, on the right-side of the scale, will match records where your condition has an exact match. Select one of the other levels to match records that are not 100% identical. High fits cases where precision is more important than reach, such as a financial service to a specific customer. Low fits cases where the opposite is true, such as a marketing campaign. The Medium level serves as a middle-ground option. 

 

1. Expand your rule and click the ![Picture 2307](Static/Lab_4A_image33.jpeg) to edit the 'Match' Rule

![Picture 20](Static/Lab_4A_picture20.png)

2. Move the Precision slider for your FullName match from High to Low. Then click Done. 

 

3. Click Save and then Run. 

  

4. Once the match process has completed, Open the Match Preview to see the match results and the Confidence Score. This shows how Customer Insights matched the data tables based on the rules you have defined. – You will notice that some profiles have been created with a low confidence of matching. 

	![Picture 21](Static/Lab_4A_picture21.png)

5. Close the preview and click the ![Picture 2307](Static/Lab_4A_image33.jpeg) to edit the match rule. Click the Preview button below the FullName rule. 

	![Picture 22](Static/Lab_4A_picture22.png)

6. Here you can preview the number of Unmatched and Matched for your full name criteria. This screenshot shows that there were 52 Unmatched and 4950 Matched. Note: Your number may be slightly different if the underlying data sources have changed since the docs were created or the matching algorithm has changed. 

 

	Click Preview Data under Unmatched or Matched to preview the matches. Notice how High Confidence uses exact spelling but can match even if the name format (First Name, Last Name / Last Name, First Name) is different. With Low confidence, notice how matches are made even when names are not spelled identically. 

	![Picture 2313](Static/Lab_4A_image34.jpeg) 

7. Close the Criteria Preview page. And click Cancel. 

 

How many Unique Customer Profiles do you have now? 

## Task 5 - Merge 

The merge phase is the last phase in the data unification process. Its purpose is reconciling conflicting data and to define the attributes that will be used in your unified customer profile. 

 

A Merged attribute is an attribute that exists in more than one data source and represents the same piece of data. For example, we may have ‘Email Address' in both eCommerce Customers and Loyalty Customer data sources. 

Customer Insights will attempt to identify attributes to be merged using their mapping to the standard data types we used in the Map stage. 

1. Click Merge. 

 

You will be presented with the Merge screen. Note that attributes from different sources that are of the same type (e.g. First Name) have been 'Merged'. 

![Picture 23](Static/Lab_4A_picture23.png) 
![Picture 24](Static/Lab_4A_picture24.png) 
  

2. Click the '>' chevron on the FirstName merged attribute. You should see that the FirstName attribute in eCommerce : Contacts is ranked number 1. This denotes that where you have a matching customer profile in LoyaltyScheme and eCommerce, the FirstName taken from eCommerce : Contacts will be the primary. 

	![Picture 25](Static/Lab_4A_picture25.png) 


3. Click the ![Picture 2455](Static/Lab_4A_image35.jpeg) button on the row for the FirstName merged attribute and click Edit. Note that you’re able to change the display name and importance rank for the merged attribute. The Display Name is the name that will be used in the Merged Profile. 

 
	![Picture 26](Static/Lab_4A_picture26.png) 
  

4. Click Cancel. 

 

5. Note that the Primary Keys from the original sources cannot be merged. For example, we have a ContactId as the primary key from eCommerce : Contacts and we also have ContactId within Loyalty : Customers. In fact, we are merging these records not on ContactId, but on FullName & Email. 

 

6. On the ContactId for the Loyalty : Customers Entity, click the edit button ![Picture 2463](Static/Lab_4A_image36.jpeg) and rename the Display Name to ContactIdLOYALTY to differentiate the item from the other IDs ingested and help avoid any confusion later. 

	![Picture 27](Static/Lab_4A_picture27.png)


7. Click Save and Run -> Run Merge and downstream processes to start the Merge Process. 

Congratulations! You have successfully Ingested, Mapped, Matched and Merged data from multiple sources within Customer Insights to create a Unified Customer Profile that can be used to gain insights into your whole customer base! 


# Exercise 3 - Creating Relationships and Measures

Overview of Relationships & Measures 

Before creating a measure, we need to understand the purchases made by a customer both online and instore. To do this we need to define the relationship between Purchases (made online and in store) and the Unified Customer Profile. 

Relationships help you connect entities and generate a graph of your data. Relationships are used when entities share a common identifier (foreign key) that can be referenced from one entity to another. Connected entities enable you to define segments and measures based on multiple data sources. 

 

![Picture 2582](Static/Lab_4A_image37.jpeg) 

 

For example, Customer has a One to Many relationships with PoS Purchases. (One loyalty scheme customer may make multiple purchases). - This is an example of the relationship we will be defining. 

 

 ![Picture 2584](Static/Lab_4A_image38.jpeg) 

 

## Measures 

Measures enables you to define all the key performance indicators (KPIs) that best reflect your specific business performance and health. Measures can either be customer-related measures such as Lifetime Value or business-health measures such as Monthly Active Users. 

 

Customer Insights provides an intuitive experience to build different types of measures, with a query-builder wizard that doesn't require the user to manually code or validate the query. 

Measures are calculated on a series of interactions that a company has with a customer, gathered from multiple data sources. Interactions are any customer touch points - these could include purchases, customer service cases, emails, phone calls, branch visits. In other scenarios interactions could also be data gathered from connected devices, withdrawals, or deposits in banking, entry/exist of a premises or area etc. 

Contoso Coffee are looking to uncover six simple Measures based on the data ingested, that will help them to identify high-value customers and their preferred purchase method (Online or Instore) 

 

Business Measures: 

- Average Store Purchase Value ($) 

- Average Web Purchase Value ($) 

Customer Attribute: 

- Lifetime Spend ($) 

- Total Club Points 

- Average Store Purchase ($) 

- Average Web Purchase ($) 

 

 

 

 

 

 

 

 

 

 

 

  

## Task 1 - Define the Relationship Between Unified Profiles and Web Purchases 

 

Define the relationship for CustomerPurchasesEcom 

1. Under Data within the left-hand menu, click Relationships in the left-navigation menu 

2. Click New Relationship 

3. Name the relationship CustomerPurchasesEcom 

4. In Description add Online Purchases to Unified Customer Profile 

5. Set Source details entity to Purchases: eCommerce and Cardinality to Many 
6. Set Target details entity to Customer : CustomerInsights and Cardinality to One 

7. Set equivalent fields to ContactId for both the Source and Target fields. 
8. Click Save 

	![Picture 28](Static/Lab_4A_picture28.png)
   

## Task 2 - Define the Relationship between Unified Profiles and Store Purchases 

 

Define the relationship for CustomerPurchasesPOS 

1. Under Data within the left-hand menu, click Relationships in the left-navigation menu 

2. Click New Relationship 

   Name the relationship CustomerPurchasesPOS 

3. In Description add Point of Sale Purchases to Unified Customers 

4. Set Source details entity to Purchases : PoS and Cardinality to Many 

5. Set Target details entity to Customer : CustomerInsights and Cardinality to One 

6. Set equivalent fields to LoyaltyId for both Source field and Target field
7. Click Save 

	![Picture 29](Static/Lab_4A_picture29.png)

 

You should now have the following relationships defined 

 

## Task 3 - Define Two Business Measures 

 

Business Measures helps you track your business performance and health. 

Examples: Average Sales per Customer and Monthly Active Users (MAU). 

The business has asked you to calculate the Average Store Purchase and Average Web Purchase values for the Contoso Coffee business. 

### Average Store Purchase Value (Business Measure) 

Average value of all in store purchases made at Contoso Coffee 

1. Click Measures on the left-hand menu. 

 

2. Click the New button in the top left-hand corner, then Build your own. 

3. Next to the Untitled measure text, select Edit name. 
	![Picture 30](Static/Lab_4A_picture30.png)
 

4. Set the name to Average Store Purchase Value ($), select Done. 

	![Picture 31](Static/Lab_4A_picture31.png)
 
 

5. Under Set up your measure calculations, select Dimensions (1). 
	![Picture 32](Static/Lab_4A_picture32.png)
 

6. Delete Customer: CustomerInsights.CustomerId and select Apply. (By deleting the customer dimension, these changes the measure from a customer measure to a business measure).

	![Picture 33](Static/Lab_4A_picture33.png)
 

7. Next to Calculation 1, click Edit name 

 

8. Set the Display name to Average Store Purchase Value ($). 

 

9. Verify the Attribute name is set to AverageStorePurchaseValue.

	![Picture 34](Static/Lab_4A_picture34.png)
 

10. Select Done. 

  

11. Under the Average Store Purchase Value ($) calculation, click Select Function and choose Average. 

	![Picture 35](Static/Lab_4A_picture35.png)
 

12. Select Add attribute, expand Purchases : PoS, and select TotalPrice. 

	![Picture 36](Static/Lab_4A_picture36.png)
 

 

13. Select Add. 

 

14. Select the Run button to complete your measure. 

 

  

### Average Web Purchase Value (Business Measure) 

Average value of all web purchases made at Contoso Coffee 

1. Click Measures on the left-hand menu. 

 

2. Click the New button in the top left-hand corner, then Build your own. 

 

3. Next to the Untitled measure text, select Edit name. 

	![Picture 37](Static/Lab_4A_picture37.png)

4. Set the name to Average Web Purchase Value ($), select Done. 

	![Picture 3105](Static/Lab_4A_image39.jpeg) 

5. Under Set up your measure calculations, select Dimensions (1). 

	![Picture 38](Static/Lab_4A_picture38.png)
 

  

6. Delete Customer: CustomerInsights.CustomerId and select Apply. (By deleting the customer dimension, these changes the measure from a customer measure to a business measure)
	![Picture 39](Static/Lab_4A_picture39.png) 

 

7. Next to Calculation 1, click Edit name 

 

8. Set the Display name to Average Web Purchase Value ($) 

 

9. Verify the Attribute name is set to AverageWebPurchaseValue. 

	![Picture 40](Static/Lab_4A_picture40.png)

10. Select Done. 

  

11. Under the Average Web Purchase Value ($) calculation, click Select Function and choose Average. 

	![Picture 41](Static/Lab_4A_picture41.png)

 

12. Select Add attribute, expand Purchases : eCommerce, and select TotalPrice. 

	![Picture 42](Static/Lab_4A_picture42.png)
 

13. Select Add. 

 

14. Select the Run button to complete your measure. 

 

  

## Task 4 - Define Customer Measures  

 

We will need two customer measures that can be used to calculate a customer attribute. We will create one measure to determine the customers total spend on Online Purchases and one measure to determine their total spend on In-Store purchases. Once we create these, we can then create a customer attribute to add those two together. 

### Total In-Store Spend (Customer Measure)  

Total of all purchases made online 

1. If necessary, click Measures on the left-hand menu. 

2. Click the New button in the top left-hand corner, then Build your own. 

3. Next to the Untitled measure text, select Edit name. 

4. Set the name to Total In-Store Spend, select Done. 

5. Under the Total In-Store Spend calculation, click Select Function and choose Sum. 

6. Select Add attribute, expand Purchases : POS, select TotalPrice, and click Add. 

7. Under Set up your measure calculations, select Dimensions (1). 

8. Select Edit Dimensions 

9. Expand Purchases: PoS, select LoyaltyID, and click Done. 

	![Picture 43](Static/Lab_4A_picture43.png)
 

10. Click Apply 

11. Select the Run button to complete your measure. 

	![Picture 44](Static/Lab_4A_picture44.png)

  

## Total Online Spend (Customer Measure)  

Total of all purchases made in store 

1. In Necessary, click Measures on the left-hand menu. 

2. Click the New button in the top left-hand corner, then Build your own. 

3. Next to the Untitled measure text, select Edit name. 

4. Set the name to Total Online Spend, select Done. 

5. Under the Total Online Spend calculation, click Select Function and choose Sum. 

6. Select Add attribute, expand Purchases: eCommerce, select TotalPrice and click Add. 

7. Under Set up your measure calculations, select Dimensions (1). 

8. Select Edit dimensions 

9. Expand Purchases: eCommerce, select ContactId, and click Done. 

	![Picture 46](Static/Lab_4A_picture46.png)
 

10. Click Apply 

11. Select the Run button to complete your measure. 

	![Picture 47](Static/Lab_4A_picture47.png)

 

  

## Task 5 - Define Customer Attributes 

 

Customer Attributes are a single field per customer that reflects a score, value, or state for each customer. Examples are Lifetime Value and Total Sales. 

In this task you will create measures to calculate the Lifetime Spend ($), Total Club Points, Average Web Purchase Value ($) and Average Store Purchase Value ($) of each customer. By calculating value for the business and customers, Contoso Coffee can identify customers with a higher than average spend on each channel. 

### Total Club Points (Customer Attribute) 

Total Loyalty Points earned by each customer 

1. If necessary, click Measures on the left-hand menu. 

2. Click the New button in the top left-hand corner, then Build your own. 

3. Next to the Untitled measure text, select Edit name. 

4. Set the name to Total Club Points, select Done. 

5. Under the Total Club Points calculation, click Select Function and choose Sum. 

6. Select Add attribute, expand Purchases : POS, select RewardPointsAdded and click Add. 

7. Select the Run button to complete your measure. 

	![Picture 48](Static/Lab_4A_picture48.png)
 

  

## Lifetime Spend (Customer Attribute)  

Total value of all purchases made for each customer 

1. If necessary, click Measures on the left-hand menu. 

2. Click the New button in the top left-hand corner, then Build your own. 

3. Next to the Untitled measure text, select Edit name. 

4. Set the name to Lifetime Spend ($), select Done. 

5. Under the LifetimeSpend calculation, click Select Function and choose Sum. 

6. Select Add attribute. 

7. Select Measures, expand TotalInStoreSpend : CustomerInsights, select Calculation 1, and select Add. 

	![Picture 49](Static/Lab_4A_picture49.png)
 

8. Select the Plus Sign icon next to Add Attribute 

9. Select Add attribute. 

10. Select Measures, expand TotalOnlineSpend : CustomerInsights, select Calculation 1, and select Add. 

	![Picture 50](Static/Lab_4A_picture50.png)

11. Select the Run button to complete your measure. 

	![Picture 51](Static/Lab_4A_picture51.png)

## Average Store Purchase (Customer Attribute) 

Average value of all store purchases made for each customer 

1. If necessary, click Measures on the left-hand menu. 

2. Click the New button in the top left-hand corner, then Build your own. 

3. Next to the Untitled measure text, select Edit name. 

4. Set the name to Average Store Purchase ($), select Done. 

5. Under the Average Store Purchase calculation, click Select Function and choose Average. 

6. Select Add attribute, expand Purchases : PoS select Total Price, and click Add. 

7. Select the Run button to complete your measure. 

	![Picture 52](Static/Lab_4A_picture52.png)

 

  

## Average Web Purchase (Customer Attribute) 

Average value of all web purchases made for each customer 

1. If necessary, click Measures on the left-hand menu. 

2. Click the New button in the top left-hand corner. 

3. Next to the Untitled measure text, select Edit name. 

4. Set the name to Average Web Purchase ($), select Done. 

5. Under the Average Web Purchase ($) calculation, click Select Function and choose Average. 

6. Select Add attribute, expand Purchases : eCommerce, select Total Price and click Add. 

7. Select the Run button to complete your measure. 

	![Picture 53](Static/Lab_4A_picture53.png)

 

  

# Task 6 - Review the Measures 

 

1. Make sure all your measures have successfully refreshed, then navigate to the Customer Insights Home Page. You should notice that your Business Measures are visible on the home page. 

	![Picture 3924](Static/Lab_4A_image40.jpeg) 

2. Navigate to the Data -> Entities menu area and open the Customer_Measure entity. 

You should be presented with a preview of the Customer Measures you have calculated against the Unified Profile Customer ID. Click on the Data tab to see the results. 

![Picture 55](Static/Lab_4A_picture55.png)

One interesting view to explore is the Summary view for the measures. From the screen above click on the Attributes tab just below the page heading (highlighted above), then click on the Summary chart icon ![Picture 3961](Static/Lab_4A_image41.jpeg) for Total Club Points. You should get a pop-up like this with some useful stats about the measure. 

![Picture 56](Static/Lab_4A_picture56.png)

You are now able to consume these measures to drive action such as Marketing Segments. 

 

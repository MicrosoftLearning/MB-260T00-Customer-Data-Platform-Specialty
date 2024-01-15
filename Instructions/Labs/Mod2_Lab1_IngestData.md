---
lab:
    title: 'Lab 2.1: Ingest data'
    module: 'Module 2: Ingest data into Dynamics 365 Customer Insights - Data'
---

# Lab 2.1: Ingest data
# Module 2: Ingest data into Dynamics 365 Customer Insights - Data

## About the Hands-on Lab

Unlike traditional approaches for realising a 360 degree view of the customer with a large amount of coding involved, Dynamics 365 Customer Insights (CI) is a finished SaaS solution which allows you to adopt an agile project management approach and deliver value in a matter of weeks. 

By attending this Hands-on Lab, you will learn step-by-step how to set up, configure and use Dynamics 365 Customer Insights. To bring this to life, we are looking at a typical customer analytics project for our example company, Contoso Coffee. 

We will introduce the business pain points, goals and high-priority use cases that Contoso has identified around their customer data initiative, and then realise a working prototype solution today. 


## Lab Scenario: Contoso Coffeee
 
Contoso Coffee produce high-quality coffee and coffee machines, which they retail through channels including new Contoso Retail Stores in premium locations, premium food resellers and the Contoso Coffee Web Site. 

Contoso plan to further expand their offerings with Contoso Cafes and a new Connected Coffee Machine which can trigger refill orders and alert Contoso Service about any issues. 

This new offering will help them to build direct relationships with their customers and learn more about how customers consume their products. 


## Business Objective 

Contoso wishes to own and build a meaningful, direct relationship with all consumers to deliver an exceptional, personalised customer experience through relevant communications, personalised recommendations and services.
 

## Challenges 

- **Transactional Relationship:** Their existing business model means that they lack a direct relationship with their customers. 

- **Data Silos:** They are unable to deliver personalised customer experiences. 


## Existing Data Landscape 

- **Fractured Customer Data:** With multiple systems, Contoso has multiple records for the same person. This causes a disjointed experience to the customer who expects to be treated as one person regardless of the channel they are transacting upon. 

- **Multiple Platforms:** The architecture at Contoso has evolved through acquisition and legacy systems meaning that data can reside in not only different systems, but different platforms across multiple clouds and on premise. 

- **Non-Customer Data:** Contoso are drawing correlations between non-customer data and the impact it has on customer experiences, including data from third parties such as weather data. 


## Contoso Coffee Customer Insights Project 

Contoso management is tasking IT and Line of Business teams with the following: 

- Establish a customer data hub combining all customer related data from siloed sources. 

- Realise a unified Contoso Customer profile. 

- Provide a 360-degree view of the customer for service agents (embedded into Dynamics 365 for Customer Service) as well as store managers (through Power BI).

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

4. Configure business and customers measures in Customer Insights to identify customers with higher than average spend in store and online

5. Build sample customer segments for Marketers to deliver personalised and targeted marketing communications 

6. Configure Customer Insights contact cards and embed into Dynamics 365 to empower Contoso Customer Service Advisors 

7. Create Power BI dashboard for Store Managers 

8. Create Greeter App with PowerApps for Contoso Coffee retail staff, empowering them to deliver personalised service 

9. Use Microsoft Power Automate to capture Customer check ins at Contoso retail stores and deliver personalised recommendations to Contoso Retail staff 

10. Demo Customer Insights prototype to group of pilot users and gather feedback 


# Module Introduction

## Lab pre-requisites: 

Before you can start this exercise, you must have completed **Lab 1.1** to set up your environment.


## Data Ingestion & Data Unification.

As Project Manager for Contoso Retail, you will create a unified customer profile by ingesting key sources of customers data and following the Map, Match and Merge process. 

In this lab, we will **ingest data**. In the next lab, we will **unify the data**.


# Approximate Time to Complete - 45 minutes

# Familiarize yourself with Customer Insights - Data

In this task, you will explore the pre-configured Demo environment to familiarize yourself with Customer Insights - Data. 

1.  Sign in to Customer Insights - Data at `https://home.ci.ai.dynamics.com` if you are not already signed in. 

2.  In the **Environment selector** in the top right-hand corner, confirm **Marketing Trial** is selected.

4.  Explore the left-hand menu options to familiarise yourself with the navigation. 

    - **Home**: Home Page 
    - **Customers**: View cards for unified Customer Profiles (you won't be able to view this yet - we need to ingest and unify our data first)
    - **Data > Data sources**: Ingest siloed demographic, transactional of behavioural data. Map, match and merge into a Unified Customer Profile. View your entities and define activity types and their relationships to your customers. 
    - **Data > Enrichment**: Go beyond your unified profile and enrich customer profiles with Microsoft Proprietary Data. Unlock data on affinities for hundreds of brands and dozens of interest-categories. These affinities are extracted for profiles that might be like your customers.
    - **Insights > Segments, Measures & Predictions:** View segments, configure measures, and use out-of-the-box prediction models (or build your own). (You won't be able to view this section yet.)
    - **Settings**: Administer Roles, Permissions, APIs and Export Destinations for Customer Segments. 

# Exercise 1 - Data Ingestion

In this lab you will become familiar with ingesting data from multiple sources. As Project Manager for Contoso Retail, you have already identified that key sources of data include eCommerce Customers, Online Purchases, in-store Point of Sales Purchases, data from Contoso Retail Loyalty Card scheme, Subscription data, Contoso Hotel data and Contacts from your Dynamics 365 CRM. 

Although Customer Insights has connectors to 35+ data sources and applications (including Dynamics 365 & the Microsoft Dataverse), for this lab you will be using the 'Text/CSV' connector. 


## Data Source Model 

Note: Some of this data will be ingested in later labs.

## Task 1 -  Ingest Customer Data from eCommerce Platform 

1.  Sign in to Customer Insights `http://home.ci.ai.dynamics.com` and verify **Marketing Trial** is selected in the drop-down menu in the top right-hand corner. 

2.  In Customer Insights, expand **Data** on the left navigation menu and select **Data sources**. 

3.  Select **+Add a data source**. View the available methods of ingesting data. For this lab, choose **Microsoft Power Query** and name the source `eCommerce`, then select **Next**. 

4.  You will be presented with a view of Power Query data sources that Customer Insights is able to ingest. Take note of the connector types available. Select the **Text/CSV** connector. 

5.  Enter `https://aka.ms/CI-ILT/Contacts` for **File path or URL** and select **Next**. It may take a few moments for the data to upload.

6.  You should now see the data from the source tabulated. Select **Transform data** to configure the datatypes and formats for the data you ingest. 

7.  You will notice that the column heading has appeared in the first row of the data. To correct this, either select **Transform** > **Use first row as headers** from the **Home** tab or select the **Transform** tab and then **Use first row as headers**.

8.  Because we have ingested data from a Text/CSV source, all columns are defaulted to a 'Text' Data Type. To successfully ingest and model the data, we can set the data type for non-text columns. 

    To change the data type, select the **ABC** icon on each column heading. Update the data type for these columns: 

    | Column Heading | New Data Type |
    | -------------- | ------------- |
    | DateOfBirth    | Date          |
    | CreatedOn      | Date          |
    | Income         | Currency      |

9.  Verify the **Name** field on the **Query settings** pane is set to `Contacts`. Select **Next**. Select **Save**. 

    > **Note:**
    >
    > Column names can only contain letters, numbers, and underscores. They cannot contain a space and must begin with a letter. If you have data where column name(s) have a space or do not begin with a letter you will want to fix that either within Power Query or before the data is brought into Customer Insights. 

Congratulations. You have now successfully created your first data source with a data set! 

We'll continue importing the next data set in the next task. 


## Task 2 - Ingest Online Purchase Data 

In this task, we will ingest Online Purchase data, representing purchases made via the Contoso Coffee website. 

1.  In Customer Insights, expand **Data** on the left menu and select **Data sources**. 

2.  Under **Managed by me (1)**, select the **eCommerce** data set and select **Edit**. Select **Next**. 

    > **Note:** If your data is still refreshing, you will need to wait for it to finish before editing. 

3.  Select **Next.** You should be presented with the **Power Query** view of the eCommerce Contacts data that you ingested in Task 1. On the **Home** tab, select **Get data**. 

4.  You will be presented with a view of data source connectors that Customer Insights is able to ingest. Select the **Text/CSV** Connector. 

5.  Enter `https://aka.ms/CI-ILT/OnlinePurchases` for **File path or URL** and select **Next**. Select **Create**. 
 
6.  As before, select **Transform**, then **Use first row as headers**.

7.  Update the **data types** for the following columns: 

	| Column Heading | New Data Type |
	| -------------- | ------------- |
	| PurchasedOn    | Date          |
	| TotalPrice     | Currency      |
 
8.  Name this query `Purchases` and select **Save**. 


## Task 3 - Ingest Customer Data from Loyalty Scheme 

1.  In Customer Insights, expand **Data** on the left menu and select **Data sources**. 

2.  Select **+Add a Data Source** and choose **Microsoft Power Query** as the import method. Name the source `Loyalty`, then select **Next**. 

3.  Select the **Text/CSV** connector. 

4.  Enter `https://aka.ms/CI-ILT/LoyaltySchemeCustomers` for **File path or URL**, select **Next** and then select **Transform data**. 

6.  As before, select **Transform**, then **Use first row as headers**.

7.  Update the data type for these columns: 

	| Column Heading | New Data Type |
	| -------------- | ------------- |
	| DateOfBirth    | Date          |
	| RewardPoints   | Whole number  |
	| CreatedOn      | Date          |

8.  Rename this query to `Customers` in the **Query settings** pane and select **Next**. 

9.  Select **Save**. 


# Task 4 - Ingest Customer Data from Point of Sale Purchases  

1.  In Customer Insights, expand **Data** on the left navigation menu and select **Data sources**. 

2.  Select **+ Add a data source**, choose **Microsoft Power Query** and name the source `PoS`, then select **Next**. 

2.  Select the **Text/CSV** connector. 

3.  Enter `https://aka.ms/CI-ILT/POSPurchases` for **File path or URL**. Select **Next** and then select **Transform data**. 

4.  As before, select **Transform**, then **Use first row as headers**.

5.  Update the **data type** for these columns: 

	| Column Heading    | New Data Type |
	| ----------------- | ------------- |
	| PurchasedOn       | Date          |
	| TotalPrice        | Currency      |
	| RewardPointsAdded | Whole number  |

6.  In the **Name** field on the **Query settings** pane, rename the query to `Purchases`. Select **Next** and select **Save**. 


# Task 5 - Ingest Customer Data from Website Reviews 

1.  In Customer Insights, expand **Data** on the left navigation menu and select **Data sources**. 

2.  Select **+ Add a data source**. Choose **Microsoft Power Query** and name the source `Website`, then select **Next**. 

3.  Select the **Text/CSV** connector. 

4.  Enter `https://aka.ms/CI-ILT/WebReviews` for **File path or URL**. Select **Next** and then select **Transform data**. 

5.  As before, select **Transform**, then **Use first row as headers**.

6.  Update the data type for these columns: 

    | Column Heading | New Data Type |
    | -------------- | ------------- |
    | ReviewRating   | Whole number  |
    | ReviewDate     | Date          |

7.  In the **Name** field on the **Query settings** pane, rename the query to `Reviews`. Select **Next** and select **Save**. 


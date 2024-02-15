---
lab:
    title: 'Lab 5.1: Enrich data'
    module: 'Module 5: Enrich data and predictions with Customer Insights - Data'
---

# Lab 5.1: Enrich data
# Module 5: Enrich data and predictions with Customer Insights - Data

When it comes to enriching your data, you will need to decide on the Brands and Categories that apply to your business. You will be able to find many of the relevant brands and categories in the list from the Microsoft Graph to choose from. In our case we will look for specific coffee companies for our brands, and beverage related categories to enrich our data with. 

Think of enrichment as a way to say, "for all of my customers, show me their likely affinity towards each of these brands and interest in these categories based on the fields I map". Then for each customer we go out and look for all the people in the graph that are similar age, location and/or gender and calculate their brand affinity and interests to enrich your data. 

You can also choose third party applications to enrich your data like Leadspace, Experian etc. but make sure you have right privileges to access. 

For this lab, we will configure enrichment using Microsoft Graph. 

### Task 1 - Adding Brand Affinity 

1.  If you haven't already, sign into Customer Insights - Data at `https://home.ci.ai.dynamics.com`

2.  Navigate to **Data > Enrichment**. 

3.  Select the **Enrich my data** button on the **Brands** tile. On the **Overview** screen, select **Next**. 

4.  Review the list of categories that are presented in the **Select an industry** drop-down. Note that there doesn't appear to be anything specific to our industry, so we will not go this route. We could possibly use **Retail Brands** but that is not specific enough for our use case. 

5.  In the **Enter brand names manually** box, enter and select these brands: 
	
    - `Peet's Coffee` 
    
    - `Blue Bottle Coffee` 
    
    - `Caribou Coffee` 
    
    - `Dunkin Donuts` 
    
    - `Starbucks` 

6.  Select **Next**. 

7.  On the **Enrichment preferences** screen, leave the brand affinity level at **Medium (recommended)** and set the match precision to **Exact and aggregate**.
 
8.  Select **Next**. 

9.  On the **Add customer Data** screen, choose **Profiles** > **Customer** for the **Customer data set**, and select **Next**. 

10. On the **Data mapping** screen, we will choose the fields to map our data with the data from Microsoft Graph. We can map both demographic as well as location information. As a minimum you must map the Country/Region. We will map more attributes to get a more refined result. 

    The system will pre-fill the entries when it can find a likely match. You can overide the entry by selecting the dropdown and choosing a different field. Here are the settings we will use: 
	
    - Date of Birth: **DateOfBirth** 

    - Gender: Gender 

    - Country/Region: Country 

    - ZIP/Postal code: PostCode

    - City: City 

    - State/Province: State 

11. Select **Next** and review the entries. 

12. Name your enrichment `BrandEnrichment`. 

13. Select **Save enrichment** and select **Close**. 


### Task 2 - Adding Interests Affinity 

1.  Navigate to **Data > Enrichment** and select the **Discover** tab. 

2.  Select the **Enrich my data** button on the **Interests** tile. On the **Overview** page, select **Next**. 

3.  In the **Enter interests manually** box, enter and select these interests: 

    - `Bottled Water & Water Delivery` 

    - `Coffee` 

    - `Tea` 

    - `Sports Drinks` 

    - `Alcoholic Beverages` 

4.  Select **Next**. 

5.  On the **Enrichment preferences** screen, leave the brand affinity level at **Medium (recommended)** and set the match precision to **Exact and aggregate**.  

6.  Select **Next**. 

7.  On the **Add customer Data** screen, choose **Customer** from the Profiles section in the dropdown, then select **Next**. 

8.  On the **Data mapping** screen, fill out the following: 

	- Date of Birth: **DateOfBirth** 

	- Gender: Gender 

	- Country/Region: Country 

	- ZIP/Postal Code: PostCode

	- City: City 

	- State/Province: State 

9.  Select **Next** and review the entries. 

10. Name your enrichment `InterestEnrichment`. 

11. Select **Save enrichment** and select **Close**. 

12. Next, we need to run the enrichments we just created. If you are not the **My enrichments** tab on the **Enrichments** page, navigate to **Data > Enrichment** in the left navigation menu, and select the **My enrichments** tab. You should see the two enrichments we just configured. 

13. Select **Run all** in the top menu and let the enrichments run.


### Task 3 - Review the Enriched Data 

Once the enrichment has finished running (it may take several minutes), you can then look at what was created. 

1.  Navigate to **Data > Enrichments** and select the **My enrichments** tab. 

2.  Review the number of profiles enriched in the **Enriched customers** column. 

3.  Now, we'll look at one of the two entities that were created to hold the enrichment data. 

    Navigate to **Data > Tables**, and then under Enrichment, select either the **BrandAffinityFromMicrosoft** or **InterestAffinityFromMicrosoft** entity. This is where the enrichment data is stored. 

    Here you will see the Industry a brand is listed in, the affinity score for a customer profile and affinity confidence as well as other information depending on which fields were mapped. 

    From this view you can also download a CSV of this data to work with offline or in third party business applications. 
 
4.  Now let's look at what we see for a specific customer. Navigate to **Customers** from the left navigation menu and pick a customer (we'll use Joseph Chestnut). When you open the Customer profile details page you will see the enrichment that pertains to 'customers like' that customer. This is based on the fields mapped when the Enrichment was configured, in our case: DateOfBirth, Gender, Geography. 


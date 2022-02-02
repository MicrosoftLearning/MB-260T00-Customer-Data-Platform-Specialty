---
lab:
    title: 'Lab 5.1: Enrich data'
    module: 'Module 5: Enrich data and predictions with Audience insights'
---

# Lab 5.1: Enrich data
# Module 5: Enrich data and predictions with Audience insights

When it comes to enriching your data, you will need to decide on the Brands and Categories that apply to your business. You will be able to find many of the relevant brands and categories in the list from the Microsoft Graph to choose from. In our case we will look for specific coffee companies for our brands, and beverage related categories to enrich our data with. 

Think of enrichment as a way to say, "for all of my customers, show me their likely affinity towards each of these brands and interest in these categories based on the fields I map". Then for each customer we go out and look for all the people in the graph that are similar age, location and/or gender and calculate their brand affinity and interests to enrich your data. 

You can also choose third party applications to enrich your data like Leadspace, Experian etc. but make sure you have right privileges to access. 

For this lab, we will configure enrichment using Microsoft Graph. 

### Task 1 - Adding Brand Affinity 

1. Navigate to **Data > Enrichment.** 

2. Click the **Enrich my data** button on the **Brands** tile. On the Overview page, click **Next.**

3. Select **Choose an industry.** Review the list of categories that are presented in the Industry dropdown. Note that there doesn't appear to be anything specific to our industry, so we will not go this route. We could possibly use Retail Brands but that is simply not specific enough for our use case. 

5. In the "Enter brand names manually" box, enter these brands: 
	- Peet's Coffee 
	- Blue Bottle Coffee 
	- Caribou Coffee 
	- Dunkin Donuts 
	- Starbucks 

6. Click **Next.**

7. On the Enrichment preferences screen, leave the brand affinity level at **Medium** and set the match precision to **Exact and aggregate.**

8. Click **Next.**

9. On the Add customer data screen, choose **Customer** from the Profiles section in the dropdown, then click **Next. **

10. On the Data Mapping screen, we will choose the fields to map our data with the data from the graph. We can map both demographic as well as location information. At a minimum you must map a country/region. We will map more attributes to get a more refined result. 

	The system will pre-fill the entries when it can find a likely match. You can overide the entry by clicking the dropdown and selecting a different field. Here are the settings we will use: 
	
	- Date of Birth: DateOfBirth 

	- Gender: Gender 

	- Country/Region: Country 
	
	- Postal code: PostCode

	- City: City 

	- State/Province: State 

11. Click **Next** and review your entries. 

12. Name your enrichment **BrandEnrichment**. 

13. Click **Save enrichment** and then **Close.**


### Task 2 - Adding Interests Affinity 

1. Navigate to **Data > Enrichment > Discover.**

2. Click the **Enrich my data** button on the **Interests** tile. On the Overview page, click **Next.**

3. In the "Enter interests manually" box, enter these interests: 

	- Bottled Water & Water Delivery 
	- Coffee 
	- Tea 
	- Sports Drinks 
	- Alcoholic Beverages

4. Click **Next.**

5. On the Enrichment preferences screen, leave the brand affinity level at **Medium** and set the match precision to **Exact and aggregate.** 

6. Click **Next.**

7. On the Add data set screen, choose Customer from the Profiles section in the dropdown, then click **Next. **

8. On the Data Mapping screen, fill out the following:

	- Date of Birth: DateOfBirth 

	- Gender: Gender 

	- Country/Region: Country 

	- Postal code: PostCode

	- City: City 

	- State/Province: State 

9. Click **Next** and review your entries. 

10. Name your enrichment **InterestEnrichment**. 

11. Click **Save enrichment** and then **Close.** 

12. Next, we need to run the enrichments we just created. If you are not the My enrichments tab on the Enrichments page, click on **Data > Enrichment** in the left hand menu, then click on the **My enrichments** tab. You should see the two enrichments we just configured. 

13. Click on **Run all** in the top menu and let the enrichments run.

### Task 3 - Review the Enriched Data 

Once the enrichment has finished running (it may take a few minutes), you can then look at what was created. 

1. The first thing you will see is the number of profiles that were enriched with data. 

2. Now, we'll look at one of the two entities that were created to hold the enrichment data. 

Click on **Data > Entities**, and then under Enrichment, click on either the BrandAffinityFromMicrosoft or InterestAffinityFromMicrosoft entity. This is where we store the enrichment data. 

Here you will see the IndustryVertical a brand is listed in, the affinity score for a customer profile and affinity confidence as well as other information depending on which fields you mapped. 

From this view you can also download a CSV of the data to work with offline. 
 
3. Now let's look at what we see for a specific customer. On the Customer page pick a customer (we'll use Joseph Chestnut). When you view the customer detail page you will see the enrichment that pertains to 'people like' that customer. This is based on the fields you chose to map when you configured the Enrichment, in our case: DateOfBirth, Gender, Geography. 

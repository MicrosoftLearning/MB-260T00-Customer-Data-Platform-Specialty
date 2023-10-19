---
lab:
    title: 'Lab 4.2: Define measures'
    module: 'Module 4: Work with Dynamics 365 Customer Insights - Data'
---

# Lab 4.2: Define measures
# Module 4: Work with Dynamics 365 Customer Insights - Data

Measures enable you to define all the key performance indicators (KPIs) that best reflect your specific business performance and health. Measures can either be customer-related measures, such as Lifetime Value, or business-health measures, such as Monthly Active Users. 

Customer Insights provides an intuitive experience to build different types of measures, with a query-builder wizard that doesn't require the user to manually code or validate the query. 

Measures are calculated on a series of interactions that a company has with a customer, gathered from multiple data sources. Interactions are any customer touch points - these could include purchases, customer service cases, emails, phone calls, branch visits. In other scenarios interactions could also be data gathered from connected devices, withdrawals, or deposits in banking, entry/exist of a premises or area, etc. 

Contoso Coffee are looking to uncover six simple Measures based on the data ingested, that will help them to identify high-value customers and their preferred purchase method (Online or Instore).

### Business Measures: 

- Average Store Purchase Value ($) 

- Average Web Purchase Value ($) 

### Customer Measures:

- Total Online Spend

- Total In-Store Spend

### Customer attributes: 

- Lifetime Spend ($) 

- Total Club Points 

- Average Store Purchase ($) 

- Average Web Purchase ($) 


## Task 1 - Define Two Business Measures 

Business Measures helps you track your business performance and health. The business has asked you to calculate the Average Store Purchase and Average Web Purchase values for the Contoso Coffee business. 


### Average Store Purchase Value (Business Measure) 

In this first task, we will create a measure to define the **average value of all in store purchases** made at Contoso Coffee. 

1.  If you haven't already, sign into Customer Insights at https://home.ci.ai.dynamics.com/. 

2.  Select **Measures** from the left navigation menu. 

3.  Select **+ New** from the toolbar, then select **Build your own**. 

4.  Next to the "Untitled measure" text, select **Edit details**. 
 
5.  Set the **Name** to `Average Store Purchase Value ($)` and select **Done**. 

6.  Toggle **Measure type** to **Business level**. 

8.  Next to **Calculation 1**, select **Edit name**. 

9.  Set the **Name** to `Average Store Purchase Value ($)`. 

10. Verify the **Output attribute name** is set to **AverageStorePurchaseValue**. 

11. Select **Done**. 

12. Under the **Average Store Purchase Value ($)** calculation, choose **Average** from the **Select function** drop-down. 

13. Select **+ Add attribute**, expand **Purchases : PoS**, and select **TotalPrice**. 

14. Select **Add**. 

15. Select the **Run** button to complete your measure. 


### Average Web Purchase Value (Business Measure) 

In this next task, we will create a measure to define the **Average value of all web purchases** made at Contoso Coffee.

1. Select **Measures** from the left navigation menu. 

2. Select **+ New > Build your own** from the toolbar. 

3. Next to the **Untitled measure** text, select **Edit name**. 

4. Set the name to `Average Web Purchase Value ($)` and select **Done**. 

5. Toggle **Measure type** to **Business level**. 

8. Next to **Calculation 1**, select **Edit name**. 

8. Set the **Name** to `Average Web Purchase Value ($)`.

9. Verify the **Output attribute name** is set to **AverageWebPurchaseValue**. 

10. Select **Done**.

11. Under the **Average Web Purchase Value ($)** calculation, choose **Average** from the **Select function** drop-down. 

12. Select **+ Add attribute**, expand **Purchases : eCommerce**, and select **TotalPrice**. 
 
13. Select **Add**. 

14. Select the **Run** button to complete your measure. 


## Task 2 - Define Customer Measures  

We will need two customer measures that can be used to calculate a customer attribute. We will create one measure to determine the customers total spend on Online Purchases and one measure to determine their total spend on In-Store purchases. Once we create these, we can then create a customer attribute to add those two together. 

### Total In-Store Spend (Customer Measure)  

In this task, we will create a measure to define **Total of all purchases made in-store.** 

1.  Sign into Customer Insights at https://home.ci.ai.dynamics.com/. 

2.  Select **Measures** from the left navigation menu. 

3.  Select **+ New > Build your own** from the toolbar. 

4.  Next to the title **Untitled measure** text, select **Edit details**. 

5.  Set the **Name** to `Total In-Store Spend` and select **Done**. 

6.  Under the **Total In-Store Spend** calculation, choose **Sum** from the **Select function** drop-down. 

7.  Select **+ Add attribute**, expand **Purchases : POS**, select **TotalPrice**, and select **Add**. 

8.  To set up the measure calculation, select **Dimensions (1)**.

9.  Select **Edit Dimensions**. 

10. Expand **Purchases: PoS**, select **LoyaltyId**, and select **Done**. 

11. Select **Apply**. 

12. Select the **Run** button to complete your measure. 

13. If you encounter an error and need to choose the **Relationship path**, select **PoS_Purchases > Customer** and select the **Run** button to complete.


## Total Online Spend (Customer Measure)  

Next, we will create a measure to define **Total of all purchases made online.**

1.  Select **Measures** on the left navigation menu. 

2.  Select **+ New > Build your own** from the toolbar. 

3.  Next to the title **Untitled measure** text, select **Edit details**. 

4.  Set the name to `Total Online Spend`, select **Done**. 

5.  Under the **Total Online Spend** calculation, choose **Sum** from the **Select function** drop-down. 

6.  Select **+ Add attribute**, expand **Purchases : eCommerce**, select **TotalPrice** and click **Add**. 

7.  Under **Set up your measure calculations**, select **Dimensions (1)**. 

8.  Select **Edit dimensions**.  

9.  Expand **Purchases : eCommerce**, select **ContactId**, and select **Done**. 

10. Select **Apply**. 

11. Select the **Run** button to complete your measure. 

12. If you encounter an error and need to choose your relationship path, select **eCommerce_Purchases > Customer**. 


## Task 3 - Define Customer Attributes 

Customer Attributes are a single field per customer that reflects a score, value, or state for each customer. Examples are Lifetime Value and Total Sales. 

In this task you will create measures to calculate the Lifetime Spend ($), Total Club Points, Average Web Purchase Value ($) and Average Store Purchase Value ($) of each customer. By calculating value for the business and customers, Contoso Coffee can identify customers with a higher than average spend on each channel. 

### Total Club Points (Customer Attribute) 

First, we will define **Total Loyalty Points earned by each customer**. 

1. If necessary, select **Measures** from the left navigation menu. 

2. Select **+ New > Build your own** from the toolbar.  

3. Next to the title **Untitled measure** text, select **Edit details**.

4. Set the name to `Total Club Points` and select **Done**. 

5. Under the **Total Club Points** calculation, choose **Sum** from the **Select function** drop-down. 

6. Select **+ Add attribute**, expand **Purchases : POS**, select **RewardPointsAdded** and select **Add**. 

7. Select the **Run** button to complete your measure. 

8. If you encounter an error and need to choose your relationship path, select **PoS_Purchases > Customer**. 


## Lifetime Spend (Customer Attribute)  

Next, we will define **Total value of all purchases made for each customer.** 

1.  If necessary, select **Measures** from the left navigation menu. 

2.  Select **+ New > Build your own** from the toolbar.  

3.  Next to the title **Untitled measure** text, select **Edit details**.

4.  Set the name to `Lifetime Spend ($)` and select **Done**. 

5.  Under the **Lifetime Spend ($)** calculation, choose **Sum** from the **Select function** drop-down. 

6.  Select **+ Add attribute**.  

7.  Select the **Measures** tab, expand **TotalInStoreSpend : CustomerInsights**, select **Calculation 1**, and select **Add.** 

8.  Select the **+** (Plus sign) to add a plus sign after the attribute you just added. The plus sign should appear in the calculation formula. 

9.  Select **Add attribute**. 

10. Select the **Measures** tab, expand **TotalOnlineSpend : CustomerInsights**, select **Calculation 1**, and select **Add**.  

11. Select the **Run** button to complete your measure. 


## Average Store Purchase (Customer Attribute) 

Next, we will define the **average value of all store purchases made for each customer.** 

1.  If necessary, select **Measures** from the left navigation menu. 

2.  Select **+ New > Build your own** from the toolbar.  

3.  Next to the title **Untitled measure** text, select **Edit details**. 

4.  Set the name to `Average Store Purchase ($)` and select **Done**. 

5.  Under the **Average Store Purchase ($)** calculation, choose **Average** from the **Select function** drop-down. 

6.  Select **+ Add attribute**, expand **Purchases : PoS**, select **Total Price**, and select **Add**. 

7.  Select **Relationship path**, and select **PoS_Purchases > Customer**. Select **Done**. 

8.  Select the **Run** button to complete the measure. 


## Average Web Purchase (Customer Attribute) 

Next, we will define **Average value of all web purchases made for each customer**.

1.  If necessary, select **Measures** from the left navigation menu. 

2.  Select **+ New > Build your own** from the toolbar.  

3.  Next to the title **Untitled measure** text, select **Edit details**. 

4.  Set the name to `Average Web Purchase ($)` and select **Done**. 

5.  Under the **Average Web Purchase ($)** calculation, choose **Average** from the **Select function** drop-down. 

6.  Select **+ Add attribute**, expand **Purchases : eCommerce**, select **Total Price** and select **Add**. 

7.  Select **Relationship path**, and select **eCommerce_Purchases > Customer**. Select **Done**. 

8.  Select the **Run** button to complete your measure. 


# Task 4 - Review the Measures 

1. Make sure all your measures have successfully refreshed, then navigate to the Customer Insights home page. You should notice that the new **Business Measures** are shown under **Recent business measures**.  

2. Navigate to **Data > Entities** and open the **Customer_Measure** entity. You should be presented with a preview of the Customer Measures you have calculated against the Unified Profile Customer ID. Select the **Data** tab to see the results. 

3. One interesting view to explore is the **Summary view** for each measure. From the screen above select the **Attributes** tab, then select the **Overview** chart icon for Total Club Points shown in the **Summary** column. You should get an **Overview** pop-up showing some useful statistics about the measure. 

You are now able to consume these measures to drive action such as **Marketing Segments**. 
 

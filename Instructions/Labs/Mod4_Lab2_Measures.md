---
lab:
    title: 'Lab 4.2: Define measures'
    module: 'Module 4: Work with Dynamics 365 Customer Insights'
---

# Lab 4.2: Define measures
# Module 4: Work with Dynamics 365 Customer Insights

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

1. Click **Measures** on the left-hand menu. 

2. Click the **+ New** button in the top left-hand corner, then select **Build your own.**

3. Next to the "Untitled measure" text, select **Edit name.** 
 
4. Set the name to "Average Store Purchase Value ($)" and select Done. 

5. Under **Set up your measure calculations**, select **Dimensions (1). **

6. Delete Customer: CustomerInsights.CustomerId and select **Apply.** (By deleting the customer dimension, this changes the measure from a customer measure to a business measure.)

7. Next to Calculation 1, click **Edit name.**

8. Set the Display name to "Average Store Purchase Value ($)."

9. Verify the Attribute name is set to "AverageStorePurchaseValue."

10. Select Done. 

11. Under the Average Store Purchase Value ($) calculation, click **Select Function** and choose **Average.**

12. Select **Add attribute**, expand **Purchases : PoS**, and select **TotalPrice.**

14. Select **Add.** 

14. Select the **Run** button to complete your measure. 

### Average Web Purchase Value (Business Measure) 

In this next task, we will create a measure to define the **Average value of all web purchases** made at Contoso Coffee.

1. Click **Measures** on the left-hand menu. 

2. Click the **+ New** button in the top left-hand corner, then **Build your own.** 

3. Next to the **Untitled measure** text, select **Edit name**.

4. Set the name to "Average Web Purchase Value ($)" and select **Done.** 

5. Under **Set up your measure calculations**, select Dimensions (1).

6. Delete **Customer: CustomerInsights.CustomerId** and select **Apply.** (By deleting the customer dimension, this changes the measure from a customer measure to a business measure.)

8. Next to Calculation 1, click **Edit name.**

8. Set the **Display name** to "Average Web Purchase Value ($)".

9. Verify the **Attribute name** is set to "AverageWebPurchaseValue". 

10. Select **Done.**

11. Under the Average Web Purchase Value ($) calculation, click Select **Function** and choose **Average.**

12. Select **Add attribute**, expand Purchases : eCommerce, and select **TotalPrice.**
 
13. Select **Add.** 

14. Select the **Run button** to complete your measure. 

## Task 2 - Define Customer Measures  
We will need two customer measures that can be used to calculate a customer attribute. We will create one measure to determine the customers total spend on Online Purchases and one measure to determine their total spend on In-Store purchases. Once we create these, we can then create a customer attribute to add those two together. 

### Total In-Store Spend (Customer Measure)  

In this task, we will create a measure to define **Total of all purchases made in-store.** 

1. If necessary, click **Measures** on the left-hand menu. 

2. Click the **+ New** button in the top left-hand corner, then select **Build your own.**

3. Next to the **Untitled measure** text, select **Edit name.**

4. Set the name to **Total In-Store Spend** and then select **Done.**

5. Under the Total In-Store Spend calculation, click **Select Function** and choose **Sum.** 

6. Select **Add attribute**, expand **Purchases : POS**, select **TotalPrice**, and click **Add.** 

7. Under "Set up your measure calculations", select Dimensions (1).

8. Select **Edit Dimensions.** 

9. Expand **Purchases: PoS**, select **LoyaltyID**, and click **Done.**

10. Click **Apply.** 

11. Select the **Run** button to complete your measure. 

12. If you encounter an error and need to choose your relationship path, select **PoS_Purchases > Customer.**

## Total Online Spend (Customer Measure)  

Next, we will create a measure to define **Total of all purchases made online.**

1. If necessary, click **Measures** on the left-hand menu. 

2. Click the **+ New** button in the top left-hand corner, then **Build your own.**

3. Next to the "Untitled measure" text, select **Edit name.** 

4. Set the name to "Total Online Spend", select **Done.**

5. Under the Total Online Spend calculation, click **Select Function** and choose **Sum.** 

6. Select Add attribute, expand Purchases: eCommerce, select **TotalPrice** and click **Add.** 

7. Under Set up your measure calculations, select Dimensions (1). 

8. Select **Edit dimensions.** 

9. Expand **Purchases: eCommerce**, select **ContactId**, and click **Done.** 

10. Click **Apply.** 

11. Select the **Run** button to complete your measure. 

12. If you encounter an error and need to choose your relationship path, select **eCommerce_Purchases > Customer.**

## Task 3 - Define Customer Attributes 
Customer Attributes are a single field per customer that reflects a score, value, or state for each customer. Examples are Lifetime Value and Total Sales. 

In this task you will create measures to calculate the Lifetime Spend ($), Total Club Points, Average Web Purchase Value ($) and Average Store Purchase Value ($) of each customer. By calculating value for the business and customers, Contoso Coffee can identify customers with a higher than average spend on each channel. 

### Total Club Points (Customer Attribute) 

First, we will define **Total Loyalty Points earned by each customer.** 

1. If necessary, click **Measures** on the left-hand menu. 

2. Click the **+ New** button in the top left-hand corner, then select **Build your own.** 

3. Next to the Untitled measure text, select **Edit name.**

4. Set the name to "Total Club Points" and then select **Done.** 

5. Under the Total Club Points calculation, click **Select Function** and choose **Sum.** 

6. Select **Add attribute**, expand Purchases : POS, select **RewardPointsAdded** and click **Add.** 

7. Select the **Run** button to complete your measure. 

8. If you encounter an error and need to choose your relationship path, select **PoS_Purchases > Customer.**

## Lifetime Spend (Customer Attribute)  

Next, we will define **Total value of all purchases made for each customer.** 

1. If necessary, click **Measures** on the left-hand menu. 

2. Click the **+ New** button in the top left-hand corner, then **Build your own.** 

3. Next to the Untitled measure text, select **Edit name.**

4. Set the name to "Lifetime Spend ($)" and then select **Done.**

5. Under the Lifetime Spend ($) calculation, click **Select function** and choose **Sum.** 

6. Select **Add attribute.** 

7. Select **Measures**, expand **TotalInStoreSpend : CustomerInsights**, select **Calculation 1**, and select **Add.** 

8. Select the **+** (plus sign) to add a plus sign after the attribute you just added. The plus sign should appear in the calculation formula.

9. Select **Add attribute.** 

10. Select **Measures**, expand **TotalOnlineSpend : CustomerInsights**, select **Calculation 1**, and select **Add.** 

11. Select the **Run** button to complete your measure. 

## Average Store Purchase (Customer Attribute) 

Next, we will define the **average value of all store purchases made for each customer.** 

1. If necessary, click **Measures** on the left-hand menu. 

2. Click the **+ New** button in the top left-hand corner, then **Build your own.** 

3. Next to the **Untitled measure** text, select **Edit name.** 

4. Set the name to "Average Store Purchase ($)" and then select **Done.**

5. Under the Average Store Purchase calculation, click **Select Function** and choose **Average.**

6. Select **Add attribute**, expand Purchases : PoS, select **Total Price**, and click **Add.** 

7. Select the **Run** button to complete your measure. 

## Average Web Purchase (Customer Attribute) 

Next, we will define **Average value of all web purchases made for each customer.**

1. If necessary, click **Measures** on the left-hand menu. 

2. Click the **+ New** button in the top left-hand corner and select **Build your own.**

3. Next to the Untitled measure text, select **Edit name.** 

4. Set the name to "Average Web Purchase ($)" and then select **Done.**

5. Under the Average Web Purchase ($) calculation, click **Select Function** and choose **Average.** 

6. Select **Add attribute**, expand Purchases : eCommerce, select **Total Price** and click **Add**. 

7. Select the **Run** button to complete your measure. 

# Task 4 - Review the Measures 

1. Make sure all your measures have successfully refreshed, then navigate to the Customer Insights Home Page. You should notice that your Business Measures are visible on the home page. 

2. Navigate to the **Data > Entities** menu area and open the **Customer_Measure** entity. You should be presented with a preview of the Customer Measures you have calculated against the Unified Profile Customer ID. Click on the Data tab to see the results. 

3. One interesting view to explore is the Summary view for the measures. From the screen above click on the Attributes tab just below the page heading, then click on the Summary chart icon for Total Club Points. You should get a pop-up with some useful stats about the measure. 

You are now able to consume these measures to drive action such as Marketing Segments. 

 

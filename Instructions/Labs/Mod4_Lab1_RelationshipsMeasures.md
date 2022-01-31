---
lab:
    title: 'Lab 4.1: Relationships'
    module: 'Module 4: Work with Dynamics 365 Audience insights'
---

# Lab 4.1: Relationships
# Module 4: Work with Dynamics 365 Audience insights

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

 

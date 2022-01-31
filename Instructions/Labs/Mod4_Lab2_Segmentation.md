# Module Introduction

## Segmentation 

You will create marketing segments to promote Contoso Coffee's new Cold Brew Coffee offering as well as to identify customers with a higher-than-average online spend whom Contoso wish to target with their new subscription and connected coffee machine services. 

These segments will allow Contoso Coffee Marketing to deliver personalised, targeted marketing journeys for upcoming product launch. 

 

## Customer Search and Cards 

You will use the Customers section of Customer Insights to review the unified customer profiles. After defining the fields to be indexed you will search for customers and will review the information shown about each unified customer profile. 

 

## Activities 

Activities provide a way for you to track very specific"tasks" that people are performing. 

 

## Data Enrichment 

Enrich your customer profiles with brands and interest affinities with the help of Microsoft Graph or any third-party application. 

 

## Objectives 

- Generate Segments for use by Marketing 

- Setup search and indexing for customers 

- Configure Activities within Customer Insights 

- Setup Data Enrichment 

 

## Prerequisites 

To complete the Customer Insights lab, you will need the following 

- Dynamics 365 Marketing Instance or Trial 

- Access to Power Apps or a Power Apps Trial 

- Access to Power Automate or a Power Automate Trial 

- Access to Power BI or a Power BI Trial 

- Microsoft Azure Trial 

- Customer Insights Trial 

If you do not have access to the above, you can follow Lab 3 to get setup. 

 

## Approximate Time to Complete - 90 mins 

    
## Exercise 1 - Segmentation

Segments enable you to group your customers into cohorts based on demographic, transactional, or behavioural customer attributes. Using segmentation, you can achieve more targeted actions such as promotional campaigns, sales activities, or customer support actions to achieve desired business goals. You can define complex filters around the Customer Profile entity and its graph of related entities. Each segment, after processing, outputs a set of customer entity records that you can export and take actions upon. 

Segments can be static (defined at the point you activate them) or Dynamic. If you create a Dynamic segment, customers will drop in and out of the segment as they meet or no longer meet the criteria you define. 

Using Customer Insights, Segments can be exported to Dynamics 365 Marketing or several other business applications and used to execute a targeted Customer Journey. Segments can also be exported to .csv or accessed via API. 

Customer Insights also provides insights over the created segments. Using Segment insights, you can find what differentiates two segments or what they have in common. Segment overlap shows which customers are common among the segments. Segment differentiators helps you find what differentiates a segment from the rest of your customers or the other segments. With both of these insights you can compare the segments against attributes and measures. 

In this lab you will segment your unified customer profiles, to uncover cohorts of customers with similar attributes. There are two ways to create segments. First you can create them manually using the New -> Blank Segment button on the top left of the screen after clicking on Segments in the left-hand menu. However, there is a new way using one of the Create from options on that page. We will do it all the ways. At the end, we will review each segment and apply insights over them to discover additional information. 

 

  

### Task 1 - Segment using Profiles: Customers from California 

 

1. Let's create a segment called Customers from California quickly using the profiles. 

 

2. Click on Segments in the left menu 

 

3. Click the New dropdown and select Create From -> Profiles 
![Picture 1](Static/Lab_4B_Picture1.png)
 

4. Select the Field -> State and Value -> California 

 

5. Click Review 

 

6. Name your segment Customers From California and set the output entity name to 

CustomersFromCalifornia 

 ![Picture 376](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image1.jpeg) 

7. Click Save 

### Task 2 - Segment using Measures: High Value Online Customers 

 

Contoso Coffee Marketing wants to run a new promotion to convert customers to subscription model. Marketing have identified that they wish to target brew-at-home customers with a higher than average online purchase value to do so. We will create this segment using the Quick Create. 

1. Click on Segments in the left menu 

 

2. Click the New dropdown and select Create From -> Measures 

	![Picture 2](Static/Lab_4B_Picture2.png)
 

3. Select the Average Web Purchase ($) attribute 

 

4. Set the operator to Greater Than 

 

5. Set the value to 138. You should have a new quick segment screen like this: 

	![Picture 3](Static/Lab_4B_Picture3.png)
 

6. Click Review 

 

7. Name your segment High Value Online Customers and set the output entity name to HighValueOnlineCustomers 

     ![Picture 483](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image2.jpeg) 

8. Click Save 

 

 

  

### Task 3 - Segment from scratch: Summer Promo 

 

Contoso Coffee Marketing want to run a new Summer Promotion targeting millennials with a higher than average in-store purchase with their newly launched Cold Brew Coffee. We will create this segment manually. 

1. Click on Segments in the left menu and Click on + New and select Blank segment. 



2. Set Type to Dynamic, Name to Summer Promotion, Output entity name to 

SummerPromo and click Next 



3. Select Customer_Measure : Customer Insights in the Group 1: Define filter 



4. Set the fields to Average Store Purchase ($), greater than or equal to and 113 

   ![Picture 597](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image3.jpeg) 

   Note: 113 is the average In-store purchase we calculated earlier. 



5. Click + AND then add Customer : CustomerInsights, DateOfBirth, greater than or equal to 1/1/1981 



6. Click + AND then set to DateOfBirth less than or equal to 12/31/1996 



7. Click + And then select All Records 

   ![Picture 599](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image4.jpeg) 

8. Click Save and then click Activate 

 

 

### Task 4 - Review Segments 

 

1. Wait for all your segments to successfully run then Navigate to the Customer Insights Home Page. You should see your segments displayed. Note: Your numbers may be slightly different if the underlying data has changed since the creation of this document. 

	![Picture 4](Static/Lab_4B_Picture4.png)
 

 

2. Click on one of your segments. You should see that you’re presented with a preview of the customers included within your segment, as well a timeline highlighting the segment size. This will display increases and decreases in the number of segment members as data changes over time and the segment is rerun. 

	![Picture 5](Static/Lab_4B_Picture5.png) 

 

3. Now that you have created your segments you are ready to start acting upon your data. You can select the segment and click Download on the top for use in 3rd party software, or you can setup an Export Destination. Segments created within Customer Insights can be made available to other parts of the PowerPlatform, Dynamics 365 Marketing or external applications. 

 

To do this you would go under Admin -> Export Destinations in the left side menu. Here you can setup and Export destination for Dynamics 365 for Sales, Dynamics 365 for Marketing, Azure Blob Storage and several business applications or tools allowing you to use the segments to execute a Marketing Campaign. We will work through this in a different module. 

 

    


### Task 5 - Apply Segment Insights 

 

Let's try to find out common customers that belong to both Customers from California and High Value Online Customers segments and also what differentiates both of these segments in terms of Reward points and LifetimeSpend. 

1. Click on Segments in the left menu, click on Insights tab and click on New on the top. 

 

2. You will now see two options as below: 

	![Picture 6](Static/Lab_4B_Picture6.png) 
 

3. Let's create using Differentiators first to see what distinguishes both of these segments. Click on Differentiators. 

 

4. Choose High Value Online Customers as primary segment and hit Next and choose Customers from California as another segment and hit Next. 

 

5. Now choose Reward points under Attributes and LifetimeSpend under Measures to see how the above segments differ from each other with respect to Reward points and LifetimeSpend. 

 

6. Click Next and name your insight High Value Online vs Customers from California with an Output entity name of HighValueOnlinevsCustomersfromCalifornia and click Save. 

 

  

7. After the run is successful, you can click on the created insight to see a screen like below. Click on the Attributes or Measures tabs to see how the segments differ from each other with respect to them. Observe the Difference score which signifies the degree of difference. The higher the score the more different they are. You may need to refresh the browser window to see the results. 

	![Picture 7](Static/Lab_4B_Picture7.png) 

8. Click on each measure and attribute to see deeper insights like below 

    ![Picture 8](Static/Lab_4B_Picture8.png) 

9. We have successfully created segment insights using Differentiators. Now let’s create using Overlap 

10. Make sure you are still in Insights tab and click on New on the top left and now choose Overlap. 

11. Select both High Value Online Customers and Customers from California segments to find out their shared customers. 

12. Click Next. 

13. Here as an optional step, you can also choose attributes to compare the segments just as we did with the Differentiators. You can simply hit Next without choosing anything. 

14. Name your insight as High Value Online Overlapped with California Customers and set the Output entity name as HighValueOnlineOverlappedwithCaliforniaCustomers then click Save. 

15. After the run is successful, you can click on the created insight to see the screen like below detailing the total and percentage of shared customers between the two segments. 

     ![Picture 928](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image5.jpeg) 

  

### Task 6 - Segment Expansion 

 

Segment Expansion can be used to find similar customers to your segment customer base using Artificial Intelligence. 

Earlier we created a segment called Summer Promotion which has millennial customers with higher than average instore purchase. Now, let us expand that segment and find customers that are similar to them for us to market our newly launched Cold Brew Coffee. 

1. Click on Segments on the left menu and choose the Summer Promotion segment. It becomes our source segment. 

2. Click on the three dots and choose Find similar customers. 

	![Picture 9](Static/Lab_4B_Picture9.png) 

3. Name your segment Summer Promotion Expansion 

4. Click on Add fields in the next step to select attributes and measures that are used to find similar customers. We'll target customers with similar average instore purchase and location. So, we will choose PostCode and AverageStorePurchase and click Apply. 

	![Picture 10](Static/Lab_4B_Picture10.png) 

5. Next you must choose who to consider, either all customers except from source segment or customers from a different segment. If different segment is selected, then we must choose which segment it is. For now, select All customers except source segment. 

6. Now the maximum number of customers to include must be selected. By default, 20% of the customers is selected which can be altered. Let us stick with 20%. 

7. If you like to include members from source segment as well then check the note at the bottom else leave it unchecked. 

8. Hit Run. 

	![Picture 11](Static/Lab_4B_Picture11.png) 
 

 

9. After the run, you can see a new segment being created and click on it to find the similarity scores which range from 0.55 to 1(0.85-1 -> Very similar, 0.7-0.85 -> Similar, 0.55-0.7 -> Somewhat similar) and check the similar customer records. 

	![Picture 12](Static/Lab_4B_Picture12.png) 
	![Picture 13](Static/Lab_4B_Picture13.png)

 

 

    

## Optional - Suggested Segments 

 

Use Suggested Segments to discover interesting segments based on a customer attribute or measure of interest 

### Discover interesting segments based on a numeric customer attribute or measure of interest  

 

1. Under the Segments section, click on the Suggestions (preview) tab. 

	![Picture 14](Static/Lab_4B_Picture14.png) 
 

2. Click on Get Suggestions to begin the configuration experience. 

 

3. We will choose Improve a measure/metric 

 

4. Next, you need to select the target attribute i.e., a customer attribute or measure of interest, for which you want to discover segment suggestions. We will select the previously created measure LifetimeSpend as the target attribute. 

 

5. Next, you will select the attributes that might influence the target attribute (LifetimeSpend) so that the AI model can find interesting patterns between the influencing attributes and the target attribute and suggest segments based on those patterns. We will select Email Subscriber, Income, Loyalty Tier, Occupation and State as the influencing attributes. 

 

   Note: In case you do not know which attributes to select, it is advised to select many attributes so that the model can analyze, and surface segment suggestions based on the underlying patterns it uncovers. However, if you want to see how certain attributes influence "LifetimeSpend", you can choose only those as well. 

 

6. Click on Run. The AI model will start finding patterns between the selected influencing attributes and the target attribute to surface segment suggestions. Please wait for a few minutes for the model to finish its analysis. 

 

7. Once the model has finished running and if it is able to uncover patterns between the influencing attributes and the target attribute, segment suggestions will be displayed under the Suggestions (preview) tab. 

 

	![Picture 1219](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image6.jpeg) 

    Since we've chosen a numeric attribute as the target attribute, segment suggestions include those where the average value of the chosen target attribute (LifetimeSpend) is significantly higher or lower that the average LifetimeSpend value across all customers. We will also explore a scenario where a categorical attribute (Eg - Customer Satisfaction: low/medium/high) is chosen as the target attribute in the next task. 

 

   Each segment suggestion card denotes how the average LifetimeSpend in that segment compares to the overall average. The number of customers in the suggestion as well as the rules learned (i.e. common traits of customers in the segment) are also highlighted. 

   ![Picture 1221](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image7.jpeg) 

   E.g. - in the above suggestion, LifetimeSpend is 20% above average i.e. the customers in this segment have historically spent much more as compared to others. There are 585 members in this segment and they have Income > 97k and a high Loyalty Tier. 

 

8. You can click on any suggestion to see more details in the side panel. We will click on the See suggestion link for the suggestion that says LifetimeSpend is 15% below average. In the side panel, you will see the following: 

	![Picture 1298](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image8.jpeg) 

	- Comparison of average LifetimeSpend of customers in this segment compared to all the customers 

	- Number of customers in the segment and its proportion as compared to the entire customer base 

	- The attribute values i.e., the rules that the model learned based on the selected influencing attributes. 

 

	In this case, customers in this segment have an average 

	LifetimeSpend of 741.89 as compared to average 

	LifetimeSpend of 869.74 across all customers. There are 599 members in this segment which is 12% of the entire customer base. These customers are not Email Subscribers, have an income less than 44k, do not belong to the high loyalty tier and are teachers. This information can then be used to target customers in this segment with personalized messaging to drive more revenue and corresponding business goals. 

 

	In a similar fashion, you can see details of other segment suggestions that you are interested in. 

 

9. You can then save the segment by clicking on Save as segment in the side panel. Name the segment and Output entity name as follows and click on Save. 

	![Picture 15](Static/Lab_4B_Picture15.png) 

 

 

  

10. The saved segment can then be viewed under the All segments tab and it can be used for downstream processes like any other dynamic segment. If you wish to look at the rules that the model learned after saving a segment, you can do so by clicking on Edit in the All segments tab. 

	![Picture 1371](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image9.jpeg) 

 

11. We have successfully found segment suggestions based on a measure of interest (LifetimeSpend). We also saved a segment which can then be utilized for downstream processes like any other dynamic segment. 

 

### Discover interesting segments based on a categorical customer attribute or measure of interest 

 

1. Under the Suggestions tab, click on Find new suggestions in the top menu to explore segment suggestions based on a different customer attribute or measure. Note that, this will replace the existing set of suggestions. 

 

2. We again will choose Improve a measure/metric 

 

3. Select CustomerSatisfaction as the target attribute of interest. Customer Satisfaction is a categorical attribute with 3 categories (low/medium/high) and we’d like to find segment suggestions based on this attribute. Then click Next. 

	![Picture 1373](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image10.jpeg) 

4. Next, select Email Subscriber, Income, Loyalty Tier, Occupation, RewardsPoints and State as the influencing attributes. 

	![Picture 1424](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image11.jpeg) 

5. Click on Run. The AI model will start finding patterns between the selected influencing attributes and the target attribute to surface segment suggestions. Please wait for a few minutes for the model to finish its analysis. 

 

6. Once the model has finished running, segment suggestions will be displayed under the Suggestions (preview) tab. 

	![Picture 1426](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image12.jpeg) 

 

	Since the target attribute is categorical, the AI model tries to find patterns/common traits of customers belonging to a particular category of the target attribute and surfaces segment suggestions. Since Customer Satisfaction has 3 different categories - low, medium and high - the AI model will try to find segments of customers that possess the same traits and a significant portion of them belong to a particular category (i.e. either low, medium or high). 

 

	Note: While only a few tiles are shown initially, you can click the See More link to see more suggestions that were found. 

	![Picture 16](Static/Lab_4B_Picture16.png) 

7. You can click on any suggestion to see segment details in the side panel. We will click on the suggestion that says 83% of customers in this suggestion have CustomerSatisfaction = low. In the side panel, you will see the following: 

 
	![Picture 1510](Static/Lab_4B_Segments,_Customer_Cards,_Activities,_Enrichment_image13.jpeg)

	- Comparison of percentage of customers in this segment that have CustomerSatisfaction = Low as compared to percentage of all customers that have CustomerSatisfaction = Low 

	- Number of customers in the segment and its proportion as compared to the entire customer base 

	- The attribute values i.e. the rules that the model learned based on the selected influencing attributes. 

 

	In this case, 83% of customers in this segment have CustomerSatisfaction = low as compared to 26% among all customers. There are 488 members in this segment which is 10% of the entire customer base. These customers are live in California, do not belong to the high loyalty tier, are not Teachers and do not live in Florida. This helps provide insight that 94% of customers having the above-mentioned traits have a low customer satisfaction. This information can then be used to target customers in this segment with personalized messaging and/or customer service to help improve their customer satisfaction and in turn address corresponding business goals. 

 

	In a similar fashion, you can see details of other segment suggestions that you are interested in. 

 

8. You can then save the segment by clicking on Save as segment in the side panel. The segment can then be viewed under the All segments tab and it can be used for downstream processes like any other dynamic segment. If you wish to look at the rules that the model learned after saving a segment, you can do so by clicking on Edit in the All segments tab. 

 

9. We have successfully found segment suggestions based on a categorical attribute of interest (CustomerSatisfaction). We also saved a segment which can then be utilized for downstream processes like any other dynamic segment.   

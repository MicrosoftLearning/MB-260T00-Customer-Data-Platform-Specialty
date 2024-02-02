---
lab:
    title: 'Lab 4.3: Create segments'
    module: 'Module 4: Work with Dynamics 365 Customer Insights - Data'
---

# Lab 4.3: Create segments 
# Module 4: Work with Dynamics 365 Customer Insights - Data

You will create marketing segments to promote Contoso Coffee's new Cold Brew Coffee offering as well as to identify customers with a higher-than-average online spend whom Contoso wish to target with their new subscription and connected coffee machine services. 

These segments will allow Contoso Coffee Marketing to deliver personalised, targeted marketing journeys for the upcoming product launch. 
 
## Exercise 1 - Create segments

Segments enable you to group your customers into cohorts based on demographic, transactional, or behavioural customer attributes. Using segmentation, you can achieve more targeted actions such as promotional campaigns, sales activities, or customer support actions to achieve desired business goals. You can define complex filters around the Customer Profile table and its graph of related entities. Each segment, after processing, outputs a set of customer table records that you can export and take actions against. 

Segments can be static (defined at the point you activate them) or Dynamic. If you create a Dynamic segment, customers will drop in and out of the segment as they meet or no longer meet the criteria. 

Using Customer Insights, Segments can be exported to Dynamics 365 Marketing or several other business applications and used to execute a targeted Customer Journey. Segments can also be exported to .csv or accessed via API. 

Customer Insights also provides insights over the created segments. Using Segment insights, you can find what differentiates two segments or what they have in common. Segment overlap shows which customers are common among the segments. Segment differentiators helps you find what differentiates a segment from the rest of your customers or the other segments. With both of these insights you can compare the segments against attributes and measures. 

In this lab you will segment your unified customer profiles, to uncover cohorts of customers with similar attributes. There are two ways to create segments. First you can create them manually by selecting **+ New > Build your own** on the toolbar after selecting **Segments** in the left navigation menu. In this lab, we will explore some of the methods of creating new Segments. At the end, we will review each segment and apply insights over them to discover additional information. 


### Task 1 - Segment using Profiles: Customers from California 

Let's create a segment called Customers from California quickly using the profiles. 

1.  If you haven't already, sign into Customer Insights at `https://home.ci.ai.dynamics.com`

3.  Expand **Insights** and select **Segments** from the left navigation menu. 

3.  Select **+ New > Create from Profiles**. 

4.  For **Field**, select **State** and for **Value**, choose **California**. 

5.  Select **Review**. 

6.  Name the segment `Customers from California` and verify the **Output table name** has been automatically populated with **CustomersFromCalifornia**. 

7.  Select **Save**. 


### Task 2 - Segment using Measures: High Value Online Customers 

Contoso Coffee Marketing wants to run a new promotion to convert customers to subscription model. Marketing have identified that they wish to target brew-at-home customers with a higher than average online purchase value to do so. We will create this segment using the Quick Create. 

1.  Select **Insights** > **Segments** from the left navigation menu. 

2.  Select **+ New > Create from Measures**. 

3.  Select the **Average Web Purchase ($)** attribute. 

4.  Set the **Operator** to **greater than**. 

5.  Set the **Value** to `138`. The graph should populate with Average Web Purchase ($) by percentile. 

6.  Select **Review**. 

7.  Name the segment `High Value Online Customers` and verify the **Output table name** has been automatically populated with **HighValueOnlineCustomers**. 

8.  Select **Save**. 


### Task 3 - Segment from scratch: Summer Promotion  

Contoso Coffee Marketing want to run a new Summer Promo targeting millennials with a higher than average in-store purchase with their newly launched Cold Brew Coffee. We will create this segment manually. 

1.  Select **Insights** > **Segments** from the left navigation menu. Select **+ New > Build your own**. 

2.  Next to the **Untitled segment** header text, select **Edit details** and change the **Name** to `Summer Promotion`

3.  Verify the **Output entity name** has been automatically populated with **SummerPromotion**, and select **Done**. 

4.  Under **Rule 1**, in the text box that reads "Enter an attribute name...", start entering `Average Store`. Select the **Average Store Purchase ($)** attribute. 

5.  Select **is** and **greater than or equal to**. And enter `113` (Note: 113 is the average in-store purchase we calculated earlier.) 

6.  Select **+ Add condition**. An *and* condition will be added. 

7.  In the **Attribute name** box, start entering `dateOf` and select the **dateOfBirth** attribute. 

8.  Select **is** and, **on or after** and enter the date as `1/1/1981` 

9.  Add another condition with an **and** qualifier. 

10.  Set this condition as **DateOfBirth is on or before** `12/31/1996` 

11. Select **Run**. 


### Task 4 - Review Segments 

1.  Wait for all your segments to successfully refresh, then navigate to the **Customer Insights - Data** home page. You should see your segments displayed, under **Recent segments**. 

2.  Select one of your segments. Under **Segments members preview** you will see customers included in the segment, as well a chart highlighting the **Segment size** over time. This will show increases and decreases in the number of segment members as data changes over time and the segment is refreshed. 

3.  Now that you have created segments, you are ready to start acting on the data. You can open a segment and select **Download** from the Command Bar to obtain a .CSV export of the segment for use in third party business applications. Be careful with the downloaded file as it will contain Customer PII (Personal Identifiable Information) and should be treated in accordance with applicable Data Security policies. Segments created in Customer Insights can be made available to other parts of the Power Platform, Dynamics 365 Marketing or external applications via API to avoid the need to download files. 


### Task 5 - Apply Segment Insights 

Let's try to find out common customers that belong to both Customers from California and High Value Online Customers segments and also what differentiates both of these segments in terms of Reward points and LifetimeSpend. 

1.  Select **Insights** > **Segments** from the left navigation menu. Select the **Insights (preview)** tab and select **+ New** from the command bar, or select the **+ New insight** button. 

2.  You will now see two options. Let's create using **Differentiators** first to see what distinguishes both of these segments. Select **Differentiators**. 

4.  Choose **High Value Online Customers** as the primary segment. Select **Next**, choose **Customers from California** as another segment, and then select **Next**. 

5.  Now choose **Reward points** under Customer fields and **LifetimeSpend** under Measure fields to see how the above segments differ from each other with respect to Reward points and LifetimeSpend. **Clear** all other customer and measure fields. 

6.  Select **Next** and name the insight `High Value Online vs Customers from California`

7.  Verify the **Output entity name** gets set to **HighValueOnlinevsCustomersfromCalifornia**. Select **Save**. 

8.  After the insight finishes refreshing, open the created insight. Select the **Attributes** or **Measures** tabs to see how the segments differ from each other with respect to the fields you selected. Observe the **Difference score**, which signifies the degree of difference. The higher the score, the more different they are.

    > **Note:** You may need to refresh the browser window to see the results. 

9.  Select each **measure** and **attribute** to see deeper insights. 

We have successfully created a Segment insight using **Differentiators**. Now let's create an insight using **Overlap**. 

9.  Make sure you're still in the **Segments > Insights (preview)** tab and select **+ New** from the command bar. Choose **Overlap**. 

10. Select both **High Value Online Customers** and **Customers from California** segments to find out their shared customers. 

11. Select **Next**. 

12. Optional: Choose some attributes to compare the segments, just as we did with the Differentiators. Or, select **Next** without choosing anything. 

13. Name the Segment Overlap "High Value Online Overlapped with California Customers" and verify the **Output entity name** is set to **HighValueOnlineOverlappedwithCaliforniaCustomers**. Select **Save**. 

14. After the insight finishes refreshing, open the created insight to see the venn diagram showing the total and percentage of shared customers between these two segments. 


### Task 6 - Segment Expansion 

Segment Expansion can be used to find similar customers to your segment customer base using Artificial Intelligence. 

Earlier we created a segment called **Summer Promotion**, which contains millennial customers with higher than average in-store purchase. Now, let's expand that segment and find customers that are similar to them for us to market our newly launched Cold Brew Coffee. 

1.  Select **Segments** from the left navigation menu and choose the **Summer Promotion** segment. This will become our source segment. 

2.  Select **Find similar customers** from the command bar. 

3.  Name your segment `SummerPromoExpansion` 

4.  Select **Add fields** in the next step to select attributes and measures that are used to find similar customers. We'll target customers with similar average in-store purchase and location, so choose **PostCode** and **AverageStorePurchase**. Select **Apply**. 

5.  Next you must choose who to consider. Either **All customers except source segment**, or **Customers from a different segment**. If a different segment is selected, then you must choose which segment it is. For now, select **All customers except source segment**. 

6.  Now the maximum number of customers to include must be selected. By default, 20% of all customers is selected which could be altered if required. Let's stick with 20%. 

7.  If you would like to include members from the source segment as well then check the last option. Otherwise, leave it unchecked. For our purposes, we can leave it unchecked.

8.  Select **Run**. 

9.  After the segment finishes refreshing, open the segment to find the **Similarity Scores** and explore the **Segment members preview**. 


## Exercise 2 - Get suggested Segments 

Use Suggested Segments to discover interesting segments based on a customer attribute or measure of interest.

### Task 1 - Discover segments based on a numeric customer attribute or measure of interest  

1.  Select **Segments** from the left navigation menu, and select the **Suggestions (preview)** tab. 

2.  Select **+ New > Suggested segments** to begin the configuration experience. 

3.  Choose **Improve a measure/metric** and select **Start**. 

4.  Under **Measure fields**, select **LifetimeSpend** as the target attribute. Select **Next**.

5.  Next, you will select the attributes that might influence the target attribute (LifetimeSpend) so the AI model can find interesting patterns between the influencing and target attribute. The model will suggest segments based on those patterns. Select **Email Subscriber**, **Income**, **Loyalty Tier**, **Occupation** and **State** as the influencing attributes. 

    > **Note:** In case you do not know which attributes to select, it is advised to select many attributes so that the model can analyze, and surface segment suggestions based on the underlying patterns it uncovers. However, if you want to see how certain attributes influence **LifetimeSpend**, you can choose only those as well. 

6.  Select **Run**. The AI model will start finding patterns between the selected influencing attributes and target attributes to surface segment suggestions. Please wait for a few minutes for the model to finish its analysis. 

7.  Once the model has finished running and if it is able to uncover patterns between the influencing attributes and the target attribute, segment suggestions will be displayed under the **Suggestions (preview)** tab. 

    Since we've chosen a numeric attribute as the target attribute, segment suggestions include those where the average value of the chosen target attribute (LifetimeSpend) is significantly higher or lower that the average LifetimeSpend value across all customers. We will also explore a scenario where a categorical attribute (such as, Customer Satisfaction: Low/Medium/High) is chosen as the target attribute in the next task. 

    Each segment suggestion card denotes how the average LifetimeSpend in that segment compares to the overall average. The number of customers in the suggestion as well as the rules learned (Common traits of customers in the segment) are also highlighted. 

    For example, in the above suggestion, **LifetimeSpend** is 20% above average. That is, the customers in this segment have historically spent much more as compared to others. There are 585 members in this segment and they have Income > 97,000 and a **high** Loyalty Tier. 

8.  You can select any suggestion to see more details in the side panel. We will select the **See suggestion** link for the suggestion that says **LifetimeSpend is 15% below average**. In the **Suggested segment details** panel, you will see the following: 

    - Comparison of average LifetimeSpend of customers in this segment compared to all the customers. 

    - Number of customers in the segment and the proportion as compared to the entire customer base. 

    - The attribute values, that is the rules that the model learned based on the selected influencing attributes. 

In this case, customers in this segment have an average LifetimeSpend of 741.89 as compared to average LifetimeSpend of 869.74 across all customers. There are 599 members in this segment which is 12% of the entire customer base. These customers are not Email Subscribers, have an income less than 44k, do not belong to the high loyalty tier and are teachers. This information can then be used to target customers in this segment with personalized messaging to drive more revenue and corresponding business goals. 

In a similar fashion, you can see details of other segment suggestions that you might be interested in. 

9.  To save the segment, select **Save as segment** in the **Suggested segment details** panel. Select **Save**. 
  
10. The saved segment can then be viewed under the **All segments** tab and it can be used for downstream processes like any other dynamic segment. If you wish to look at the rules that the model learned after saving a segment, you can do so by selecting **Edit** in the **All segments** tab. 

Congratulations! We have successfully found segment suggestions based on a measure of interest (LifetimeSpend). We also saved a segment which can then be utilized for downstream processes like any other dynamic segment. 


### Task 2 - Discover segments based on a categorical customer attribute or measure of interest 

1.  Under the **Segments > Suggestions (preview)** tab, select **+ Find new suggestions** on the top command bar to explore segment suggestions based on a different customer attribute or measure. 

    > **Note:** This will replace the existing set of suggestions. 

2.  Choose **Improve a measure/metric**. Select **Start**. 

3.  Select **CustomerSatisfaction** as the target attribute of interest. Customer Satisfaction is a categorical attribute with 3 categories (low/medium/high) and we’d like to find segment suggestions based on this attribute. Select **Next**. 

4.  Select **Email Subscriber**, **Income**, **Loyalty Tier**, **Occupation**, **RewardsPoints** and **State** as the influencing attributes. 

5.  Select **Run**. The AI model will start finding patterns between the selected influencing and target attributes to surface segment suggestions. Please wait for a few minutes for the model to finish the analysis. 

6.  Once the model has finished refreshing attribute based suggestions, segment suggestions will be displayed on the **Suggestions (preview)** tab. Since the target attribute is categorical, the AI model tries to find patterns or common traits of customers belonging to a particular category of the target attribute and surfaces segment suggestions. Since Customer Satisfaction has 3 different categories - low, medium and high - the AI model will try to find segments of customers that possess the same traits and a significant portion of them belong to a particular category (Either low, medium or high). 

    > **Note:** While only a few tiles are shown initially, you can select **See more ->** to reveal further suggestions. 

7.  Select the **83% of customers in this suggestion have CustomerSatisfaction = low** suggested segment. In the **Suggested segment details** panel, you will see the following: 

    - Comparison of percentage of customers in this segment that have CustomerSatisfaction = Low as compared to percentage of all customers that have CustomerSatisfaction = Low. 

    - Number of customers in the segment and the proportion as compared to the entire customer base. 

    - The attribute values, that is the rules that the model learned based on the selected influencing attributes. 

    In this case, 83% of customers in this segment have CustomerSatisfaction = low as compared to 26% among all customers. There are 488 members in this segment which is 10% of the entire customer base. These customers live in **California**, do not belong to the **high** Loyalty Tier, are not **Teachers** and do not live in **Florida**. This helps provide insight that 94% of customers having the above-mentioned traits have a low customer satisfaction. This information can then be used to target customers in this segment with personalized messaging and/or customer service to help improve their customer satisfaction and in turn address corresponding business goals. 

    In a similar fashion, you can review the **Suggested segment details** of other segment suggestions that you may be interested in. 

8.  To save the segment, select **Save as segment**. The segment can then be viewed under the **All segments** tab and it can be used for downstream processes like any other Dynamic Segment. If you wish to look at the rules that the model learned after saving a segment, you can do so by selecting **Edit** from the **All segments** tab. 

Congratulations! We have successfully found segment suggestions based on a categorical attribute of interest (CustomerSatisfaction). We also saved a segment which can then be utilized for downstream processes like any other Dynamic Segment. 


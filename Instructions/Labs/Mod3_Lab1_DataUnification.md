---
lab:
    title: 'Lab 3.1: Unify the data'
    module: 'Module 3: Create a unified customer profile in Dynamics 365 Audience insights'
---

# Lab 3.1: Unify the data
# Module 3: Create a unified customer profile in Dynamics 365 Audience insights

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

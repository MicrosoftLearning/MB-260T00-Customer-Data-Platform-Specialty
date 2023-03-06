---
lab:
    title: 'Lab 3.1: Unify the data'
    module: 'Module 3: Create a unified customer profile in Dynamics 365 Customer Insights'
---

# Lab 3.1: Unify the data
# Module 3: Create a unified customer profile in Dynamics 365 Customer Insights

Having ingested the raw data from your data sources into entities you will now begin the Map, Match, Merge process to create a single Unified Customer Profile by merging data from each customer profile source. 

To do this you will first map your ingested entities against a standard model and select the Primary Key for each of your profiled entities. Following the completion of this you will then create your Match Rule that will be used to match contacts from all customer entities. 

Finally, running the Merge process will create a single set of unique Customers having matched profiles from all customer entities using your match rules. 

Your objective is to find out how many unique customer profiles Contoso Retail has across various data sources. 


## Exercise 1 - Unify the data

## Task 1 - Map contacts to common data types 

1.  If you haven't already, sign into Customer Insights at https://home.ci.ai.dynamics.com/.

2.  On the left menu, expand **Data**, select **Unify**. Select **Get started**. Under **Source fields** on the right-hand side, select **+ Select entities and fields**. 

3.  Select the entities that represent the customer profile - **Contacts (eCommerce)** and **Customers (Loyalty)**. Then select **Apply**.

4.  You will now be presented with the mappings of your source entity against standard model types. You can review the types in the table. 

5.  You must choose a 'Primary Key' for each entity you have ingested. The primary key must be a unique reference. For eCommerce Contacts, select **ContactId** as the primary key. 

6.  The eCommerce Contacts data contains a column named **Email Subscriber** which will be mapped to an incorrect type, **Identity.Service.Email**, because of the name. Open the dropdown for this field and select the empty option (nothing/blank). If we do not do this then the default system behaviour is to merge this field with the EMail field which we do not want. 

7.  Select **Loyalty Customers** under Entities and set **LoyaltyId** as the primary key. 

8.  Select **Save source fields** in the top left-hand corner. 

9.  Select **Next** and **Next** again, to skip the duplicate checking and move on to the **Matching conditions** step. 


## Task 2 - Specify Match Order 

For the next stage, we must select the order in which to merge the profiles. You will be able to merge attributes to ensure that the unified profiles are complete as well as the priority of which sources to use for those attributes. 

1.  You should select the most complete or accurate profile source as the Primary (first) source. Use the arrow buttons to move **Contacts : eCommerce** as the primary (first) Source (if it isn't already). Select the check mark to **Include all** records. 

2.  Confirm that **Customers : Loyalty** is now the second source in the list. Choose to **Include all** records. 


## Task 3 - Create a Match Rule 

In this task, you will create a simple rule used to match records together. Rules can consist of single (e.g. based on ID) or multiple conditions (e.g. Full Name, Postcode, Date of Birth). 

For further details on Match Rules, please see [Customer Insights documentation](https://docs.microsoft.com/en-us/dynamics365/customer-insights/audience-insights/match-entities#define-rules-for-match-pairs). 

1.  There is a warning indicator on the Customers : Loyalty line. Select **+ Add rule** or select the + icon oo the right. 

2. Add the first condition using FullName: 

	- For the **Contacts : eCommerce** entity, select the **FullName** field. 
	
	- For the **Customers : Loyalty** entity, select the **FullName** field. 
	
	- Leave the **Normalize** drop-down blank. 
	
	- Set the Precision Level to **Basic**. 
	
	- Set the Precision Value to **High** using the slider. 

3. Enter the name `FullName, Email` for the rule. 

4. Add a second condition for email address by selecting **+ Add** and selecting **Add condition**. 

	- For the **Contacts : eCommerce** entity, select the **EMail** field. 
	
	- For the **Customers : Loyalty** entity, select the **EMail** field. 
	
	- Leave the **Normalize** blank. 
	
	- Set the Precision Level to **Basic**. 
	
	- Set the Precision Value to **High**.

5. Select **Done**. 

6. Select **Next**, select **Next** and select **Create customer profiles**.

Customer Insights is now matching customer data from all your sources of customer information to identify how many unique customer profiles you would have based on your rules. 

Confer with the class: **How many unique customers do you have when combining your datasets?** 


## Task 4 - Precision

In Task 3, we used High Precision in the match-rule against Full Name. In this task, you will adjust the precision level to create a higher number of matches by including matches of a lower confidence (resulting in a lower number of unique profiles). 

**Notes on Precision:** 

- **Exact** on the right-side of the scale, will match records where your condition has an exact match. Select one of the other levels to match records that are not 100% identical. 
- **High** fits cases where precision is more important than reach, such as a financial service to a specific customer. 
- **Low** fits cases where the opposite is true, such as a marketing campaign. 
- The **Medium** level serves as a middle-ground option. 

1. Ensure you are in the **Match** tab. Expand your rule and click the **Pencil** button to edit the Match rule. 

2. Move the Precision slider for your FullName match from High to Low. Then click **Done.**

3. Click **Save** and then **Run.** 

4. Once the match process has completed, open the vertical dots button next to your rule and select **Match Preview** to see the match results and the Confidence Score. This shows how Customer Insights matched the data tables based on the rules you have defined. You will notice that some profiles have been created with a low confidence of matching. 

5. Close the preview and click the **Pencil** icon to edit the match rule. Click the Preview button below the FullName rule. 

6. Here you can preview the number of Unmatched and Matched for your full name criteria. 

7. Click Preview Data under Unmatched or Matched to preview the matches. Notice how High Confidence uses exact spelling but can match even if the name format (First Name, Last Name / Last Name, First Name) is different. With Low confidence, notice how matches are made even when names are not spelled identically. 

7. Close the Criteria Preview page and click **Cancel.**

How many Unique Customer Profiles do you have now? 

## Task 5 - Merge 

The merge phase is the last phase in the data unification process. Its purpose is reconciling conflicting data and to define the attributes that will be used in your unified customer profile. 

A Merged attribute is an attribute that exists in more than one data source and represents the same piece of data. For example, we may have ‘Email Address' in both eCommerce Customers and Loyalty Customer data sources. 

Customer Insights will attempt to identify attributes to be merged using their mapping to the standard data types we used in the Map stage. 

1. Click on the **Merge** tab to switch to the Merge area of the Unify section.

2. You will be presented with the Merge screen. Note that attributes from different sources that are of the same type (e.g. First Name) have been merged.

2. Click the **FirstName** merged attribute. You should see that the FirstName attribute in eCommerce : Contacts is ranked number 1. This denotes that where you have a matching customer profile in LoyaltyScheme and eCommerce, the FirstName taken from eCommerce : Contacts will be the primary. 

3. Click the **Rename** button (it resembles a text box) on the row for the FirstName merged attribute. Note that you’re able to change the Output Field Name. The Output Field Name is the name that will be used in the Merged Profile.   

4. Click Cancel. 

5. Note that the Primary Keys from the original sources cannot be merged. For example, we have a ContactId as the primary key from eCommerce : Contacts and we also have ContactId within Loyalty : Customers. In fact, we are merging these records not on ContactId, but on FullName & Email. 

6. On the ContactId for the Loyalty : Customers Entity, click the **Rename** button and rename the Output Field Name to **ContactIdLOYALTY** to differentiate the item from the other IDs ingested and help avoid any confusion later. 


7. Click **Save** and **Run > Run Merge and downstream processes** to start the Merge Process. 

Congratulations! You have successfully Ingested, Mapped, Matched and Merged data from multiple sources within Customer Insights to create a Unified Customer Profile that can be used to gain insights into your whole customer base! 

## Exercise 2 - Search for customers 
In this exercise, we will set up Search and Filter criteria to enable Customer Insights users to search for unified customer profiles so that you can quickly pull information on a specific customer or group of customers. 

### Task 1 - Configure the Search Columns and Filter Index 

1. Click **Customers** in the left menu bar.

2. Click **Search & filter index.** 

3. Some customer search specific fields are already added by default and you can add more by clicking **Add** on the right-hand side. Click **Add** now.
 
5. Make sure **CustomerId, FirstName, LastName, FullName, DateOfBirth, EMail, PostCode, Headshot, ContactId (eCommerce_Contacts),** and **LoyaltyId** are selected. Deselect any other fields that are checked. Click **Apply**.

5. Click **Save** and then click **Run**.

### Task 2 - Search for a Customer Record 

1. Click **Customers** in the left menu bar. You should be presented with a set of customer cards, representing the Unified Profiles. You can expand cards to see more about the customer or sort the cards with various fields by clicking on **Expand cards** and **Sort options** on the top. 

2. You can use the search bar to search for text attributes relating to unified customer profiles. (E.g. Searching '24502' will search against all text attributes and return matches and partial matches.)

Use the search bar to answer the following questions. 

- What is Brian Gobble's Date of Birth? (Search with value 'Brian Gobble') 

- Which customer has Loyalty Card ID LOYID_5707? (Search with value 'LOYID_5707') 

- Which customer has a postcode of 24502? (Search '24502') 


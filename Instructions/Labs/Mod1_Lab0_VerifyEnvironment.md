---
lab:
    title: 'Lab 1.1: Verify environment'
    module: 'Module 1: Get started with Dynamics 365 Customer Insights'
---

# Lab 1.1: Verify environment
# Module 1: Get started with Dynamics 365 Customer Insights

## Approximate Time to Complete - 30 mins 

This appendix contains step-by-step instructions to provision and configure a Customer Insights environment, including prerequisites. 

### WWL Tenants - Terms of Use
If you are being provided with a tenant as a part of an instructor-led training delivery, please note that the tenant is made available for the purpose of supporting the hands-on labs in the instructor-led training. 
Tenants should not be shared or used for purposes outside of hands-on labs. The tenant used in this course is a trial tenant and cannot be used or accessed after the class is over and are not eligible for extension. 
Tenants must not be converted to a paid subscription. Tenants obtained as a part of this course remain the property of Microsoft Corporation and we reserve the right to obtain access and repossess at any time. 


## Step 1: Power Apps License 

1.  Now that you have a working Office 365 tenant, we will add a Power Platform trial license to the tenant. Open a new tab and navigate to [https://powerapps.microsoft.com](https://powerapps.microsoft.com/)[.](https://powerapps.microsoft.com/) On this page you will see a **Try free for 30 day** link on the top right. Select that link and enter the email for the admin account you were provided. Select **Start your free trial**. 

2.  Enter the password provided. If prompted, enter a phone number. (It is recommended to keep the location set to United States, and enter `0123456789` for phone number.) 

3.  Select **Get started**. You will be taken to the Power Apps homepage. Select **Skip** if prompted with the tutorial. 


## Step 2: Power BI Trial  

1.  You will also need a Power BI Trial to create dashboards showing the information from Customer Insights. To get started navigate to [https://aka.ms/trybi](https://aka.ms/trybi)[]([https://aka.ms/trybi](https://signup.microsoft.com/get-started/signup?sku=a403ebcc-fae0-4ca2-8c8c-7a907fd6c235&email=&ru=https%3a%2f%2fapp.powerbi.com%2f%3fpbi_source%3dweb%26redirectedFromSignup%3d1%26noSignUpCheck%3d1&products=a403ebcc-fae0-4ca2-8c8c-7a907fd6c235&brandingId=28b276fb-d2a0-4379-a7c0-57dce33da0f9&ali=1&bac=1&signedinuser=anjenni%40microsoft.com)) in a new tab. 

2.  You will be prompted to use your M365 admin credential. Select **Continue** to confirm and follow the same steps from the previous task to add the Power BI trial.

3.  Select **Get started**. It may take a few minutes for Power BI to set up. 


## Step 3: Dynamics 365 Marketing Trial 

Now that we have users with licenses in our Office 365 tenant, we can create our demo Dynamics environments. 

1.  In a new browser tab, navigate to [https://dynamics.microsoft.com/en-us/dynamics-365-free-trial/](https://dynamics.microsoft.com/en-us/dynamics-365-free-trial/). 

2.  Select the **Marketing** tab and select **Try for free**. Enter your provided admin email and select **Start your free trial**. You will then be prompted to enter your country and phone number. Select **Submit**. 

3.  It may take a moment for the trial to build. When the **Launch Trial** button appears, select it to enter the Dynamics 365 Marketing application. 


## Step 4: Customer Insights Trial 

Now that we have setup our Admin user, Power Apps license, Power BI and Dynamics 365 Marketing trial, we are ready to request our trial of Customer Insights. 

1.  In a new browser tab, navigate to [https://aka.ms/tryci](https://signup.microsoft.com/get-started/signup?SKU=036c2481-aa8a-47cd-ab43-324f0c157c2d&ali=1&RU=https%3a%2f%2fhome.ci.ai.dynamics.com%2fstart%2ftrial&products=036c2481-aa8a-47cd-ab43-324f0c157c2d&brandingId=28b276fb-d2a0-4379-a7c0-57dce33da0f9).

2.  Select **Continue** to stay signed in using your M365 admin account. Fill out the necessary information and click **Continue**. 

3.  Select **Get started**. 

4.  If prompted to enter your country again, select **United States** and select **Continue**. 

5.  Select **Individual consumers (B-to-C)** on the **Choose your business** page. 

6.  Your trial will launch and you'll arrive on the Welcome page. For the **Select an industry demo** drop-down, select **Retail**. This will load retail demo data into the  environment. 

7.  Select the **Start trial** button in the header. 

8.  Next you will create the environment. For **Name**, enter **Your Name** CI ILT Lab. Select **Next**. 

9.  Select **Next** again and for Microsoft Dataverse environment, select **Marketing Trial**. 

10. Select **Next**, review the selections and finally select **Create**. 

11. Once it completes you will be at the landing retail demo page for Customer Insights. Using the environment selector, make sure you are in the environment you created. You are now ready to start on the labs. 


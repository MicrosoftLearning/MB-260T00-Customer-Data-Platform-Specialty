## Approximate Time to Complete - 30 mins 

 

This appendix contains step-by-step instructions to provision and configure a Customer Insights environment, including prerequisites. This should only be followed if the environment has not been set up for your training session. If it has, please complete Lab 3 instead of this appendix. 

 

**Note:** completing this lab requires enrolling in certain Microsoft cloud services using trial subscriptions. You may need to supply your own telephone number and a credit card to subscribe. To avoid charges, remember to cancel your trial subscriptions at the end of the course, or before the trial periods end (durations vary by product). 

  

## Step 1 - Office 365 Trial 

The first step in the process is to create an Office 365 tenant for your user accounts. Open an"in privat" browser window and navigate to [https://aka.ms/appinadayo365signup](https://aka.ms/appinadayo365signup)[.](https://aka.ms/appinadayo365signup) Fill in your email address and click **Next** 

![Picture 1](Static/Appendix_A_Picture1.png)

On the next screen, you will want to click on the **Create a new account instead** 


![Picture 222](Static/Appendix_A_Provision_the_Infrastructure_image1.jpeg)

  

  

You are now able to fill in information about yourself, then click **Next**

![Picture 2](Static/Appendix_A_Picture2.png)
 

Now you will be asked for a phone number to text or call with a verification code. 

![Picture 3](Static/Appendix_A_Picture3.png)

After entering the verification code and continuing you will next be able to choose your business identity. You will need to provide a company (tenant name). We suggest using something unique and personal to you, your name may work. 

![Picture 298](Static/Appendix_A_Provision_the_Infrastructure_image2.jpeg)

 

Finally, you will need to create your admin account and a password for it. We recommend using 'admin' for your email address as that is the account you are creating. You'll have something like admin@CIILTLab.onmicrosoft.com for your account. When you have finished click **Sign up**. 

![Picture 300](Static/Appendix_A_Provision_the_Infrastructure_image3.jpeg)

 

  

Once everything completes you will get a page like this where you can click **Go to Setup** if you'd like to setup mail or install office apps. For the purposes of this training you are done at this point and do not need to do either of those things. 

![Picture 331](Static/Appendix_A_Provision_the_Infrastructure_image4.jpeg)

 



## Step 2 Power Apps License 

Now that you have a working Office 365 tenant, we will add a Power Platform trial license to the tenant. Open a new tab and navigate to [https://powerapps.microsoft.com](https://powerapps.microsoft.com/)[.](https://powerapps.microsoft.com/) On this page you will see a **Try free button** on the top right. Click that button and enter the email for the admin account you created in the last step. 

![Picture 401](Static/Appendix_A_Provision_the_Infrastructure_image5.jpeg)

 

You will then get the **Almost There** screen, click the **Start** button. 

![Picture 403](Static/Appendix_A_Provision_the_Infrastructure_image6.jpeg)

 

Upon clicking **Start** you will be taken to the Power apps page. 

  

## Step 3 Power BI Trial  

You will also need a Power BI Trial to create a nice dashboard showing the information from Customer Insights. To get started navigate to [https://aka.ms/trybi](https://aka.ms/trybi)[](https://aka.ms/trybi)in an in-private or incognito window. 

On the page enter the email for your admin account created in Step 1, like this and then click **Sign Up**. 

![Picture 468](Static/Appendix_A_Provision_the_Infrastructure_image7.jpeg)

 

Click on the **Sign in** button and enter your password. Then click **Start**. 

![Picture 470](Static/Appendix_A_Provision_the_Infrastructure_image8.jpeg)

 

On the **Invite more people** screen you can click **Skip.** Finally, you will need to install the Power BI desktop application from here: [https://www.microsoft.com/en](https://www.microsoft.com/en-us/download/details.aspx?id=55330)[-](https://www.microsoft.com/en-us/download/details.aspx?id=55330)[us/download/details.aspx?id=55330](https://www.microsoft.com/en-us/download/details.aspx?id=55330)[](https://www.microsoft.com/en-us/download/details.aspx?id=55330)

## Step 4 Dynamics 365 Marketing Trial 

Now that we have users with licenses in our Office 365 tenant, we can create our demo Dynamics environments. Navigate to [https://trials.dynamics.com/Dynamics365/marketing](https://trials.dynamics.com/Dynamics365/marketing)[](https://trials.dynamics.com/Dynamics365/marketing)where you will see this page. 

![Picture 4](Static/Appendix_A_Picture4.png)

Select the **Marketing** box and then fill in the email and phone number. This should be the admin email you created in Step 1 (something like admin@CIILTLab.onmicrosoft.com). After you fill in the info and click the **Next** button, you'll get a screen telling you that"you have an account with us, click **Sign In.** Next, you'll have a screen asking about sharing information, simply click **Create** to move ahead. 

During the setup process you may be presented with one or more **Permissions requested** screen. If so, check the **Consent on** behalf box and then click Accept. Once it has completed you will see a final consent screen check both boxes and enter any physical address then click **Get Started**. 

![Picture 5](Static/Appendix_A_Picture5.png)
 

Finally, click the **Begin** button and you will be taken to the D365 Marketing application. 

 


## Step 5 Customer Insights Trial 

Now that we have setup our Admin user, Power Apps license and Dynamics we are ready to request our Trial of Customer Insights. Open a new"in privat" browser instance and navigate to [https://aka.ms/tryci](https://aka.ms/tryci)[.](https://aka.ms/tryci) 

On the page you see, click on '**Yes, add it to my account'** 

![Picture 644](Static/Appendix_A_Provision_the_Infrastructure_image9.jpeg) 

This will kick off the process to add 25 user licenses for a trial to your tenant. First, you will need to click the **Try now** button on the Confirm your Order page. 

![Picture 6](Static/Appendix_A_Picture6.png)

Click **Continue.** It will open the Microsoft 365 admin page. Here you need to assign CI license to the admin user you created. 

![Picture 7](Static/Appendix_A_Picture7.png)

Expand the **Billing** menu option and click on **Licenses** and then click on **Dynamics 365 Customer Insights.** 

![Picture 714](Static/Appendix_A_Provision_the_Infrastructure_image10.jpeg) 

Click on +**Assign licenses.** Choose your admin account in the right pop up menu and click **Assign.** 

Open https://home.ci.ai.dynamics.com/Start. 

The first screen is labeled **Customize your trial**. Choose an industry to load the demo environment where you can explore all the pre-setup features and insights with the chosen industry demo data. Let's choose **Retail** and review the terms and conditions and click **Continue.** 

![Picture 8](Static/Appendix_A_Picture8.png)

Next you will create the environment. We suggest you name it CI ILT Lab. Once you enter the name and select the region you can click **Create**. 

![Picture 9](Static/Appendix_A_Picture9.png)

 

Once it completes you will be at the landing retail demo page for Customer Insights. Switch to your environment by clicking on top right at **Environment** and you are good to start on the labs. 

![Picture 10](Static/Appendix_A_Picture10.png)

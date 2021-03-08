JOIN UDF COURSE
===============

Welcome to the Telemetry Streaming course! In this course we will:

Explore F5 Telemetry Streaming, by using a declarative API model to forward, aggregate and analyze BIG-IP telemetry.

During this hands-on lab you will learn the following:

- How to use F5's declarative API to deploy applications via AS3. 

- How to use F5's declarative API to collect application statistics via Telemetry Streaming.

- How to use two data consumers to visualize statistics from Telemetry Streaming.

This lab will go through initial setup and add you to the Telemetry Streaming Symposium 2021 workstation.  

Follow these steps to complete this lab.



**EXERCISE 1 - SETTING UP THE LAB WORKSTATION**

#. From your client's web browser, navigate to `https://udf.f5.com <https://udf.f5.com>`__.
#. Login with your UDF credentials.  If you have not previously logged into UDF an email was sent to the address you provided with a temporary password to complete the registration process.   If you are returning UDF user but do not remember you password, simply click the password reset button to start the password reset process.
#. Locate the **[Symposium2021] Automation: Service Analytics and Metrics with TS course** and select **LAUNCH**. 

   .. image:: ./schedule.png

#. Click **JOIN** to join the Session: 
   
   .. image:: ./join.png

#. Click **CONTINUE** to enter into the Session: 
   
   .. image:: ./continue.png

#. Click the **DEPLOYMENT** tab in the top left, which contains all of the components deployed for this lab. 

   .. image:: ./class.png



**EXERCISE 2 - RDP TO THE WINDOWS JUMPHOST**

In this exercise, we will connect to the Windows Jumphost.   

#. Go into the **DEPLOYMENT** tab, and locate the **JUMPHOST** block. 

#. Click **DETAILS** in the **JUMPHOST** block and **copy the administrator password**. You will need this in the next step to access your RDP. 

   .. image:: ./credentials.png

#. Click **ACCESS** -> **'RDP'** and this will download a **.rdp** file to your local machine. 

   .. image:: ./system1.png

#. Once the RDP has downloaded, open the **.rdp** file and when prompted, select **CONTINUE**. 
#. If you are using Windows and receive RDP security dialogs, click **CONNECT** to proceed. If you are not using Windows then proceed to the next step.

   .. image:: win-rdp-prompt-1.png
   
   Click **YES** to proceed.

   .. image:: win-rdp-prompt-2.png

#. When prompted for the Administrator password, paste into the password field the password copied from the previous step. 

   .. image:: ./loginrdp.jpg

#. You should now be in your windows Jumphost. 

   .. image:: ./windows.jpg

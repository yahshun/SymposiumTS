Telemetry Streaming With AWS Cloudwatch
=======================================

In this lab we will configure our Telemetry Streaming JSON declaration to establish a connection between our AWS consumer and our BIG-IP. 

**Task 1 - Login to AWS Cloudwatch**
  
#. From your client, return to the UDF webisite and click on the Documentation tab

#. From the Cloud Accounts section, copy the Console Username and Console Password (keep this tab open for the next section). Click the Console URL. Paste in the Console Username and Console Password. 

   .. image:: ./cw1.png    

#. Once logged in, click the Services dropdown, search and select Cloudwatch 

   .. image:: ./cw2.png

#. On the left pane, under Logs select Log groups. Under the Actions dropdown select Create log group. 

   .. image:: ./cw3.png

#. Name the log group (ie my_log_group) and select the Create log group blue button. 

#. Click on the log group you just created. Select Create Log Stream and name your log stream (ie my_log_stream) 

   .. image:: ./cw4.png
 
**Task 2 - Edit the AWS Cloudwatch TS Declaration**
  
#. Return to the Jumphost's RDP session and the Postman application

#. Expand the Collection titled `Create AWS Cloudwatch Consumer`. Open the AWS Cloudwatch request. Open the Body tab of the request 
   
   .. image:: ./cw5.png

#. We need to edit the My_Consumer JSON section with setting from our AWS environment. 

#. Edit the region value to match what is located in the UDF Cloud account section. 

#. Edit the logGroup value to match the name of the log group you previously created in the AWS Console.

#. Edit the logStream value to match the name of the log stream you previously created in the AWS Console. 
 
#. Copy the API Key from the Cloud account section to the username value.

#. Copy the API secret from the Cloud Account Section to cipherText value. 

   .. image:: ./cw1.png
    
   .. image:: ./cw7.png
 
#. Click the blue Send to POST the Telemetry Streaming declaration. Ensure a 200 OK response. 
 
**Exercise 3 – View the logs in AWS Cloudwatch**

#. Return to the AWS Console and naviate to Cloudwatch 

#. Navigate to the log stream you created. 

#. Notice that logs have been populated in the log stream. 

   .. image:: ./cw6.png

#. Expand the log. Scroll down and you will find data on the virtual servers, pools, and various other objects.  

**Exercise 5 – Manipulate the Search**

#. On the left pane, select the subcategory Insights 

   .. image:: ./cw8.png

#. Click into the Select log group(s) search bar and select your group. Then click the Run query button. 

   .. image:: ./cw9.png

#. You can manipulate the search field with our examples.

   .. code-block:: sql
    
      fields @timestamp, @message, system.hostname, system.cpu, system.tmmCpu
          | stats avg(system.cpu) as SystemCpu, avg(system.tmmCpu) as TmmCpu by bin(5m), system.hostname

   .. code-block:: sql

      fields @timestamp, @message, system.hostname
           |parse @message "clientSideTraffic.bitsIn\":*," as clientsin
           |parse @message "clientSideTraffic.bitsOut\":*," as clientsout

#. Paste the either of the code blocks into the text box and click Run Query 

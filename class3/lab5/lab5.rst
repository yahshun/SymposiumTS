TELEMETRY STREAMING WITH AWS CLOUDWATCH
=======================================

In this lab we will configure our Telemetry Streaming JSON declaration to establish a connection between our AWS consumer and our BIG-IP. 



**EXERCISE 1 - LOGIN TO AWS CLOUDWATCH**
  
#. From your client, return to the `UDF website <https://udf.f5.com>`__ and click on the **DOCUMENTATION** tab for this lab.

#. From the Cloud Accounts section, copy the **REGION**, the **Console Username** and **Console Password** (keep this tab open for the exercises below). Click the **CONSOLE URL**. Paste in the **Console Username** and **Console Password**. 

   .. image:: ./cw1b.png    

#. Once logged in, click the **SERVICES** dropdown, search and select **CLOUDWATCH**. 

   .. image:: ./cw2b.png

#. On the left pane, under **LOGS** select **LOG GROUPS**. Select **CREATE LOG GROUP** on the right side. 

   .. image:: ./cw3b.png

#. Name the log group. Example: **my_log_group** and select the **CREATE** orange button on the bottom right-hand side. 

   .. image:: ./cw3c.png

#. Click on the log group you just created. Select **CREATE LOG STREAM** and name your log stream Example: **my_log_stream**.

   .. image:: ./cw4b.png
 


**EXERCISE 2 - EDIT THE AWS CLOUDWATCH TS DECLARATION**
  
#. Return to the **Jumphost's RDP session** and the **Postman** application.

#. Expand the Collection titled **CREATE AWS CLOUDWATCH CONSUMER**. Open the **AWS CLOUDWATCH** request. Open the **BODY** tab of the request.
   
   .. image:: ./cw5b.png

#. We need to edit the **My_Consumer JSON** section with the settings copied earlier from our AWS environment at the top of this lab. 

   .. image:: ./cw1b.png

   .. image:: ./cw5c.png

#. Edit the **region** value to match what is located in the **UDF Cloud account section**. 

#. Edit the **logGroup** value to match the name of the log group you previously created in the AWS Console. Example: **my_log_group**

#. Edit the **logStream** value to match the name of the log stream you previously created in the AWS Console. Example: **my_log_stream**
 
#. Copy the **API Key** from the cloud account section to the **username value**.

#. Copy the **API secret** from the cloud account Section to **cipherText value**. 
    
#. Click the blue **SEND** to POST the Telemetry Streaming declaration. Ensure a **200 OK** response. 
 
   .. image:: ./cw7b.png



**EXERCISE 3 - VIEW THE LOGS IN AWS CLOUDWATCH**

#. Return to the AWS Console and navigate to **CLOUDWATCH**.

#. Navigate to the log stream you created. Example: **my_log_stream**

#. Notice that logs have been populated in the log stream. 

   .. image:: ./cw6b.png

#. Expand the log. Scroll down and you will find data on the virtual servers, pools, and various other objects.  



**EXERCISE 4 - MANIPULATE THE SEARCH**

#. On the left pane, select the subcategory **INSIGHTS**.

   .. image:: ./cw8b.png

#. Click into the Select **log group(s) search bar** and select your group. Then click the **RUN QUERY** button. 

   .. image:: ./cw9b.png

#. You can manipulate the search field with these examples.

   .. code-block:: sql
    
      fields @timestamp, @message, system.hostname, system.cpu, system.tmmCpu
          | stats avg(system.cpu) as SystemCpu, avg(system.tmmCpu) as TmmCpu by bin(5m), system.hostname

   .. code-block:: sql

      fields @timestamp, @message, system.hostname
           |parse @message "clientSideTraffic.bitsIn\":*," as clientsin
           |parse @message "clientSideTraffic.bitsOut\":*," as clientsout

#. Paste the either of the code blocks above into the text box and click **RUN QUERY**. 

   Example Output

   .. image:: ./cw10.png

.. note:: This concludes the F5 telemetry Streaming lab.
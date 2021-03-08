TELEMETRY STREAMING WITH KIBANA
===============================

In this lab we will configure our Telemetry Streaming JSON declaration to establish a connection between our Kibana consumer and our BIG-IP. 



**EXERCISE 1 - CONFIGURE KIBANA AS THE TELEMETRY CONSUMER**

#. From Postman, Expand the collection **CREATE ELK CONSUMER**. 

#. Click the **ELK CONSUMER** request.

#. Click on the **BODY** tab and review the configurations below. 

   .. image:: ./elkbody.jpg
   
   .. hint:: Here is what is important from this declaration: 

   * The Listener collects event logs from all BIG-IP sources, including LTM, ASM, AFM, APM, and AVR. You can configure all of these by POSTing a single AS3 declaration or you can use TMSH or the GUI to configure individual modules.  

   * The Consumer class is the third party consumer we wish to send our captured data to. 
  
#. Send the POST request by clicking the blue **SEND** button on the right-hand side. Ensure a **Status: 200 OK** response.  

   .. image:: ./elkresponse.png

.. note:: By sending this GET request to ``https://10.1.1.9/mgmt/shared/telemetry/declare`` with the correct credentials and current body we've established a connection between our consumer and our BIG-IP. 

.. note:: Additionally, you should see a Read Only collection in Postman.  These API calls are necessary to configure the Elastic database and provide a mapping of indexes between the BigIP and Elastic.  You do not need to send these commands as the ELK environment is already pre-configured.

.. note:: To learn more about AS3, see `Application Services 3 Extension Documentation <https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/>`__. For AS3 with Telemetry Streaming see `F5 Telemetry Streaming <https://clouddocs.f5.com/products/extensions/f5-telemetry-streaming/latest/>`__.



**EXERCISE 2 - GENERATE TRAFFIC ON OPENCART**
  
#. From the UDF page, find the host named **TRAFFIC GEN** and select **WEB SHELL** from the dropdown. 

   .. image:: ./trafficgen.png

#. Type **su** for sudo user access and press **ENTER**. If prompted, the password is **toor**.  

#. Change directory by typing: **cd /home/ec2-user**

#. Run the **baseinline** script by typing the command: **./baseline_menu.sh**

#. From the menu, choose **2) Alternate** and press **ENTER**. Let it run while you continue with the labs.



**EXERCISE 3 - ANALYZE TELEMETRY VIA KIBANA**

#. Return to the Jumphost's RDP session, open a new tab in Chrome and click the **KIBANA** bookmark.

#. Select the **DISCOVER** tab on the top left.

#. Ensure that **F5** is selected in the dropdown and that a reasonable time range is selected in the top right (ie 15 minutes in the screenshot below).

   .. image:: ./f5selected.jpg

#. Now you should see some logs coming in. 



**EXERCISE 4 - CREATE A SIMPLE KIBANA VISUALIZATION**

#. In Discover field, type: ``data.http_code \: 40*`` 
   
   This will show you all HTTP responses starting with 40. Press the blue **REFRESH** to apply.

   .. image:: ./kib_1.png

#. Click the **VISUALIZE** tab on the left and click **CREATE A VISUALIZATION**.

#. You can explore various types of graphs. For this exercise we will select the **LINE GRAPH**.

#. Under **SELECT INDEX** select ``f5\*``

#. On the left, under Buckets select **X-AXIS**. Select **DATE HISTOGRAM** from the **AGGREGATION** dropdown, **data.event_timestamp** from the **FIELD** dropdown, and **AUTO** from the Interval dropdown.

   .. image:: ./kib_2.png

#. Now select the **APPLY CHANGES PLAY BUTTON** next to Panel Settings. Press the blue **REFRESH** button on the top right. View your visualization as the Telemetry data comes in.

   .. image:: ./kib_3.png

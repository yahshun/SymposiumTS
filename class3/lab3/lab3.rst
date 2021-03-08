DEPLOY A WEB APPLICATION
========================

In this lab we will use the AS3 API too programmatically deploy an application to the BIG-IP with a single REST call.


**EXERCISE 1 - EXPLORE BIG-IP**

#. Open Chrome and navigate to the BIG-IP GUI ``https://10.1.1.9`` or by clicking the bookmark on the bar. 

#. Proceed past any security warnings by clicking **ADVANCED** and then **Proceed to 10.1.1.9 (unsafe)**.

   .. image:: ./privacy-error.png

#. Login to the BIG-IP with the following credentials:

   +---------------+------------------------------------+
   | Username      |        **admin**                   |
   +---------------+------------------------------------+
   | Password      |    **AgilityIsFun123!**            |
   +---------------+------------------------------------+

#. Once you are logged in, navigate to **LOCAL TRAFFIC** -> **VIRTUAL SERVERS** -> **VIRTUAL SERVERS LIST**. 

   .. image:: ./vslist.jpg

#. Note that you are in the **COMMON** partition (top-right) and the BIG-IP has no Virtual Servers, Pools or Pool Members configured. 

   .. image:: ./vslistdisplay.png


**EXERCISE 2 - CONFIGURE AND DEPLOY THE HTTP APPLICATION VIA AS3 WITH THE APPROPRIATE TELEMETRY STREAMING CONFIGURATION**

The focus for this exercise is to deploy an application with the appropriate Telemetry Streaming configuration objects.

#. Minimize Chrome and open the Postman application.

#. Expand the Postman collection **DEPLOY APPLICATION** to view the requests.

#. Click the **CREATE APPLICATION VIA AS3** request.

#. Click on the **BODY** tab and examine the request body. 

   .. image:: ./jsonbody.jpg

   .. hint::  Here is what is important in this declaration: 
   
   * The telemetry_local_rule allows traffic through port 6514.  

   * The telemetry_traffic_log_profile builds a logging profile which specifies the log parameters. 

   .. image:: ./as3snippet.png

#. Send the POST request by clicking the blue Send button.

#. Ensure you received a **Status: 200 OK** response. 

   .. image:: ./200response.jpg

.. note:: By sending this GET request to ``https://10.1.1.9/mgmt/shared/appsvcs/declare`` with the correct credentials and current body we've built an application declaratively via AS3. 

.. note:: To learn more about AS3, please see `Application Services 3 Extension Documentation <https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/>`__. 


**EXERCISE 3 - VERIFY SUCCESSFUL DEPLOYMENT VIA BIG-IP GUI**

#. Open Chrome. 

#. Click the BIG-IP bookmark or navigate to ``https://10.1.1.9``

#. Login to the BIG-IP with the following credentials:

   +---------------+------------------------------------+
   | Username      |        **admin**                   |
   +---------------+------------------------------------+
   | Password      |    **AgilityIsFun123!**            |
   +---------------+------------------------------------+

#. Once you are logged in, navigate to **LOCAL TRAFFIC** -> **VIRTUAL SERVERS** -> **VIRTUAL SERVERS LIST**. 

   .. image:: ./vslist.jpg

#. Notice that you are currently in the **COMMON** partition and that there is now an application built named **opencart_vs**. 

   .. image:: ./ocbigip.png



**EXERCISE 4 - VERIFY WEB APPLICATION**

#. In Chrome, click on the **+** to open a new tab and show the bookmark tool bar.

   .. image:: ./chrome_new_tab.png

#. In Chrome, click on the **OpenCart** bookmark. 

   .. image:: ./ocbookmark.jpg

#. Verify the application is working by clicking a few tabs and view some products. 

   .. image:: ./opencart.jpg

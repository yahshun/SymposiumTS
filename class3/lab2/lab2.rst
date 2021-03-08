REVIEW API CALLS
================

In this lab section we are introducing Postman, an API Development Environment that helps us structure API calls. We will send GET requests to obtain the RPM package that shows details of the API.


**EXERCISE 1 - CHECK APPLICATION SERVICES 3 EXTENSION (AS3) RPM AVAILABILITY**
  
#. Open Postman. 

#. Open the the Postman collection **VERIFY INSTALLATION**.

   .. image:: ./postman1.jpg

#. Click the **GET AS3 RPM PACKAGE** request.

#. Examine the request in the grey box near the top. Note that we are sending a **GET** request with an empty body. Send the **GET** request by clicking the blue **SEND** button on the right hand side.

   .. note:  We have built in auth for you, using Basic username and password authentication. 

   .. image:: ./send1.jpg

#. You should see a similar response. 

   .. image:: ./as3rpm.jpg

.. note:: By sending this GET request to ``https://10.1.1.9/mgmt/shared/appsvcs/info`` with the correct credentials, the response shows details of the AS3 API available on this BIG-IP. 

.. note:: This AS3 RPM package was pre-installed. For instructions, see `Downloading and installing the AS3 package <https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/userguide/installation.html>`__.


**EXERCISE 2 - CHECK TELEMETRY STREAMING RPM AVAILABILITY**
  
#. Click the **GET TS RPM PACKAGE** request.

#. Examine the request. Note that we are sending a **GET** request with an empty body. Send the **GET** request by clicking the blue **SEND** button. 

   .. image:: ./sendts.jpg

#. You should see a similar response. 

   .. image:: ./tsrpm.jpg

.. note:: By sending this GET request to ``https://10.1.1.9/mgmt/shared/telemetry/info`` with the correct credentials, the response shows details of the TS API available on this BIG-IP. 

.. note:: This Telemetry Streaming RPM package was pre-installed. For instructions, see `Downloading and installing Telemetry Streaming <https://clouddocs.f5.com/products/extensions/f5-telemetry-streaming/latest/installation.html>`__.

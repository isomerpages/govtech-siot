---
layout: leftnav-page-content
title: Sending Commands Downstream
permalink: /starter-kit/sending-commands-downstream/
breadcrumb: Sending Commands Downstream
collection_name: starter-kit
---

# Sending service request
*These steps will show how to send commands from DECADA to device through a service request*

1. Login to DECADA

2. Go to Product and select your product

![service-request](/images/riots-dk/decada-setup/decada_setup_product_1.png)

3. Go to Debugging tab

4. In the drop-down list for Device (see below), select your Device

![service-request](/images/riots-dk/sending-commands-downstream/service_request_1.png)

5. Make sure your device is connected to DECADA (you will see Device is online like shown below) 

![service-request](/images/riots-dk/sending-commands-downstream/service_request_2.png)

6. Under Debugging, select the service (with the prefix S: like shown below) and change the value on the right (replace the "2 bytes length"). Click Run.

![service-request](/images/riots-dk/sending-commands-downstream/service_request_3.png)

When the response from the device is received, you should see this success message.

![service-request](/images/riots-dk/sending-commands-downstream/service_request_4.png)

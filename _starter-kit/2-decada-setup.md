---
layout: leftnav-page-content
title: Decada Setup
permalink: /starter-kit/decada-setup/
breadcrumb: Decada Setup
collection_name: starter-kit
---

# Setup your DECADA for RIOTS
## Creating your Model
*Model is the summary of features of the devices that are connected to the DECADA Cloud, including attributes, measure points, services and events of the device.*

1. Login to DECADA

2. Go to Model and click on **New Model**

![model](/images/riots-dk/decada-setup/decada_setup_model_1.png)

3. Fill in the fields to create your model

An example of how you can create your model is shown below:

![model](/images/riots-dk/decada-setup/decada_setup_model_2.png)



## Creating your Measure Point(s)
*Measure Points are entities expected to be received upstream from devices. Examples are `temperature` and `humidity`.*

1. Once your model has been created, go to **Edit** on the rightmost column for your model
2. Go to **Feature Definition** tab (beside Basic Information)
3. Click on **Add**
4. Under **Feature Type** drop-down list, select **Measure Points**

For this demo, make sure the identifier is **ambient_temp** and data type is **double**

![measurepoints](/images/riots-dk/decada-setup/decada_setup_measurepoints_1.png)

An identifier is:
- A unique ID given to a measure point
- At least 4 characters in length with no space.
- The name of the measure point you send upstream to DECADA
- Uneditable once you have created the measure point.

If you have used the identifier for another measurepoint, you will see this error message:

![measurepoints](/images/riots-dk/decada-setup/decada_setup_measurepoints_2.png)



## Creating your Service(s)
*Services are for sending commands downstream to your device.*

1. Click on **Add**

2. Under **Feature Type** drop-down list, select **Service**

Fill in **name** and **identifier** of your service in the fields provided.

Take note that the identifier has to be at least 4 characters in length and **only alphanumeric characters** are allowed.

An example for adding a service is shown below:

![service](/images/riots-dk/decada-setup/decada_setup_service_1.png)

3. Select **Synchronous**, as we will send an acknowledgement response upon receiving a command from DECADA Cloud.

4. Select **New Parameter** for **Input Parameters**. An input parameter is a specific command you want to send to your device (e.g. change sensor poll rate, wifi credentials)

Fill in the form for the new parameter. 

We will use **string** as our parameter data type in this guide. For string length, set it as 5. *In general, add 2 to your maximum character length as buffer (e.g. max character length for sensor poll rate to be set as 3 characters, so string length is 3+2=5)*

Sending multiple parameters in a single instance downstream is also supported.

![service](/images/riots-dk/decada-setup/decada_setup_service_2.png)

5. Select **New Parameter** for **Output Parameter**. An output parameter is a specific response you want to receive from your device after your service request (e.g. sensor poll rate updated)

Fill in the form for the new parameter. Set **string** as our parameter data type and the string length as 6.

![service](/images/riots-dk/decada-setup/decada_setup_service_3.png)

6. Click OK when you are done creating your service(s).



## Creating your Product
*Product is the collection of the devices that are connected to the DECADA Cloud.*

1. Go to Device Management > Product
![product](/images/riots-dk/decada-setup/decada_setup_product_1.png)

2. Click on New Product

Fill in the **Product Name**. Select **Device** for **Asset Type** and the model you have created previously from the **Model** drop-down box.

Select **Json** for **Data Type** and **enable** the **Certificate-based bi-directional authentication**.

![product](/images/riots-dk/decada-setup/decada_setup_product_2.png)

3. Once your product is created, click on **View** on the rightmost column for your product.

Activate the **Enable Dynamic Activation** (outlined in red below). This allows devices to register itself without having to manually on-board each individual device on DECADA.

![product](/images/riots-dk/decada-setup/decada_setup_product_3.png)


## Creating your Application
*Application gives devices access to DECADA APIs.*

1. Go to **Application Registration** using the left sidebar

![application](/images/riots-dk/decada-setup/decada_setup_application_1.png)

2. Click on **Register App** (outlined in red below) to create a new application

![application](/images/riots-dk/decada-setup/decada_setup_application_2.png)

3. Fill in the details to create your application

![application](/images/riots-dk/decada-setup/decada_setup_application_3.png)

4. Once your application has been created, you will be redirected to App Details, which displays your application name, *application access key* and *secret key*, as shown in the image below. (Some information has been omitted)

![application](/images/riots-dk/decada-setup/decada_setup_application_4.png)



## Configuring your Device(s)
*Devices are objects that are connected to the DECADA Cloud, defined and managed by the Product and Model they are registered under.*

1. You will need to note down a few credentials needed to configure your device.

  a. Go to **Product** and select your product, you will be able to get your:
   - Organization Unit ID (hover over your Model Name at the top as shown below)
   - Product Key
   - Product Secret

   ![device](/images/riots-dk/decada-setup/decada_setup_device_1.png)

  b. Go to **Application Registration** and select your Application (see *Creating your Application step 4*), you should be able to get your:
   - Access Key (under accessKey)
   - Access Secret (under secretKey)

2. Keep these credentials for a later step --- RIOTS Software Setup: **Input DECADA Credentials into Source Code**.


---
layout: leftnav-page-content
title: Set up your Cloud Service
permalink: /starter-kit/set-up-your-cloud-service/
breadcrumb: Set up your Cloud Service
collection_name: starter-kit
---

# Setup your DECADA for MANUCA
## 1. Creating your Model
*Model is the summary of features of the devices that are connected to the DECADA Cloud, including attributes, measure points, services and events of the device.*

1. Go to [DECADA](https://portal.decada.gov.sg) and login with your user credentials.

2. Open the left navigation panel, go to **Model** and click on **New Model**

<img class="large" src="/images/manuca/decada-setup/decada_setup_model_1.png" alt="model">

3. Fill in the fields to create your model

An example of how you can create your model is shown below:

<img src="/images/manuca/decada-setup/decada_setup_model_2.png" alt="model">


## 2. Creating your Measurement Point(s)
*Measure Points are entities expected to be received upstream from devices. Examples are `temperature` and `humidity`.*

1. Once your model has been created, go to **Edit** on the rightmost column for your model
2. Go to **Feature Definition** tab (beside Basic Information)
3. Click on **Add**
4. Under **Feature Type** drop-down list, select **Measurement Points**

> In this user guide, we will use the identifier **ambient_temp** of data type **double**.

<img src="/images/manuca/decada-setup/decada_setup_measurepoints_1.png" alt="measurepoints">

An identifier is:
- A unique ID given to a measure point
- At least 4 characters in length with no space.
- The name of the measure point you send upstream to DECADA
- Uneditable once you have created the measure point.


## 3. Creating your Service(s)
*Services are for sending commands downstream to your device.*

1. Click on **Add**

2. Under **Feature Type** drop-down list, select **Service** and fill in name of the service.

> In this user guide, we will use the identifier **sensorpollrate**.

Take note that the identifier has to be at least 4 characters in length and **only alphanumeric characters** are allowed.

<img src="/images/manuca/decada-setup/decada_setup_service_1.png" alt="service">

3. Select **Synchronous**, as we will send an acknowledgement response upon receiving a command from DECADA Cloud.

4. Select **New Parameter** for **Input Parameters**. An input parameter is a specific command you want to send to your device (e.g. change sensor poll rate, wifi credentials)

> In this user guide, we will use the identifier **sensor_poll_rate** for the input parameter, **string** as the data type and string length of **5** bytes. 

*In general, add 2 to your maximum character length as buffer (e.g. max character length for sensor poll rate to be set as 3 characters, so string length is 3+2=5)*

Sending multiple parameters in a single instance downstream is also supported.

<img src="/images/manuca/decada-setup/decada_setup_service_2.png" alt="service">

5. Select **New Parameter** for **Output Parameter**. An output parameter is a specific response you want to receive from your device after your service request (e.g. sensor poll rate updated)

> In this user guide, we will use the identifier **success** for the output parameter, **string** as the data type and string length of **6** bytes. 

<img src="/images/manuca/decada-setup/decada_setup_service_3.png" alt="service">

6. Click OK when you are done creating your service(s).


<a id="DecadaProduct"></a>

## 4. Creating your Product
*Product is the collection of the devices that are connected to the DECADA Cloud.*

1. On the left navigation panel, go to **Device Management** > **Product**
<img class="large" src="/images/manuca/decada-setup/decada_setup_product_1.png" alt="product">

2. Click on **New Product**

Fill in the **Product Name**. Select **Device** for **Asset Type** and the model you have created previously from the **Model** drop-down box.

Select **Json** for **Data Type** and **enable** the **Certificate-based bi-directional authentication**.

<img src="/images/manuca/decada-setup/decada_setup_product_2.png" alt="product">

3. Once your product is created, click on **View** on the rightmost column for your product.

Activate the **Enable Dynamic Activation** (outlined in red below). This allows devices to register themselves without you manually on-boarding each individual device on DECADA, provided that the devices have the appropriate credentials. (This will be elaborated further in the section **Configuring your Device(s)**)

<img class="large" src="/images/manuca/decada-setup/decada_setup_product_3.png" alt="product">


<a id="DecadaApplication"></a>

## 5. Creating your Application
*Application gives devices access to DECADA APIs.*

1. On the left navigation panel, go to **Application Registration**.  

<img class="large" src="/images/manuca/decada-setup/decada_setup_application_1.png" alt="app">

2. Click on **Create App** (outlined in red below) to create a new application

<img class="large" src="/images/manuca/decada-setup/decada_setup_application_2.png" alt="app">

3. Fill in the details to create your application

<img class="large" src="/images/manuca/decada-setup/decada_setup_application_3.png" alt="app">

4. Once your application has been created, you will see the `Success: App created` message and your application will be displayed as shown below.

<img class="large" src="/images/manuca/decada-setup/decada_setup_application_4.png" alt="app">

<a id="DecadaCredentials"></a>

## 6. Configuring your Device(s)
*Devices are objects that are connected to the DECADA Cloud, defined and managed by the Product and Model they are registered under.*

You will need to note down a few credentials needed to configure your device.  
- Organization Unit ID (OUID)
- Product Key
- Product Secret
- Access Key
- Access Secret

The following steps will elaborate on how to find these credentials:

1. You can find your OUID by going to the left navigation panel > **IAM** > **Organization Profile**.  
<img class="large" src="/images/manuca/decada-setup/decada_setup_ouid_1.png" alt="ouid">  

Your OUID is the id under **Organization ID** (see the screenshot below for reference).
<img class="large" src="/images/manuca/decada-setup/decada_setup_ouid_2.png" alt="ouid">


2. Next, go to left navigation panel > **Device Management** > **Product**

3. Select **View** under the **Operations** column for your product (see [Creating your Product](#DecadaProduct)), you will be able to get your:
- Product Key
- Product Secret

<img class="large" src="/images/manuca/decada-setup/decada_setup_productkey.png" alt="productkey">

4. Go to **Application Registration** and select your application (see [Creating your Application](#DecadaApplication)), you should be able to get your:
- Access Key (named `accessKey`)
- Access Secret (named `secretKey`)

<img class="large" src="/images/manuca/decada-setup/decada_setup_applicationkey.png" alt="applicationkey">

5. Keep these credentials for a later step – [Build and Flash Software: Input DECADA Credentials into Source Code](/starter-kit/build-and-flash-sw/#InputCredentials).

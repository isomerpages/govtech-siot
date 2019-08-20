---
layout: leftnav-page-content
title: DECADA Cloud
permalink: /tech-stack/decada-cloud/
breadcrumb: DECADA Cloud
collection_name: tech-stack
---

# Introduction to DECADA Cloud

**DECADA** (Device Management, Control and Data Acquisition Systems) is a multi-tenant cloud platform by GovTech that provides support for device management, data acquisition and data analytics of IoT devices.

The platform supports an ecosystem of applications that facilitate the acquisition and exchange of data. Applications are provided and managed by GovTech and third party vendors.

DECADA is part of the Singapore Government’s [Smart Nation Sensor Platform](https://www.tech.gov.sg/products-and-services/smart-nation-sensor-platform/) initiative. It is deployed on the Government Commercial Cloud (GCC). Plans are also underway to deploy the solution on the Government Digital Cloud (GDC).

<a id="DECADA-Product-Features"></a>
# Main Product Features

The DECADA Edge Gateway supports the following features:
* Asset Management
* Data Acquisition
* **Event Triggers**
* Stream Processing
* **Data Analytics**
* APIs and SDKs
* Generation of Reports
* **Application Framework**

We will be elaborating on three of our features **bolded** above.

## Event Triggers

Services can be created within DECADA to enable organisations to define, receive, and process alerts for their assets. Alert triggering rules can be defined against asset data to achieve responsive troubleshooting when anomalies occur.

![DECADA Event Alert Message Flow](/images/decada/features/alert_message_flow.png)

## Data Analytics

DECADA provides a series of toolkits for data analytics. Users can utilize data querying services to extract, cleanse and perform analysis for business decisions.

The main tools provided are:
* Data Integration
* Data IDE
* Workflow Operation
* Cluster Monitoring
* Data Explorer
* Metadata Explorer

![DECADA Data Analytics IDE](/images/decada/features/data_ide.png)

## Application Framework

DECADA empowers developers with the ability to create, manage and acquire resources of the organisation that they manage. The platform also provides identity management features to handle the authentication and authorisation of Application Programming Interface(API) calls made to it.

![DECADA Data Analytics IDE](/images/decada/features/app_framework.png)

Internally, containers are containerised and isolated in production.

<a id="DECADA-Connecting-To-DECADA-Cloud"></a>
# Connecting to DECADA Cloud

We offer 3 different ways of connecting to the cloud:
1. Direct Connection
2. DECADA Edge
3. Cloud-to-cloud

## Direct Connection

A direct connection between a sensor device and the DECADA cloud can be established with or without the use of DECADA’s SDKs (Software Development Kits).

### DECADA's SDKs

GovTech maintains SDKs that contain implementation for device registration, device data ingestion, data transmission and device control. As of August 2019, the SDKs will be published and will be available in Java, Python and C/C++. X86 and ARM processors are both supported.

### Vanilla Connection

In the event that the solutions provided by GovTech cannot meet the unique requirements of certain systems, clients can still interface with DECADA using supported device communication protocols such as:
* MQTT
* Constrained Application Protocol (CoAP)
* RESTful API via HTTPS

## DECADA Edge

GovTech provide a software solution that is x86/ARM architecture compatible. The solution can be deployed either on-premise, or as a virtual instance on the cloud. Please see [DECADA Edge](/tech-stack/decada-edge/) for more information.

## Cloud-to-Cloud

As some agencies might have existing infrastructure in place, GovTech provides customised cloud-to-cloud connection options that can integrate seamlessly with different implementations.

Examples of cloud-to-cloud connections include:
* Pushing - Forwarding data to a 3rd party cloud deployed by an agency
* Pulling - Retrieving data from an agency’s cloud system

In the above examples, the described data might be raw, filtered or even aggregated from the sensors.

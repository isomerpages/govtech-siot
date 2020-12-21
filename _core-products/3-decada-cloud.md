---
layout: leftnav-page-content
title: DECADA Cloud
permalink: /core-products/decada-cloud/
breadcrumb: DECADA Cloud
collection_name: core-products
---

# Introduction to DECADA Cloud

**DECADA** (Device Management, Control and Data Acquisition Systems) is a multi-tenant cloud platform by GovTech that provides support for device management, data acquisition and data analytics of IoT devices.

The platform supports an ecosystem of applications that facilitate the acquisition and exchange of data. Applications are provided and managed by GovTech and third party vendors.

DECADA is part of the Singapore Government’s [Smart Nation Sensor Platform](https://www.tech.gov.sg/products-and-services/smart-nation-sensor-platform/) initiative. It is deployed on the Government Commercial Cloud (GCC). Plans are also underway to deploy the solution on the Government Digital Cloud (GDC).

<a id="DECADA-Product-Features"></a>

# Main Product Features

The DECADA product supports the following features:

- Asset Management
- Data Acquisition
- **Event Triggers**
- Stream Processing
- **Data Analytics**
- Generation of Reports
- **APIs & Application Framework**

We will be elaborating on three of our features **bolded** above.

## Event Triggers

Alerts can be created within DECADA to enable organisations to define, receive, and process events for their assets. Alert triggering rules can be defined against asset data to achieve responsive troubleshooting when anomalies occur.

![DECADA Event Alert Message Flow](/images/decada/features/alert_message_flow.png)

Monitoring events of interest is a crucial capability when managing large fleets of sensors.

A deployed device or sensor might experience events that the maintainence team needs to be notifed of, including when a device is disconnected or when values beyond the expected range are detected.

Events can be consumed via a email notification, or via an API for monitoring via a dashboard or external tool.

## Data Analytics

DECADA provides a series of toolkits for data analytics. Users can utilize data querying services to extract, cleanse and perform analysis for business decisions.

The main tools provided are:

- Data Integration
- Data IDE
- Workflow Operation
- Cluster Monitoring
- Data Explorer
- Metadata Explorer

<img class="large" src="/images/decada/features/data_ide.png" alt="DECADA Data Analytics IDE">

## APIs & Application Framework

DECADA empowers developers with the ability to easily deploy and manage web applications through the Application Framework. The Framework includes a web portal for end users to log in and access applications that they are authorized for.

APIs are also provided so that data ingested by the platform can be consumed and used in other ways. For instance, a service is able to perform time series queries on sensor data and provide a dashboard interface for agencies to query aggregated data.

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

- MQTT
- Constrained Application Protocol (CoAP)
- RESTful API via HTTPS

## DECADA Edge

GovTech provides a software solution that is x86/ARM architecture compatible. The solution can be deployed either on-premise, or as a virtual instance on the cloud. Please see [DECADA Edge](/core-products/decada-edge/) for more information.

## Cloud-to-Cloud

As some agencies might have existing infrastructure in place, GovTech provides customised cloud-to-cloud connection options that can integrate seamlessly with different implementations.

Examples of cloud-to-cloud connections include:

- Pushing - Forwarding data to a 3rd party cloud deployed by an agency
- Pulling - Retrieving data from an agency’s cloud system

In the above examples, the described data might be raw, filtered or even aggregated from the sensors.

<a id="DECADA-Device Lifecycle Management"></a>

# Device Lifecycle Management

<img class="large" src="/images/decada/lifecycle/device_lifecycle_management.png" alt="Device Lifecycle Management Screenshot">

## Plan & Design Phase

DECADA requires users to plan and design how they will manage their devices. Devices are modelled based on their attributes and measure points. The connection scheme of the devices can be based upon hardware designs, deployment methods or security requirements. The hierarchy of the devices can be indicated too.

### Model Planning

The model is a template that describes the device. This template will contain attributes and measure points. A user is able to associate many devices to the same model.

### Hierarchy Planning

Asset trees can be arranged in a hierarchical form to better manage assets. Users can organize the assets according to:

- Geographical location: country, state, city, district, etc.
- Industry domain: wind power, photovoltaic, energy storage, etc.
- Device type: fan, inverter, combiner box, etc.

### Connection Scheme

The connection scheme is selected based on hardware capabilities of the devices and the security requirements of their connections.

## Provisioning Phase

Each device must be uniquely identified by its product key, device key and device secret (device triple).

If certificate authentication is required, a client can request for a certificate to be generated from the DECADA API.

In a device-end development scenario, users can utilise the SDK provided by GovTech to perform authentication with DECADA. DECADA will then validate the device triple. Upon verification, devices will be able to send data to DECADA.

Methods to provision devices are described below.

### Provisioning individual devices

  1. A user will create the _Model_, _Product_ and _Device_ in DECADA to obtain the device triple to be burned onto the device
  2. Devices will use the device triple to connect to DECADA cloud using the GovTech's SDK. Data can be transferred between devices and DECADA

### Provisioning Edge for multiple devices provisioning

  1. A user will create the _Edge Model_, _Product_ and _Device_ in DECADA to obtain its device triple
  2. A user will also create the _Model_, _Product_ and _Device_ of the sub-devices. The sub-devices are placed under the _Edge_
  3. Once the sub-devices are placed under the _Edge_, the user will use the _Edge_ device triple to connect to DECADA cloud. Data can be transferred to cloud via Edge

### Provisioning application to enable multiple devices registration

  1. A user can register an application that used to provision devices onto DECADA. Upon registration, the user will be provided with the application's access key and secret key
  2. The application will call the API to register and provision the new device and obtain the device triple
  3. The application will then use the device triple to connect to DECADA. Data can be transferred between devices and cloud

### Provisioning 3rd-party cloud
  1. The 3rd-party cloud will need to have an application to forward the device data to DECADA. The application will be registered to DECADA to obtain the access key and secret key
  2. The device connected to the 3rd-party cloud will be detected by the application. It will call the API to register and obtain the device triple for the new device
  3. The application will then use the device triple to connect to DECADA. Data can be transferred between devices and cloud

## Service Phase

Once the devices are provisioned, DECADA will be able to receive and monitor data transmitted. Other functionalities provided include:

- Monitoring of data from devices to cloud - The monitoring can be done through DECADA or external applications
- Enabling and disabling remotely - Services defined by the devices' models can be triggered
- Monitoring alerts sent via email or SMS. Alert triggering rules can be set up to react to real-time measure point telemetry
- Managing, consuming and storing data according to business needs

## Maintenance Phase

The firmware of devices can be updated over-the-air by DECADA.

Certificates will be renewed upon expiry for devices that require certificate authentication. This is to ensure that connectivity can be maintained.

## Decommissioning Phase

When devices are scheduled to be decommissioned, users can use the DECADA to:

- Disable and delete devices
- Revoke certificates of devices that were issued
- Archive data

<a id="DECADA-Service-Level-Agreement"></a>

# Service Level Agreement

## Infrastructure and Service Guarantee

### Cloud services

When two or more role instances are deployed in different fault and upgrade domains, at least one role instance will have Role Instance Connectivity of at least 99.95%.

### Virtual Machines

- For any single instance Virtual Machine using premium storage for all disks, the Virtual Machine Connectivity is at least 99.9%.
- For all Virtual Machines that have two or more instances deployed in the same Availability Set, the Virtual Machine Connectivity to at least one instance is at least 99.95% of the time.

### DNS

Valid DNS requests will receive a response from at least one Azure DNS name server all the time.

### SQL Database

Connectivity between DECADA MySQL Server and Internet gateway will be available at least 99.99% of the time.

### Loan Balancer

A load balanced endpoint using Azure Standard Load Balancer(serving two or more healthy Virtual Machine instances) will be available 99.99% of the time.

### Backup

Backup and restore functionality will be available at least 99.9% of the time.

### DDoS Protection

DDoS Protection Service will be available at least 99.99% of the time.

### Multi-Factor Authentication

Multi-Factor Authentication services will be available at least 99.9% of the time.

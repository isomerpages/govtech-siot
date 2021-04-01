---
layout: leftnav-page-content
title: Overview
permalink: /core-products/decada-embedded/
breadcrumb: DECADA Embedded - Overview
second_nav_title: "DECADA Embedded"
collection_name: core-products
---

# Introduction to DECADA Embedded

DECADA Embedded is a family of microcontroller-class devices that are capable of communicating directly to DECADA Cloud.

As part of the Singapore Government Tech Stack, DECADA Embedded provides software reference designs to hasten development time. By extending the reference examples, developers will be able to add their custom application logics for their use cases, while not having to fret over how onboarding and communication is done with DECADA Cloud in the software.

<a id="Sofware-References"></a>

## Software References

Real-time Operating System (RTOS) is recommended for embedded devices that connects to any cloud service, as the communication services can be offloaded to a separate thread from the core application logic itself. 
The RTOS reference examples follow the following model:
1. Data Ingestion
2. Process and Analyze
3. Respond

MQTT over TLS is the standard communication protocol to interact with DECADA Cloud. Several software modules are also included to help kick start your DECADA Embedded device development.

The golden public release repository can be found [here](https://github.com/GovTechSIOT/decada-embedded-example-mbedos), and would work almost off-the-shelf once the user has configured their personal DECADA credentials into the software. Besides Mbed OS RTOS, we are working to provide reference examples for other popular RTOS as well.

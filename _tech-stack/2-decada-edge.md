---
layout: leftnav-page-content
title: DECADA Edge
permalink: /tech-stack/decada-edge/
breadcrumb: DECADA Edge
collection_name: tech-stack
---

# Introduction to DECADA Edge Gateway

**DECADA Edge Gateway** is a product and software solution to onboard new and existing sensor nodes to DECADA securely with ease. It is both a Gateway to DECADA and an Edge to process and aggregate sensor nodes data to reduce data traffic to DECADA. It also provides the capability to make agile onsite decisions.

As part of the Singapore Government Tech Stack, DECADA Edge Gateway is open to be configured through its web user interface, allowing different combinations of sensor nodes connection and data processing. Partners can also develop and contribute their own [Edge Gateway plugin modules](#DECADA-EDGE-Plugins) to connect and process their sensors' data before sending it to DECADA.

DECADA Edge Gateway software can be deployed on a variety of hardware, ranging from low-power ARM Single-Board-Computer(SBC)s to full fledged Intel i7 gateways, with the hardware and the residing operating system environment conforming to the Singapore Government's security guidelines.

<a id="DECADA-EDGE-Product-Features"></a>
## Product Features

The DECADA Edge Gateway supports the following features:

* Secured connection to DECADA Cloud
* Firmware Over-The-Air (FOTA) update capability
* Transformation between communication protocols
* Web User Interface configuration
* Data Resiliency
* Data Aggregation
* Data Analytics

<a id="DECADA-EDGE-Design-Overview"></a>
### Design Overview

**DECADA Edge Gateway** software is written on top of open source QT C++ framework. There are two main parts in the software - **Core** modules and **Plugins**. Core modules compromises of managers that provides services for plugins to function.

<img class="large" src="/images/decada-edge/design/decada-edge-design-overview.png" alt="DECADA Edge Design Overview">

<a id="DECADA-EDGE-Plugins"></a>
### Plugins

DECADA Edge Gateway software supports plugins from its plugin ecosystem.  Each individual plugin can be viewed as a single function to achieve a single task.

Plugins enable adaptive and fast deployment, reducing the need to redevelop existing software in order to fulfil the unique requirements of different systems. New and existing plugins can be added and replaced without affecting existing Edge Gateway Software instances. Plugins are delayed loaded into DECADA Edge Gateway using the QT Plugins' architecture.

An example of the combination of plugins to achieve data acquisition from various sensor nodes, with data processing and sending to DECADA via a single MQTT channel is shown below.

<img class="large" src="/images/decada-edge/plugins/decada-edge-example.png" alt="DECADA Edge Plugin Example">

Plugins can be classified into the following categories:

<table>
  <tr>
    <th>Category of Plugins</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>I/O</td>
    <td>Acquire data from sensors</td>
  </tr>
  <tr>
    <td>Processing</td>
    <td>Transform, decorate, and/or filter metrics</td>
  </tr>
  <tr>
    <td>Information</td>
    <td>Collect information of the system</td>
  </tr>
  <tr>
    <td>Aggregation</td>
    <td>Create aggregate metrics (eg. mean, min, max, quantiles)</td>
  </tr>
  <tr>
    <td>Web</td>
    <td>Provide web interfaces for configuration or visualisation</td>
  </tr>
  <tr>
    <td>Analytics</td>
    <td>Perform video and data analytics</td>
  </tr>
</table>

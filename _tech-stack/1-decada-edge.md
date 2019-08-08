---
layout: leftnav-page-content
title: DECADA Edge
permalink: /tech-stack/decada-edge/
breadcrumb: DECADA Edge
collection_name: tech-stack
---

# Introduction to DECADA Edge Gateway

**DECADA Edge Gateway** is a product and software solution to onboard new and existing sensor nodes to DECADA securely with ease. It is both a Gateway to DECADA and an Edge to process and aggregate sensor nodes data to reduce data traffic to DECADA and provides the capability to make agile onsite decision.

As part of the Singapore Government Tech Stack, DECADA Edge Gateway is open to be configured through its web user interface, allowing different combination of sensor nodes connection and data processing. Partners can also develop and contribute their own [Edge Gateway plugin modules](#DECADA-EDGE-Plugins) to connect and process their sensor nodes' data before sending it to DECADA.

DECADA Edge Gateway software can be deployed on a variety of hardware, ranging from low-power ARM Single-Board-Computer(SBC)s to full fledged Intel i7 gateways, with the hardware and the residing operating system environment conform to Government security guidelines.

<a id="DECADA-EDGE-Product-Features"></a>
## Product Features

The DECADA Edge Gateway supports the following features:

1. Secured connection to DECADA Cloud
2. Firmware Over-The-Air (FOTA) update capability
3. Transformation between communication protocols
4. Web User Interface configuration
5. Data Resiliency
6. Data Aggregation
7. Data Analytics

<a id="DECADA-EDGE-Design-Overview"></a>
### Design Overview

**DECADA Edge Gateway** software is written on top of open source QT C++ framework. There are two main part in the software - **Core** modules and **Plugins**. Core modules compromises of all manager which main role is to provide services for plugins to function.

![DECADA EDGE Design Overview](/images/decada-edge/design/decada-edge-design-overview.png)

<a id="DECADA-EDGE-Plugins"></a>
### Plugins

DECADA Edge Gateway software supports plugins from its plugin ecosystem.  Each individual plugin can be viewed as a single function to achieve a single task.

Plugins enable adaptive and fast deployment, reducing the need to redevelop existing software in order to fulfil the unique requirements of different systems. New and existing plugins can be added and replaced without affecting existing Edge Gateway Software instance. Plugins are delayed loaded into DECADA Edge Gateway using QT Plugins architecture.

An example of a combination of plugins to achieve data acquisition from various sensor nodes, processes the data and send to DECADA via a single MQTT channel is shown below.

![DECADA EDGE Plugin Example](/images/decada-edge/plugins/decada-edge-example.png)

Plugins can be classified under the following categories:

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

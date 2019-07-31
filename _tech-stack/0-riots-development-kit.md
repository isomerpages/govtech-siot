---
layout: leftnav-page-content
title: RIOTS Development Kit
has_children: true
permalink: /tech-stack/riots-dk/
breadcrumb: RIOTS Development Kit
collection_name: tech-stack
---

# Introduction to RIOTS DK
The Robotics, Internet-of-Things and Sensors Development Kit (RIOTS DK) is an embedded sensor node development kit, designed to provide a platform on which multiple sensors can integrate and publish their measure points to DECADA Cloud swiftly.  

As part of the Singapore Government Tech Stack, RIOTS provides a reference design to the hardware and software used in developing sensor nodes that are DECADA-Ready. By extending the sensor library in RIOTS Operating System, users will be able to integrate their dedicated sensors onto the RIOTS Board, and read out the sensor measure point(s) in real-time on the DECADA Cloud dashboard.

## RIOTS Board
The **RIOTS Board** is the physical hardware –  it is powered by an ARM Cortex-M7 MCU with 2MB of flash memory, and supports both WiFi and Ethernet as its network communication interfaces. It supports up to 6 external sensors (3 for I2C interface, 3 for SPI) and has one on-board temperature sensor that can be used for monitoring the health of the RIOTS Board. The on-board temperature sensor is used in RIOTS Operating System as an example measure point. An ESP32 is used as the WiFi module.

Additional Details:

- Supports two (2) backup batteries, useful for events of intermittent power outage from the main power supply
- Supports three (3) programmable GPIO LEDs
- Supports flash memory extension through MicroSD Card

### RIOTS Board Layout

![RIOTS Board Layout](/images/riots-dk/intro/riots_board_front_labelled.png)

<table>
  <tr>
    <th>Components</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>ESP32 WiFi Module</td>
    <td>WiFi controller board; Header slot can be used for other communication modules, for example ZigBee</td>
  </tr>
  <tr>
    <td>TTL Serial</td>
    <td>Interface for serial debugging and powers the RIOTS Board concurrently; Connected to the development machine via TTL-USB Cable</td>
  </tr>
  <tr>
    <td>JTAG</td>
    <td>Interface for programming the MCU; Connected to the development machine via ST-LINK Programmer</td>
  </tr>
  <tr>
    <td>External Power Source</td>
    <td>Header for powering the RIOTS board; Not necessary if TTL Serial is in use</td>
  </tr>
  <tr>
    <td>Ethernet</td>
    <td>Socket for wired Local Area Network (LAN) connection</td>
  </tr>
  <tr>
    <td>STM32F767ZI</td>
    <td>MCU used for running RIOTS Operating System</td>
  </tr>
  <tr>
    <td>On-board Temperature Sensor</td>
    <td>Sensitive temperature sensor (TMP75) used for monitoring the temperature of the board, especially in hot outdoor conditions</td>
  </tr>
  <tr>
    <td>MicroSD Slot</td>
    <td>Insert a MicroSD Card (Not included in RIOTS development kit) for flash storage extension</td>
  </tr>
  <tr>
    <td>I2C</td>
    <td>3 Inter-Integrated Circuit Interface ports for external sensors</td>
  </tr>
  <tr>
    <td>SPI</td>
    <td>3 Serial Peripheral Interface ports for external sensors</td>
  </tr>
</table>

## RIOTS Operating System
**RIOTS Operating System** is a Real-Time Operating System (RTOS) example customized for the RIOTS Board –  it is based on mbedOS and developed to showcase the ease of developing RTOS applications using the RIOTS Board, that has the capability to publish data to the government cloud. RIOTS Operating System uses multi-threading to handle Data Ingestion (via Sensor Thread), Process and Analyze (via Behavior Coordinator Thread) and Respond (via Communication Controller Thread and Subscription Manager Thread). MQTT over TLS is the standard communication protocol to interact with DECADA Cloud. Several software modules are included to help kick start your sensor node RTOS development. The public release repository can be found [here](insert_github_url), and would work almost off-the-shelf once the user has configured their personal DECADA credentials into the software. After the binary is compiled, and flashed onto the RIOTS Board, you should observe temperature (using on-board temperature sensor) being updated on your DECADA Cloud measure points.

# Contents of RIOTS DK

![RIOTS DK Contents](/images/riots-dk/intro/contents.png)

<table>
  <tr>
    <th>Components</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>RIOTS Board</td>
    <td>Development Board</td>
  </tr>
  <tr>
    <td>Wifi Module</td>
    <td>Plug-in to the RIOTS Board; Handles wireless internet connectivity</td>
  </tr>
  <tr>
    <td>TTL-USB Cable</td>
    <td>Used for serial debugging, while concurrently powering the RIOTS Board</td>
  </tr>
  <tr>
    <td>DECADA Credentials</td>
    <td>To on-board RIOTS Board to DECADA Cloud (for demo use only)</td>
  </tr>
</table>

**Additional Tools** (not included in RIOTS DK)

<img src="/images/riots-dk/intro/stlink-v2.jpg" alt="ST-Link Programmer v2" width="150"/>
<img src="/images/riots-dk/intro/stlink-v3.jpg" alt="ST-Link Programmer v3" width="150"/>

<table>
  <tr>
    <th>Components</th>
    <th>Description</th>
  </tr>
  <tr>
    <td>ST-Link Programmer V2/V3</td>
    <td>For flashing the binary into the MCU of RIOTS Board</td>
  </tr>
</table>

---
layout: leftnav-page-content
title: Overview
permalink: /core-products/manuca/
breadcrumb: MANUCA - Overview
second_nav_title: "MANUCA"
collection_name: core-products
---

![MANUCA LOGO](/images/manuca/intro/main_logo_wo_tagline.png)

# Introduction to MANUCA

MANUCA, short for eMbedded Advanced Network of Micro Computing Applications, is a platform designed to integrate multiple sensors and publish their measure points to DECADA Cloud swiftly. The platform currently consists of [MANUCA Development Kit (MANUCA DK)](#MANUCA-DK) and [MANUCA Operating System (MANUCA OS)](#MANUCA-OS).

As part of the Singapore Government Tech Stack, MANUCA provides a reference design to the hardware and software used in developing sensor nodes that are DECADA-Ready. By extending the sensor library in MANUCA OS, users will be able to integrate their dedicated sensors onto the MANUCA DK, and read out the sensor measure point(s) in real-time on the DECADA Cloud dashboard.

<a id="MANUCA-DK"></a>

## MANUCA DK

The **MANUCA DK** is the physical hardware –  it is powered by an ARM Cortex-M7 MCU with 2MB of flash memory, and supports both WiFi and Ethernet as its network communication interfaces. It supports up to 6 hardware connectors (3 for I2C interface, 3 for SPI) which can be connected to more than a hundred sensors. An on-board temperature sensor is also included for monitoring the health of the MANUCA DK. The on-board temperature sensor is used in MANUCA OS as an example measure point. An ESP32 is used as the WiFi module.

Additional Details:

- Supports two (2) backup batteries, useful for events of intermittent power outage from the main power supply
- Supports three (3) programmable GPIO LEDs
- Supports flash memory extension through MicroSD Card

### MANUCA DK Layout

![MANUCA DK Layout](/images/manuca/intro/layout.png)

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
    <td>Interface for serial debugging and powers the MANUCA DK concurrently; Connected to the development machine via TTL-USB Cable</td>
  </tr>
  <tr>
    <td>JTAG</td>
    <td>Interface for programming the MCU; Connected to the development machine via ST-LINK Programmer</td>
  </tr>
  <tr>
    <td>External Power Source</td>
    <td>Header for powering the MANUCA DK; Not necessary if TTL Serial is in use</td>
  </tr>
  <tr>
    <td>Hardware Reset Button</td>
    <td>Button for manually resetting the system</td>
  </tr>
  <tr>
    <td>Programmable LEDs</td>
    <td>Software controlled GPIO LEDs; Programmable by user</td>
  </tr>
  <tr>
    <td>STM32F767ZI</td>
    <td>MCU used for running MANUCA OS</td>
  </tr>
  <tr>
    <td>On-board Temperature Sensor</td>
    <td>Sensitive temperature sensor (TMP75) used for monitoring the temperature of the board, especially in hot outdoor conditions</td>
  </tr>
  <tr>
    <td>MicroSD Slot</td>
    <td>Insert a MicroSD Card (Not included in MANUCA development kit) for flash storage extension</td>
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

MANUCA DK User Manual can be downloaded [here](/files/MANUCA_User_Manual_V1.pdf)

<a id="MANUCA-OS"></a>

## MANUCA OS

**MANUCA OS** is a Real-Time OS (RTOS) example customized for the MANUCA DK – it is based on mbedOS and developed to showcase the ease of developing RTOS applications using the MANUCA DK, that has the capability to publish data to the government cloud. MANUCA OS uses multi-threading to handle Data Ingestion (via Sensor Thread), Process and Analyze (via Behavior Coordinator Thread) and Respond (via Communication Controller Thread and Subscription Manager Thread). MQTT over TLS is the standard communication protocol to interact with DECADA Cloud. Several software modules are included to help kick start your sensor node RTOS development.

The public release repository can be found [here](https://github.com/GovTechSIOT/stack-manuca-os), and would work almost off-the-shelf once the user has configured their personal DECADA credentials into the software. After the binary is compiled, and flashed onto the MANUCA DK, you should observe temperature (using on-board temperature sensor) being updated on your DECADA Cloud measure points.

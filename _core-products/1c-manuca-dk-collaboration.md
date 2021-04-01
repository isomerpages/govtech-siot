---
layout: leftnav-page-content
title: Dev Kit Collaboration
permalink: /core-products/decada-embedded/dev-kit-collaboration/
breadcrumb: DECADA Embedded - Dev Kit Collaboration
second_nav_title: "DECADA Embedded"
collection_name: core-products
---

# MANUCA Development Kit Collaborations

---

We welcome industry partners to `manuca-ready` their commercial development boards.
In order to do so, you should :

1. Have a hardware that is capable of directly connecting to a cloud service. You may use the Hardware Requirements listed below as a guideline (but not limited to).
2. Provide an open-sourced software SDK that runs on your hardware, and is able to connect to DECADA, our IoT cloud (details in the Software Requirements section below).
3. Send your board to us verification.

During this process, you may require consultation and/or assistance from us. For example, you would need a temporary DECADA account to test your software SDK. You may reach out to us via email [here](https://www.siot.gov.sg/contact-us/).

#

# Hardware Requirements

---

## MCU

- ARM Cortex M3/M4/M4F/M7/M33 with clock speed of 120MHz and above
- SRAM of 256kB, in continuous block (320kB and above recommended for multi-threading support)
- Flash Memory of 1MB and above
- 512kB is sufficient for end-node devices (sense and send data; tested using mbed-os 5.14.2) using ARMC6.
- 1MB is set to factor in users that will compile using `gcc-arm`

## External Peripheral Port(s)/Socket(s)

- GPIO Port(s)
- I2C Port(s)
- SPI Port(s)
- USART/RS485 Port(s)
- Zigbee Socket - USART

## Onboard Sensor

- Temperature Sensor

## Connectivity Radio

Either PCB-mounted or via Zigbee Socket as an external accessory:

- WiFi Module (eg. ESP32) and/or
- Cellular Module (eg. Quectel BG96)

## Security

- Provisioned a dedicated tamper pin (eg. GPIO that triggers on hardware breaching)
- Able to set MCU read-out protection using tool

## Programming/Debugging

- Onboard in-circuit programmer and debugger module with serial debug via micro-usb/usb-c

## Optional Hardware Support

- Crypto Hardware Acceleration (MCU)
- microSD card slot (Storage)
- External NOR flash module (Storage)
- Accelerometer (Sensor)
- Secure Element (Security) - Recommended

#

# Software Requirements (SDK Example)

---

## Security

- Use of common TLS libraries (eg. mbedtls)
- Connection to DECADA via TLS 1.2
- Storage of private key
- Flash memory for low-risk application
- Secure Element for high-risk applications

## General Steps for Provisioning with DECADA

- The following sequence diagram illustrates the [Connect method](https://github.com/GovTechSIOT/stack-manuca-os/blob/master/src/DecadaManagerV2/decada_manager_v2.cpp#L27) of DecadaManagerV2, which uses DECADA API V2 for Device Provisioning:

![Sequence Diagram](/images/manuca/intro/decadamanagerv2_connect_seq_diagram.png)

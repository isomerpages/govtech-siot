---
layout: leftnav-page-content
title: Troubleshooting
permalink: /starter-kit/troubleshooting/
breadcrumb: Troubleshooting
collection_name: starter-kit
---

# FAQs

<table>
  <tr>
    <th>Question(s)</th>
    <th>Answer</th>
  </tr>
  <tr>
    <td>My RIOTS Board is unable to connect to the internet</td>
    <td>Ensure credentials are entered correctly in Boot Manager. If "NetworkInterface successfully configured" is printed out in serial debug, it means RIOTS Operating System has successfully connected to the internet.</td>
  </tr>
  <tr>
    <td>I am unable to see data updated in my DECADA dashboard</td>
    <td>Ensure your DECADA Cloud credentials in mbed_app.json are correct.</td>
  </tr>
  <tr>
    <td>I do not see serial debug read-outs from the RIOTS board</td>
    <td>Perform a Hardware reset or power cycle, and check if your serial port terminal is configured to read from the correct serial port. See RIOTS Board Setup for configuring your serial port terminal.</td>
  </tr>
  <tr>
    <td>No sensor readings updated on DECADA dashboard</td>
    <td>Test with example code to check if sensor is connected to the RIOTS board and functioning. If there is sensor reading, then the problem probably lies in the integration of the sensor into RIOTS Operating System. <details> <summary> Common issues </summary> - Polling the sensor faster than the sensor's measurement rate, resulting in no new available data; increase the sensor_thread sleep time to allow the sensor to measure a new set of data before reading the sensor <br><br> - Wrong I<sup>2</sup>C address used for I<sup>2</sup>C sensor; make sure the I<sup>2</sup>C address used in the sensor driver tallies with the address given in the sensor datasheet and the hardware configuration of the sensor's address (for sensors with multiple I<sup>2</sup>C address) <br><br> - I<sup>2</sup>C port pin name assigned to sensor is different from connected pins on the actual RIOTS board. See Reference for External Sensor Connectors for the pin names available for external sensor connections. </details></td>
  </tr>
  <tr>
    <td>I am unable to successfully drag-and-drop my compiled binary into the hardware</td>
    <td>Upgrade your ST-Link's firmware as described <a href="https://www.st.com/content/st_com/en/products/development-tools/software-development-tools/stm32-software-development-tools/stm32-programmers/stsw-link007.html">here</a></td>
  </tr>
</table>
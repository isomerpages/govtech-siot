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
    <td>I cannot find any files under mbed-os in my MANUCA OS</td>
    <td>Retry pulling the remote repository with <code>git clone --recurse-submodules https://github.com/GovTechSIOT/stack-manuca-os.git</code> <br> Take note that <code>--recurse-submodules</code> should be included when pulling the remote repository, if not your submodules will not be downloaded, resulting empty submodules folders.</td>
  </tr>
  <tr>
    <td>My MANUCA OS is unable to compile</td>
    <td><details> <summary> Error: No module named fuzzywuzzy </summary> Check your mbed-os version by entering in the Terminal window in your repository folder: <br> <code>cd mbed-os/</code><br> <code>git branch</code> <br> It should show <code>* (HEAD detached at 1bf6b20df9)</code> <br> If it does not, enter <code>git checkout 1bf6b20df9 </code> </details></td>
  </tr>
  <tr>
    <td>My MANUCA DK is unable to connect to the internet</td>
    <td>Ensure credentials are entered correctly in Boot Manager. If "NetworkInterface successfully configured" is printed out in serial debug, it means MANUCA OS has successfully connected to the internet.</td>
  </tr>
  <tr>
    <td>I am unable to see data updated in my DECADA dashboard</td>
    <td>Ensure your DECADA Cloud credentials in mbed_app.json are correct and the measurepoints configured on DECADA and names of the data being published from MANUCA OS are exactly the same.</td>
  </tr>
  <tr>
    <td>I do not see serial debug read-outs from the MANUCA DK</td>
    <td>Perform a Hardware reset or power cycle, and check if your serial port terminal is configured to read from the correct serial port. See <a href="/starter-kit/set-up-your-hardware/#SerialDebug">Set up your Hardware</a> for configuring your serial port terminal.</td>
  </tr>
  <tr>
    <td>No sensor readings updated on DECADA dashboard</td>
    <td>Test with example code to check if sensor is connected to the MANUCA DK and functioning. If there is sensor reading, then the problem probably lies in the integration of the sensor into MANUCA OS. <details> <summary> Common issues </summary> - Polling the sensor faster than the sensor's measurement rate, resulting in no new available data; increase the sensor_thread sleep time to allow the sensor to measure a new set of data before reading the sensor <br><br> - Wrong I<sup>2</sup>C address used for I<sup>2</sup>C sensor; make sure the I<sup>2</sup>C address used in the sensor driver tallies with the address given in the sensor datasheet and the hardware configuration of the sensor's address (for sensors with multiple I<sup>2</sup>C address) <br><br> - I<sup>2</sup>C port pin name assigned to sensor is different from connected pins on the actual MANUCA DK. See <a href="/starter-kit/extend-the-code/#ReferenceExtSensors">Reference for External Sensor Connectors</a> for the pin names available for external sensor connections. </details></td>
  </tr>
  <tr>
    <td>I am unable to successfully drag-and-drop my compiled binary into the hardware</td>
    <td>Upgrade your ST-Link's firmware as described <a href="https://www.st.com/content/st_com/en/products/development-tools/software-development-tools/stm32-software-development-tools/stm32-programmers/stsw-link007.html">here</a></td>
  </tr>
</table>

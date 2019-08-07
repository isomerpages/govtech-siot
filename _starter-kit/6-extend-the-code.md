---
layout: leftnav-page-content
title: Extend the Code
permalink: /starter-kit/extend-the-code/
breadcrumb: Extend the Code
collection_name: starter-kit
---

Now that you know how to build the MANUCA OS and flash it into your MANUCA DK, you can further extend your system for your use cases.  

An example case-study is [SensorPod](/products/sensorpod/), a product deployed at CETRAN in NTU, which was built on the MANUCA DK.  

We have extended MANUCA OS to include advanced features like physical tamper sensing, hot plug for sensors, bootloader, and over-the-air updating for environmental sensing of the vehicle test track. The possibilities enabled by building on the MANUCA DK are boundless.  

Below are simple guides to help users get started with connecting to external sensors via MANUCA OS.  

## Adding external sensors onto MANUCA

We will demonstrate this feature of the MANUCA DK by using a CO<sub>2</sub> and RH/T Sensor Module, named SCD30. More details can be found on [Sensirion's website for SCD30](https://www.sensirion.com/en/environmental-sensors/carbon-dioxide-sensors-co2/).

### Connection Diagram
![Connection Diagram of SCD30](/images/manuca/extend-the-code/ext_sensor_1_connection_diagram.png)

1. Connect the SCD30 sensor as shown in the diagram above

2. Test the sensor with this image file: [manuca-scd30-i2c-test.bin](/files/manuca-scd30-i2c-test.bin)

    a. If the sensor is active, you should see values of CO<sub>2</sub>, temperature and humidity printed out like this:
    ![Serial Log of SCD30](/images/manuca/extend-the-code/ext_sensor_2_serial_log.png)

3. The Sensor Driver for SCD30 is provided in MANUCA OS, under **sensors-lib**. It is written as a derived class of the base class called SensorType. This is to provide a common interface between the sensors and sensor thread. 

![SCD30 driver directory](/images/manuca/extend-the-code/ext_sensor_3_directory.png)

4. To use the sensor, the sensor driver header file must be included in **sensor_thread.cpp** 

Add `#include "scd30.h"` under all the include statements in sensor thread.

~~~cpp
#include "scd30.h"
~~~

5. Create an instance of the SCD30 class by adding the first two lines before the `while (1)` loop starts in **sensor_thread.cpp**

~~~cpp
Scd30 co2_sensor(i2c_data_pin, i2c_clk_pin, I2C_FREQUENCY);    // creates a SCD30 object
co2_sensor.Enable();    // enable the sensor

while (1)
{
	/* sensor thread loop */
}
~~~

6. Within the `while (1)` loop of sensor thread, look for the line containing  `/* Read other sensor values */`

This is where we will add the process of reading data from the CO<sub>2</sub> sensor.

~~~cpp
while (1)
{
	/* Do other things */

	/* Read other sensor values */
	s_data.clear()    // clear previous data from other sensors
	stat = co2_sensor.GetData(s_data);    // get data from CO2 sensor
	if (stat == SensorType::DATA_NOT_RDY || stat == SensorType::DATA_CRC_ERR)
	{
    	tr_warn("Sensor data error");    // send warning trace if sensor is returning error
	}
    
	if (stat == SensorType::DATA_OK)
	{
    	for (int i=0; i<s_data.size(); i++)    // for each pair element of s_data vector
    	{
        	llp_sensor_mail_t *llp_mail;    
        	llp_mail = llp_sensor_mail_box.calloc();
        	while (llp_mail == NULL)
        	{
            	llp_mail = llp_sensor_mail_box.calloc();
            	tr_warn("Memory full. NULL pointer allocated");
            	ThisThread::sleep_for(500);
        	}      
        	llp_mail->sensor_type = StringToChar(s_data[i].first);    // first of the pair element is data type e.g. CO2
        	llp_mail->value = StringToChar(s_data[i].second);    // second of the pair is data value e.g. 400.00
        	llp_mail->raw_time_stamp = RawRtcTimeNow();
        	llp_sensor_mail_box.put(llp_mail);
    	}
	}
	sent_msg_body = true;

	/* Do other things */
}
~~~


<details>

<summary>Code Explanation</summary>

  This looks very similar to the reading of temperature data from the on-board temperature sensor, but notice the line for `(int i=0; i<s_data.size(); i++)` in the above code block, in which `s_data` is a `std::vector`. A vector is a sequence container which can change its size dynamically, which means that when we on-board more sensors to MANUCA, the system can handle dynamic changes in the number of data points collected --- at least up until the limits of the system memory.

  Therefore, it is important to remember to **clear the `s_data` vector** before reading the data from CO<sub>2</sub> sensor, because it will contain the values from the previous sensor reading. It will also help prevent occurrences of memory leak if there are too many elements in the vector.

  This can be done by adding the line `s_data.clear()` when the data inside the vector is no longer needed.

  The method `GetData(s_data)` obtains the three measure points from the CO<sub>2</sub> sensor and stores it in the vector `s_data`. The measure points available from this sensor are CO<sub>2</sub>, temperature, and humidity.

  The data points can be accessed by index, with `s_data[i].first` as the data type (e.g. CO<sub>2</sub>) and `s_data[i].second` as the data value (e.g. 400.00). Both are stored as string type.

</details>

<br>

7. Before you can see the new measure points being streamed to your DECADA Cloud platform, you will need to configure the new measure points onto DECADA Cloud.
The following steps are similar to **(2) DECADA setup: Creating your Measure Point(s)**. 

	a. Login to your DECADA dashboard

	b. Go to **Model** and select **edit** on the rightmost column. 

	c. Go to **Feature Definitions** and click **Add**

	d. Fill up the fields for your CO<sub>2</sub> measure point. An example looks like this:
  
	![CO2 measure point](/images/manuca/extend-the-code/ext_sensor_4_decada.png)

	e. Repeat the previous step the other measure points; temperature and humidity.

8. Now compile the code and flash the binary file into your MANUCA DK. You should see data updates for the three new measure points on your DECADA Cloud platform when the board is running.

9. For on-boarding other external sensors, you can add in your driver for the sensor and add the reading of your sensor into sensor thread. If you do not have the driver, you can search for open source drivers on [mbed website](https://os.mbed.com/code/).

### Reference for External Sensor Connectors

The below diagram shows how you can connect your own I<sup>2</sup>C/SPI sensors to the MANUCA DK as external sensors.

![External I2C Connectors](/images/manuca/extend-the-code/external_connectors_reference_i2c.png)
![External SPI Connectors](/images/manuca/extend-the-code/external_connectors_reference_spi.png)

<table>
  <tr>
    <th width="50">I<sup>2</sup>C</th>
    <th width="50">SDA</th>
    <th width="200">SCL</th>
    <th width="50">SPI</th>
    <th width="50">MISO</th>
    <th width="50">MOSI</th>
    <th width="50">CLK</th>
    <th>NSS</th>
  </tr>
  <tr>
    <td>1</td>
    <td>PB_9</td>
    <td>PB_6</td>
    <td>1</td>
    <td>PA_6</td>
    <td>PB_5</td>
    <td>PA_5</td>
    <td>PA_4</td>
  </tr>
  <tr>
    <td>2</td>
    <td>PF_0</td>
    <td>PF_1</td>
    <td>2</td>
    <td>PC_2</td>
    <td>PC_3</td>
    <td>PB_10</td>
    <td>PB_12</td>
  </tr>
  <tr>
    <td>4</td>
    <td>PF_15</td>
    <td>PF_14</td>
    <td>4</td>
    <td>PE_5</td>
    <td>PE_6</td>
    <td>PE_12</td>
    <td>PE_4</td>
  </tr>
</table>

You can use these ports by using the mbed PinName enumerator, for example:

~~~cpp
#include "mbed.h"

const PinName i2c_data_pin_1 = PinName::PB_9;
const PinName i2c_clk_pin_1 = PinName::PB_6;
~~~

---
layout: leftnav-page-content
title: Build and Flash Software
permalink: /starter-kit/build-and-flash-sw/
breadcrumb: Build and Flash Software
collection_name: starter-kit
---

# 1. Open the Source Code

<details>
  <summary><font size=4>Mbed Studio</font size></summary>

  1. Open Mbed Studio and login using your Mbed account
  2. Go to File → Open Workspace → \<workspace_directory> (the workspace you have created in [Set up your Software Environment: Pulling the MANUCA OS into your IDE](/starter-kit/set-up-your-software-env/#Workspace))  
  3. On the top left, select **stack-manuca-os** as the Active program
</details>

<br>
<details>
  <summary><font size=4>Visual Studio Code</font size></summary>

  1. In VS Code, go to File → Open Workspace... → \<workspace_directory> (the workspace you have created in [Set up your Software Environment: Pulling the MANUCA OS into your IDE](/starter-kit/set-up-your-software-env/#Workspace))  
</details>

# 2. Set up Important Configurations
### 2.1 Change TLS Configuration

> Due to DECADA Cloud migration works, a temporary security workarond is required.  

Disable SSL Verification by doing the following:
1. In your IDE, go to **mbed-os** → **features** → **netsocket** → **TLSSocketWrapper.cpp**
2. Change line 550 to 

~~~cpp
mbedtls_ssl_conf_authmode(get_ssl_config(), MBEDTLS_SSL_VERIFY_NONE);
~~~  

<a id="InputCredentials"></a>

### 2.2 Input DECADA Credentials into Source Code

1. On your IDE (mbed studio/vs code), open the mbed_app.json file and go to **line 44** (as seen below) to add in your DECADA Credentials (which is obtained from [Set up your Cloud Service: Configuring your Device(s)](/starter-kit/set-up-your-cloud-service/#DecadaCredentials)).

~~~json
"decada-ou-id": {
"help": "Organization Unit ID issued for connecting to DECADAcloud",
"value": "\"enter_organization_unit_id_here\""
},
"decada-access-key": {
"help": "Access key issued for connecting to DECADAcloud application",
"value": "\"enter_access_key_here\""
},
"decada-access-secret": {
"help": "Access secret issued for connecting to DECADAcloud application",
"value": "\"enter_access_secret_here\""
},
"decada-product-key": {
"help": "Product key issued for connecting to DECADAcloud product",
"value": "\"enter_product_key_here\""
},
"decada-product-secret": {
"help": "Product secret issued for connecting to DECADAcloud product",
"value": "\"enter_product_secret_here\""
},
~~~
2. Save your changes.

# 3. Build the binary

<details>
  <summary><font size=4>Mbed Studio</font size></summary>

  1. In Mbed Studio, ensure target is set to **NUCLEO-F767ZI (NUCLEO_F767ZI)**
  2. We use C++11 as the standard for software development. Under Build profile, select **Import custom profiles**, then select **./tools/profiles/mbedstudio_release.json**
  ![mbed-studio](/images/manuca/build-and-flash/mbed_studio_setup_1.png)
  3. Click on the blue hammer icon on the left to build the source code.   
  If your build is successful, you should see something similar to the screenshot below:
  ![mbed-studio](/images/manuca/build-and-flash/mbed_studio_setup_2.png)
  The binary image will be located in `./BUILD/NUCLEO_F767ZI/ARMC6/stack-manuca-os.bin`

</details>

<br>
<details>
  <summary><font size=4>Visual Studio Code</font size></summary>

  2. In VS Code's terminal (or your regular terminal) enter the following line to compile:
  
  ~~~bash
  mbed compile --target NUCLEO_F767ZI --toolchain GCC_ARM --profile ./tools/profiles/tiny_debug.json
  ~~~
  
  ![vscode](/images/manuca/build-and-flash/vscode_setup_1.png)

  If your build was successful, you should see something similar to the screenshot below:
  ![vscode](/images/manuca/build-and-flash/vscode_setup_2.png)
  The binary image will be located in `./BUILD/NUCLEO_F767ZI/GCC_ARM-TINY_DEBUG/stack-manuca-os.bin`

</details>



# 4. Flash the binary into MANUCA DK

1. Locate the binary file in the BUILD folder e.g. `./BUILD/NUCLEO_F767ZI/ARMC6/stack-manuca-os.bin`
2. Using ST-Link V3 programmer, simply drag-and-drop the binary into the hardware folder (similar to copying a file into a USB stick). 

# 5. Configure WiFi SSID, and verify flash success

1. The ST-Link programmer should flash red and green as the binary is being flashed on the MANUCA DK.

2. Open your serial debug program, for example minicom, and press the hardware reset button on the MANUCA DK as shown below. The button is labelled as **H/W RESET**, located on the right of the WIRELESS MODULE slot.

<img class="small" src="/images/manuca/build-and-flash/hardware_reset_button.jpg" alt="hardware-reset">

Hit the spacebar while in your serial debug program, and you should see the Boot Manager screen as shown. Note that the BootManager can only be accessed within the first 5 seconds of a hard reset.

![boot](/images/manuca/build-and-flash/flash_success.png)

3. Enter the passphrase `stackx2019` to login to the Boot Manager.

4. After successfully logging into Boot Manager:
 - Select option (1) to change to your dedicated WiFi SSID
 - Select option (2) to change to your dedicated WiFi Password
 - Select option (-2) to perform a software reset and exit the BootManager. 
 - Select option (-1) if you wish to clear the WiFi SSID, WiFi Password and SSL Certificates, which are all stored in Persistence Storage.

![wifi](/images/manuca/build-and-flash/bootmanager_changewifi.png)

5. The program will automatically register with DECADA Cloud and publish the on-board temperature sensor readings upstream onto your DECADA dashboard.

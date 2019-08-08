---
layout: leftnav-page-content
title: Build and Flash
permalink: /starter-kit/build-and-flash/
breadcrumb: Build and Flash
collection_name: starter-kit
---

# Build the binary

<details>
  <summary>Mbed Studio</summary>

  1. Open Mbed Studio and login using your newly created Mbed account
  2. File → Open Workspace → \<workspace_directory>
  3. On the top left, select `manuca-os-example` as the Active program
  4. Ensure Target is set to **NUCLEO-F767ZI (NUCLEO_F767ZI)**
  5. We use C++11 as the standard for software development. Under Build profile, select **Import custom profiles**, select `./tools/profiles/mbedstudio_release.json`
  ![mbed-studio](/images/manuca/flashing-code/mbed_studio_setup_1.png)
  6. Click on the blue hammer icon on the left to build the source code. The binary image would be located in `./BUILD/NUCLEO_F767ZI/ARMC6/manuca-os-example.bin`
  If your build was successful, you should see something similar to the screenshot below:
  ![mbed-studio](/images/manuca/flashing-code/mbed_studio_setup_2.png)

  **Running Unit Tests (Optional):**
  1. In terminal (at the root of the repository), `mbed test -t GCC_ARM -m NUCLEO_F767ZI --profile ./tools/profiles/tiny_debug.json -n src-*,threads-*`

</details>

<br>
<details>
  <summary>Visual Studio Code</summary>

  1. In VS Code, File → Open Workspace... → \<workspace_directory>
  2. In VS Code's terminal (or your regular terminal), `mbed compile --target NUCLEO_F767ZI --toolchain GCC_ARM --profile ./tools/profiles/tiny_debug.json` to compile
  ![vscode](/images/manuca/flashing-code/vscode_setup_1.png)
  If your build was successful, you should see something similar to the screenshot below:
  ![vscode](/images/manuca/flashing-code/vscode_setup_2.png)
  **Running Unit Tests (Optional):**
  1. In terminal (at the root of the repository), `mbed test -t GCC_ARM -m NUCLEO_F767ZI --profile ./tools/profiles/tiny_debug.json -n src-*,threads-*`

</details>

# Flash the binary into MANUCA DK

1. Locate the binary file in the BUILD folder e.g. `./BUILD/NUCLEO_F767ZI/ARMC6/manuca-os-example.bin`
2. Using ST-Link V3 programmer, simply drag-and-drop the binary into the hardware folder (similar to copying a file into a USB stick). 

# Configure WiFi SSID, and verify flash success

1. The ST-Link programmer should flash red and green as the binary is being flashed on the MANUCA DK.

2. Open your serial debug program, for example minicom, and press the hardware reset button on the MANUCA DK. Hit the spacebar while in your serial debug program, and you should see the Boot Manager screen as shown. Note that the BootManager can only be accessed within the first 5 seconds of a hard reset.

![boot](/images/manuca/flashing-code/flash_success.png)

3. Enter the passphrase `stackx2019` to login to the Boot Manager.

4. After successfully logging into Boot Manager, select option (1) to change to your dedicated WiFi SSID, and option (2) to change to your dedicated WiFi Password. Select option (-2) to perform a software reset and exit the BootManager. Option (-1) currently empties the WiFi SSID, WiFi Password and SSL Certificates, which are all stored in Persistence Storage, and should be used as a need-to basis.

![wifi](/images/manuca/flashing-code/bootmanager_changewifi.png)

5. The program will automatically register with DECADA Cloud and publish the on-board temperature sensor readings upstream onto your DECADA dashboard.

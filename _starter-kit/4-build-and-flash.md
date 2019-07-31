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
  3. On the top left, select `stack-riots-os-example` as the Active program
  4. Ensure Target is set to **NUCLEO-F767ZI (NUCLEO_F767ZI)**
  5. We use C++11 as the standard for software development. Under Build profile, select **Import custom profiles**, select `./tools/profiles/mbedstudio_release.json`
  ![mbed-studio](/images/riots-dk/flashing-code/mbed_studio_setup_1.png)
  6. Click on the blue hammer icon on the left to build the source code. The binary image would be located in `./BUILD/NUCLEO_F767ZI/ARMC6/stack_riots-os-example.bin`
  If your build was successful, you should see something similar to the screenshot below:
  ![mbed-studio](/images/riots-dk/flashing-code/mbed_studio_setup_2.png)

  **Running Unit Tests (Optional):**
  1. In terminal (at the root of the repository), `mbed test -t GCC_ARM -m NUCLEO_F767ZI --profile ./tools/profiles/tiny_debug.json -n src-*,threads-*`

</details>

<br>
<details>
  <summary>Visual Studio Code</summary>

  1. In VS Code, File → Open Workspace... → \<workspace_directory>
  2. In VS Code's terminal (or your regular terminal), `mbed compile --target NUCLEO_F767ZI --toolchain GCC_ARM --profile ./tools/profiles/tiny_debug.json` to compile
  ![vscode](/images/riots-dk/flashing-code/vscode_setup_1.png)
  If your build was successful, you should see something similar to the screenshot below:
  ![vscode](/images/riots-dk/flashing-code/vscode_setup_2.png)
  **Running Unit Tests (Optional):**
  1. In terminal (at the root of the repository), `mbed test -t GCC_ARM -m NUCLEO_F767ZI --profile ./tools/profiles/tiny_debug.json -n src-*,threads-*`

</details>

# Flash the binary into RIOTS Board

1. Locate the binary file in the BUILD folder e.g. `./BUILD/NUCLEO_F767ZI/ARMC6/stack_riots-os-example.bin`
2. Using ST-Link V3 programmer, simply drag-and-drop the binary into the hardware folder (similar to copying a file into a USB stick). 

# Verify flash success

1. The ST-Link programmer should flash red and green as the binary is being flashed on the RIOTS Board.

2. Open your serial debug program and press the hardware reset button on your board. Then press space in your serial debug program. You should see the boot manager screen 

![boot](/images/riots-dk/flashing-code/flash_success.png)

3. Enter the passphrase `stackx2019` 

4. The program should be able to register with DECADA and send the on-board temperature sensor readings upstream onto your DECADA dashboard

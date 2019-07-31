---
layout: leftnav-page-content
title: Set up your Hardware
permalink: /tech-stack/riots-dk/set-up-your-hardware/
breadcrumb: Set up your Hardware
collection_name: starter-kit
---

# Set up your Hardware
## Wiring up the RIOTS Board
1. Connect the **ESP32 WiFi Module** onto the **WIRELESS MODULE** port on the board

![step 1](/images/riots-dk/riots-board-setup/riots_setup_1_wifi.jpg)

2. Connect the **TTL-USB Cable** to the **SERIAL DEBUG** port, with black wire aligned to the GND pin

![step 2](/images/riots-dk/riots-board-setup/riots_setup_2_ttl.jpg)

3. Connect the **ST-LINK programmer** cable to the **JTAG** pins, with red wire at the bottom

![step 3](/images/riots-dk/riots-board-setup/riots_setup_3_jtag.jpg)

4. Your board set up should look like this:

![step 4](/images/riots-dk/riots-board-setup/riots_setup_4.jpg)

5. Connect the USB side of the **TTL-USB Cable** and **ST-LINK programmer** to your computer. The board should light up.

## Setting up your RIOTS Board Serial Debug Program
Proceed with the following steps, depending on which OS your computer is running on.
<details markdown="1">
  
  <summary markdown='span'>Linux</summary>
  
  1. Find out which serial port your **TTL-USB Cable** is connected to by disconnecting your **TTL-USB Cable**, then entering `dmesg | grep tty` into Terminal.

  Reconnect your TTL-USB Cable and reenter the `dmesg | grep tty` command.

  You should see something like this:

  ~~~bash
  ~$ dmesg | grep tty
  [12213.614731] usb 1-3: FTDI USB Serial Device converter now attached to ttyUSB0
  ~~~

  Take note of the name of the Serial Device – in the above example, it is ttyUSB0.

  2. Install minicom by entering `sudo apt-get install minicom` into Terminal. This step will install minicom if not installed yet.

  3. Configure minicom by entering `sudo minicom -s` into Terminal. You should see this configuration window:
  ![linux-minicom-setup](/images/riots-dk/riots-board-setup/linux_debug_setup_1.jpg)
  Use arrow keys/enter to navigate the menu.

  4. Go to **Serial port setup**.
  ![linux-minicom-setup](/images/riots-dk/riots-board-setup/linux_debug_setup_2.jpg)
  There are three things you need to do:

  - Change Serial Device to the name of the port that the TTL-USB Cable is connected to. You can change your Serial Device by entering **A**, then editing the name, and press **enter**.

  - Change the Baud Rate to 115200 by entering **E**, then entering **E** again, and press **enter**.

  - Switch off Hardware Flow Control by entering **F**, and press **enter**.

  Leave the Serial port setup by pressing **enter**.

  5. Go to **Save setup as dfl** and **enter**. This will save your configuration as default.

  6. Go to **Exit** and **enter**. This will bring you to the minicom application in Terminal.
  ![linux-minicom-setup](/images/riots-dk/riots-board-setup/linux_debug_setup_3.png)
  You should see `Welcome to minicom` and the Port should reflect the name of your TTL-to-USB cable port.

  Now your Serial Debugging tool for Linux has been set up successfully.

  You can run minicom again by typing `sudo minicom` into the Terminal.

</details>

<br>
<details markdown="1">
  
  <summary markdown='span'>MacOS</summary>
  
  1. Find out which serial port your **TTL-USB Cable** is connected to by disconnecting your **TTL-USB Cable**, then entering `ls /dev/tty*` into Terminal.

  Reconnect your TTL-USB Cable and reenter the `ls /dev/tty*` command. You should see an extra port displayed, `/dev/tty.usbserial-FT9J98X2`

  2. Install minicom using the following commands:
  - `ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" < /dev/null 2> /dev/null`
  - `brew install minicom`

  3. Configure minicom by entering `sudo minicom -s` into Terminal. You should see this configuration window:
  ![macos-minicom-setup](/images/riots-dk/riots-board-setup/macos_debug_setup_1.png)
  Use arrow keys/enter to navigate the menu.

  4. Go to **Serial port setup**.
  ![macos-minicom-setup](/images/riots-dk/riots-board-setup/macos_debug_setup_2.png)
  There are three things you need to do:

  - Change Serial Device to the name of the port that the TTL-USB Cable is connected to. You can change your Serial Device by entering **A**, then editing the name, and press **enter**.

  - Change the Baud Rate to 115200 by entering **E**, then entering **E** again, and press **enter**.

  - Switch off Hardware Flow Control by entering **F**, and press **enter**.

  Leave the Serial port setup by pressing **enter**.

  5. Go to **Save setup as dfl** and **enter**. This will save your configuration as default.

  6. Go to **Exit** and **enter**. This will bring you to the minicom application in Terminal.
  ![macos-minicom-setup](/images/riots-dk/riots-board-setup/macos_debug_setup_3.png)
  You should see a message similar to the above image and the Port should reflect the name of your TTL-to-USB cable port.

  Now your Serial Debugging tool for Linux has been set up successfully.

  You can run minicom again by typing `sudo minicom` into the Terminal.

</details>

<br>
<details markdown="1">
  
  <summary markdown='span'>Windows</summary>
  
  1. Download [Tera Term](https://osdn.net/projects/ttssh2/releases/) for Windows. This tutorial is for Tera Term, though you can use PuTTY as well.

  2. Run the Tera Term `.exe` file and install the software.

  3. A "New connection" window will pop up. Select the **Serial** option if available. If not, click cancel.
  ![windows-teraterm-setup](/images/riots-dk/riots-board-setup/windows_debug_setup_1.PNG)

  4. Go to **Setup > Serial port...**
  You should see something like this:
  ![windows-teraterm-setup](/images/riots-dk/riots-board-setup/windows_debug_setup_2.PNG)

  To find out what port your TTL-USB Cable is connected to:

  - Disconnect the cable and close this window.
  - Reopen the window and click on the **Port** dropdown list. Note the ports displayed.
  - Reconnect your cable, and reopen the Serial port setup window. The newly connected TTL-USB Cable will show up on the dropdown list.
  Change **Port** to your TTL-USB Cable port, and the **Baud rate** to **115200**. Click OK.

</details>

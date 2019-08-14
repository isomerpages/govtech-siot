---
layout: leftnav-page-content
title: Set up your Software Environment
permalink: /starter-kit/set-up-your-software-env/
breadcrumb: Set up your Software Envinronment
collection_name: starter-kit  
---

## Setting up the Integrated Development (IDE) Environment

Proceed with the following steps, depending on which Operating System your development machine is running on.

**Available Integrated Development Environments (IDEs):**
1. Mbed Studio *(Recommended)* -  MacOS and Windows
2. Visual Studio Code (VS Code) - Ubuntu Setup Included Only

**Development Machine Pre-requisite(s):**
1. [Git](https://git-scm.com/downloads) installed
___
<br>

<details>
  <summary><font size=4>Mbed Studio Setup</font size></summary>

  1. Create an Mbed Account at <https://os.mbed.com/account/signup/> (This account is required to use Mbed Studio IDE)
  2. Download Mbed Studio from <https://os.mbed.com/studio/>
  3. Install Mbed Studio

</details>

<br>
<details>
  <summary><font size=4>Visual Studio Code Setup</font size></summary>

  1. Download VS Code for Ubuntu at <https://code.visualstudio.com/download>
  2. Install VS Code
  3. Install Python by entering `sudo apt-get install python2.7` in terminal.
  4. Install Pip by entering `sudo apt-get install python-pip` in terminal. 
  5. Download gcc-arm-embedded-6-2017-q2 Toolchain; download the toolchain **6-2017-q2** from [here](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads), and decompress the folder
  6. Install mbed client by entering `sudo pip install mbed-cli`  
  Enter `mbed help` to check if mbed-cli is properly installed.  
  7. Add gcc-arm toolchain to mbed-cli compiler by entering `mbed config -G GCC_ARM_PATH <path to GCC_ARM bin\>   # path example: ~/gcc-arm/gcc-arm-none-eabi-6-2017-q2-update/bin/`  
  *Replace `<path to GCC_ARM bin\>` with the file path of the downloaded GCC ARM toolchain.*  
  Enter `mbed config --list` to show the toolchain attached to mbed-cli compiler.  
  8. On VS Code, install the following packages under Extensions (ctrl + shift + x)  
    a. C/C++ By Microsoft  
    b. Cortex-Debug by marus25  
    c. ESLint by Dirk Baeumer  
    d. Python by Microsoft  

</details>

<a id="Workspace"></a>

## Pulling the MANUCA OS Repository into your IDE
1. Create a folder that would be your mbed work space by entering `mkdir <workspace_directory>` in terminal. *Replace `<workspace_directory>` with your desired workspace name.*
2. Go into the workspace by entering `cd <workspace_directory>` in terminal.
2. Enter `git init` in terminal to initialize a git work space
3. Then, enter `git clone --recurse-submodules https://github.com/GovTechSIOT/stack-manuca-os.git` to download pull the remote repository to your development machine.


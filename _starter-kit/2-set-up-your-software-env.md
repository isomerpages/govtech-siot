---
layout: leftnav-page-content
title: Set up your Software Environment
permalink: /starter-kit/set-up-your-software-env/
breadcrumb: Set up your Software Envinronment
collection_name: starter-kit  
---

## 1. Setting up the Integrated Development Environment (IDE)

Proceed with the following steps, depending on which Operating System your development machine is running on.

**Available Integrated Development Environments (IDEs):**
1. Mbed Studio *(Recommended)* -  MacOS and Windows
2. Visual Studio Code (VS Code) - Ubuntu Setup Included Only

<br>

<details>
  <summary>Mbed Studio Setup</summary>

  1. Create an Mbed Account at <https://os.mbed.com/account/signup/> (This account is required to use Mbed Studio IDE)
  2. Download Mbed Studio from <https://os.mbed.com/studio/>
  3. Install Mbed Studio

</details>

<br>
<details>
  <summary>Visual Studio Code Setup</summary>

  1. Download VS Code for Ubuntu at <https://code.visualstudio.com/download>
  2. Install VS Code
  3. Install Python by entering the following line in Terminal:
      ~~~bash
      sudo apt-get install python2.7
      ~~~  
  4. Install Pip by entering the following line in Terminal:
      ~~~bash
      sudo apt-get install python-pip
      ~~~  
  5. Download gcc-arm-embedded-6-2017-q2 Toolchain; download the toolchain **6-2017-q2** from [here](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads), and decompress the folder
  6. Install mbed client by entering the following line in Terminal:
      ~~~bash
      sudo pip install mbed-cli
      ~~~  
      Enter the following line in Terminal to check if mbed-cli is properly installed.  
      ~~~bash
      mbed help
      ~~~  
  7. Add gcc-arm toolchain to mbed-cli compiler by entering the following line in Terminal:
      ~~~bash
      mbed config -G GCC_ARM_PATH <path to GCC_ARM bin\>   # path example: ~/gcc-arm/gcc-arm-none-eabi-6-2017-q2-update/bin/
      ~~~    
      *Replace `<path to GCC_ARM bin\>` with the file path of the downloaded GCC ARM toolchain.*  
      Enter the following line in Terminal to show the toolchain attached to mbed-cli compiler.  
      ~~~bash
      mbed config --list
      ~~~  
  8. On VS Code, install the following packages under Extensions (ctrl + shift + x)  
      a. C/C++ By Microsoft  
      b. Cortex-Debug by marus25  
      c. ESLint by Dirk Baeumer  
      d. Python by Microsoft  

</details>

___
<a id="Workspace"></a>

## 2. Pulling the MANUCA OS Repository into your IDE

**Development Machine Pre-requisite(s):**  
  \> [Git](https://git-scm.com/downloads) installed

1. Create a folder that would be your mbed work space by entering the following line in terminal. *Replace `<workspace_directory>` with your desired workspace name.*
    ~~~bash
    mkdir <workspace_directory>
    ~~~  
2. Go into the workspace by entering the following line in Terminal:
    ~~~bash
    cd <workspace_directory>
    ~~~ 
2. Enter the following line in Terminal to initialize a git work space
    ~~~bash
    git init
    ~~~  
3. Then, enter the following line to download pull the remote repository to your development machine.
    ~~~bash
    git clone --recurse-submodules https://github.com/GovTechSIOT/stack-manuca-os.git
    ~~~  
4. For **non-Mbed Studio users**, install the required python modules by running the following code lines in Terminal:
    ~~~bash
    cd stack-manuca-os/mbed-os/
    sudo pip install -r requirements.txt
    ~~~

___
<a id="SerialDebug"></a>

## 3. Installing your Serial Debug Program
This program will allow you to read the serial debug output from the MANUCA DK. Proceed with the following steps to install your serial debug program, depending on which OS your computer is running on.
<details>
  
  <summary>Linux</summary>

  1. Install minicom by entering the following line into Terminal. This step will install minicom if not installed yet.
  ~~~bash
  sudo apt-get install minicom
  ~~~  


</details>

<br>
<details>
  
  <summary>MacOS</summary>

  1. Install minicom using the following commands in Terminal:  
  ~~~bash
  ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" < /dev/null 2> /dev/null  
  brew install minicom  
  ~~~  


</details>

<br>
<details>
  
  <summary>Windows</summary>
  
  1. Download [Tera Term](https://osdn.net/projects/ttssh2/releases/) for Windows.

  2. Run the Tera Term `.exe` file and install the software.

</details>
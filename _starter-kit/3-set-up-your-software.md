---
layout: leftnav-page-content
title: Set up your Software
permalink: /starter-kit/set-up-your-software/
breadcrumb: Set up your Software
collection_name: starter-kit  
---

# Set up your Software
## Setting up the Integrated Development (IDE) Environment

**Available Integrated Development Environments (IDEs):**
1. Mbed Studio *(Recommended)* -  MacOS and Windows
2. Visual Studio Code - Ubuntu Setup Included Only

**Development Machine Pre-requisite(s):**
1. Git installed

<details>
  <summary>Mbed Studio Setup</summary>

  1. Create an Mbed Account at <https://os.mbed.com/account/signup/> (This account is required to use Mbed Studio IDE)
  2. Download Mbed Studio from <https://os.mbed.com/studio/>
  3. Install Mbed Studio

</details>

<details>
  <summary>Visual Studio Code Setup</summary>

  1. Download VS Code for Ubuntu at <https://code.visualstudio.com/download>
  2. Install VS Code
  3. Install Python
    a. In terminal, `sudo apt-get install python2.7`
  4. Install Pip
    a. In terminal, sudo apt-get install python-pip 
  5. Download gcc-arm-embedded-6-2017-q2 Toolchain
    a. Download 6-2017-q2 from [here](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads), and decompress the folder
  6. In terminal, `sudo pip install mbed-cli`
    a. In terminal, `mbed help` to check if mbed-cli is properly installed
  7. Add gcc-arm tool chain to mbed-cli compiler
    a. In terminal, `mbed config -G GCC_ARM_PATH <path to GCC_ARM bin\>   # path example: ~/gcc-arm/gcc-arm-none-eabi-6-2017-q2-update/bin/`
    b. In terminal, `mbed config --list` to show the toolchain attached to mbed-cli compiler

</details>

## Pulling the RIOTS Operating System Repository into your IDE

<details>
  <summary>Mbed Studio Setup</summary>

  1. Create a folder that would be your mbed work space. `cd <workspace_directory>`
  2. In terminal, `git init` to initialize a git work space
  3. In terminal, `git clone --recurse-submodules <public_github_url>)`
  4. In terminal, `git submodule update --init --recursive`

</details>

<details>
  <summary>Visual Studio Code Setup</summary>

  1. Create a folder that would be your mbed work space. `cd <workspace_directory>`
  2. In terminal, `git init` to initialize a git work space
  3. In terminal, `git clone --recurse-submodules <public_github_url>)`
  4. Open VS Code, and install the following packages under Extensions (ctrl + shift + x)
    a. C/C++ By Microsoft
    b. Cortex-Debug by marus25
    c. ESLint by Dirk Baeumer
    d. Python by Microsoft

</details>

## Input DECADA Credentials into Source Code

Go to mbed_app.json **line 44** to add in your DECADA Credentials as shown below.

~~~json
"decada-ou-id": {
"help": "Organization Unit ID issued for connecting to DECADAcloud",
"value": "\"<insert_ou_id>\""
},
"decada-access-key": {
"help": "Access key issued for connecting to DECADAcloud application",
"value": "\"<insert_decada_access_key>\""
},
"decada-access-secret": {
"help": "Access secret issued for connecting to DECADAcloud application",
"value": "\"<insert_decada_access_secret>\""
},
"decada-product-key": {
"help": "Product key issued for connecting to DECADAcloud product",
"value": "\"<insert_product_key>\""
},
"decada-product-secret": {
"help": "Product secret issued for connecting to DECADAcloud product",
"value": "\"<insert_product_secret>\""
},
~~~

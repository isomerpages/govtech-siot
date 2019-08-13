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
  >* In terminal, `sudo apt-get install python2.7`
  4. Install Pip
  >* In terminal, sudo apt-get install python-pip 
  5. Download gcc-arm-embedded-6-2017-q2 Toolchain
  >* Download 6-2017-q2 from [here](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads), and decompress the folder
  6. In terminal, `sudo pip install mbed-cli`
  >* In terminal, `mbed help` to check if mbed-cli is properly installed
  7. Add gcc-arm tool chain to mbed-cli compiler
  >* In terminal, `mbed config -G GCC_ARM_PATH <path to GCC_ARM bin\>   # path example: ~/gcc-arm/gcc-arm-none-eabi-6-2017-q2-update/bin/`
  >* In terminal, `mbed config --list` to show the toolchain attached to mbed-cli compiler

</details>

## Pulling the MANUCA OS Repository into your IDE

<details>
  <summary>Mbed Studio Setup</summary>

  1. Create a folder that would be your mbed work space. `cd <workspace_directory>`
  2. In terminal, `git init` to initialize a git work space
  3. In terminal, `git clone --recurse-submodules https://github.com/GovTechSIOT/stack-manuca-os.git`
  4. In terminal, `git submodule update --init --recursive`

</details>

<details>
  <summary>Visual Studio Code Setup</summary>

  1. Create a folder that would be your mbed work space. `cd <workspace_directory>`
  2. In terminal, `git init` to initialize a git work space
  3. In terminal, `git clone --recurse-submodules https://github.com/GovTechSIOT/stack-manuca-os.git`
  4. Open VS Code, and install the following packages under Extensions (ctrl + shift + x)
  >* C/C++ By Microsoft
  >* Cortex-Debug by marus25
  >* ESLint by Dirk Baeumer
  >* Python by Microsoft

</details>

## Important Configurations

### Change TLS Configuration

> Due to DECADA Cloud migration works, a temporary security workarond is required.  

Disable SSL Verification by changing mbed-os/features/netsocket/TLSSocketWrapper.cpp line 550 to `mbedtls_ssl_conf_authmode(get_ssl_config(), MBEDTLS_SSL_VERIFY_NONE);`


### Input DECADA Credentials into Source Code

Go to mbed_app.json **line 44** to add in your DECADA Credentials as shown below.

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

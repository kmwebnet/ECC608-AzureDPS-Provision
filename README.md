# ECC608-Azure-DPS-provisioning

This registers device certificate to Azure IoT DPS service and prepares for connecting Azure IoT Hub.

# Requirements

  Platformio with VS Code environment.
  install "Espressif 32" platform definition on Platformio  
  Prior to compile this project, you must copy "cert_chain.c", which is made by privious step [ECC608-Provision](https://github.com/kmwebnet/ECC608-Provision) to "src" folder.  

  you need to modify the definition and variables in main.c as follows:  
  ```
// your SSID and PASS
#define EXAMPLE_WIFI_SSID ""
#define EXAMPLE_WIFI_PASS ""


// URL and ID scope which are pointed out by your Azure IoT DPS service console.
static const char* global_prov_uri = "";
static const char* id_scope = "";
  ```


# Environment reference
  
  Espressif ESP32-DevkitC
  this project initialize both of I2C 0,1 port, and the device on I2C port 0 is BME280 Ambient sensor.  
  pin assined as below:


      I2C 0 SDA GPIO_NUM_18
      I2C 0 SCL GPIO_NUM_19

      I2C 1 SDA GPIO_NUM_21
      I2C 1 SCL GPIO_NUM_22
          
  Microchip ATECC608A(on I2C port 1)

# Usage

Once you do git clone, you need to execute "git submodule update --init --recursive"  
you need to change a serial port number which actually connected to ESP32 in platformio.ini.

# Run this project

At first, you need to create self-signed CA chain by using python scripts step-by-step in "scripts" folder for test purpose.  
1, create root-ca.crt and signer-ca.crt  
2, convert their extension from .crt to .pem to upload Azure IoT DPS certificate registration.  
3, you need to verify them follow the steps described by Azure IoT DPS.

If you don't make sense this topic, please step back to [ECC608-Provision](https://github.com/kmwebnet/ECC608-Provision).  

# Result

If you run this project with success, you can find the results on serial console as follows:

```
....
Registering testcorp.azure-devices.net ...
Azure IoT URL provisioning complete.
device sn provisioning complete.

```

# License

This software is released under the MIT License, see LICENSE.

Connect N27 device to your Azure IoT Central Application
===

---
# Table of Contents

-   [Introduction](#Introduction)
-   [Prerequisites](#Prerequisites)
-   [Create Azure IoT Central application](#Create_AICA)
-   [Device Connection Details](#DeviceConnectionDetails)
-   [Prepare the Device](#preparethedevice)
-   [Integration with IoT Central](#IntegrationwithIoTCentral)
-   [Additional Links](#AdditionalLinks)

<a name="Introduction"></a>

# Introduction 

**About this document**

N27 is an NB-IoT/eMTC/GPRS module specially designed for M2M and IoT applications. Adopting the 3GPP Rel. 14 LTE technology, it delivers 1119 Kbps downlink and 588 Kbps uplink data rates.N27 supports Qualcomm® location Suite Gen9 VT (GPS, GLONASS, BDS, Galileo and QZSS). The integrated GNSS greatly simplifies product design, and provides quicker, more accurate and more reliable position fix. 
      N27 integrates industrial UART interfaces and supports various network protocols, such as CoAP, UDP, TCP, MQTT, etc. With low power consumption, ultra wide operating temperature range, excellent RF performance, industry-standard interfaces and abundant functionalities (USB-to-serial drivers for Windows 7/8/8.1/10, Linux, Android), N27 is the optimal option for energy metering, telematics, smart city, tracking and environmental monitoring etc.

<a name="Prerequisites"></a>
# Prerequisites

You should have the following items ready before beginning the process: 

-   [Azure Account](https://portal.azure.com)
-   [Azure IoT Hub Instance](https://docs.microsoft.com/en-us/azure/iot-hub/about-iot-hub)
-   [Azure IoT Hub Device Provisioning Service](https://docs.microsoft.com/en-us/azure/iot-dps/about-iot-dps)
-   Provide Network connectivity (LTE) supported by the device
-  Its mandatory that the device code/software image is preinstalled in device to enable Plug and Play

_Create Azure IoT Central application_
You should createan Azure IoT Centralapplication at first according to the following steps:
Navigate to the [Azure IoT Central Build](https://aka.ms/iotcentral) site. Then sign in with a Microsoft personal, work, or school account.
Navigate to Build page, choose Connectedlogisticsand click Create app.
![Image text](https://github.com/shea666/N27_PNP/blob/master/picture/%E6%8D%95%E8%8E%B7.PNG)

Enter your own friendly application name.A unique Application URL based on the application name will be generated. You can use this URL to access your application.
![Image text](https://github.com/shea666/N27_PNP/blob/master/picture/%E6%8D%95%E8%8E%B71.PNG)

Review other Terms and Conditionsandselect Create at the bottom of the page.
_Device Connection Details_

This section describes how to add a device to your IoT Central application and get device connection details. Theses connection details will be used when Integration with IoT Central
Navigate to IoT Central application page, the default page is on Dashboard.To add a new device template, select +New on the Device Templates page.
![Image text](https://github.com/shea666/N27_PNP/blob/master/picture/%E6%8D%95%E8%8E%B72.PNG)
<a name="preparethedevice"></a>
# Prepare the Device.

**Hardware Environmental setup**

-   Please include how to setup and connect the device. Include external links for any software required for Hardware setup

**Software Environmental Setup**

-   Please include the prerequisite required to setup the device. Please use external links when possible pointing to your own page with device preparation steps.

### Option 1

-   If device code not pre-installed on your device, please provide us the URL of your repository.

-   Specify the steps on how to flash the image on device and provide required URL's to download the flash-able image and necessary tools. **Please add the screenshots where ever necessary.**

### Option 2

-   For the partners using the Microsoft PnP SDK samples

-   If recompilation of code is not required, please provide config file here, such that it can be copied in the C sdk environment to enable Plug and Play on device

-   Please include instruction on how to compile the code, tools and environment required to compile etc. **Please add the screenshots where ever necessary**

### Option 3

-   If recompilation is required, then please provide the link for GitHub repo for anyone to modify.

-   Please include instruction on how to compile the code , tools and environment required to compile etc. **Please add the screenshots where ever necessary**

<a name="IntegrationwithIoTCentral"></a>
# Integration with IoT Central

-   Include the steps on how to connect the Device to IoT Central
-   Include the steps by step process on how the devices use the DPS configuration (ID Scope, SAS Key, Device ID, Registration ID) to provision to IoT Central.
-   Include screenshots and comments on how IoT Central shows/visualize telemetry coming from your PnP device.
-   Use this [Get started]( https://aka.ms/AA66he8) doc as an example

<a name="AdditionalLinks"></a>
# Additional Links

Please refer to the below link for additional information for Plug and Play 

-    [Blog](https://azure.microsoft.com/en-us/blog/iot-plug-and-play-is-now-available-in-preview/)
-    [FAQ](TBD) 
-    [Plug and Play C SDK](https://github.com/Azure/azure-iot-sdk-c/tree/public-preview) 
-    [Plug and Play Node SDK](https://github.com/Azure/azure-iot-sdk-node/tree/digitaltwins-preview)
-    [Plug and Play Definitions](https://github.com/Azure/IoTPlugandPlay)

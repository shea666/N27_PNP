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

Choose IoT Device from the list of custom device templates, select Next: Customize, then select Next: Review, and then select Create. Enter Environmental Sensor as the name of your device template.
Download ‘EnvironmentalSensorInline.capabilitymodel.json’ file that contains the [IoT Plug and Play](https://docs.microsoft.com/en-us/azure/iot-pnp/overview-iot-plug-and-play)
device capability model. 
After you download the file, open it in a text editor, and replace the two instances of <YOUR_COMPANY_NAME_HERE> with ‘neoway’. 
Note: only the characters a-z, A-Z, 0-9, and underscore permit.
Back toDevice templates > Environmental Sensor page. Choose Import Capability Model to create a new device capability model from a JSON file. Navigate to the folder where you saved the EnvironmentalSensorInline.capabilitymodel.json file on your local machine. Select the file and then select Open. 
In order to interact with your device, you should create a view to display relevant information about your device.

![Image text](https://github.com/shea666/N27_PNP/blob/master/picture/%E6%8D%95%E8%8E%B73.PNG)

Select Views and then Visualizing the Device.
select Humidity and Temperature, and then select Combine. select the Change Visualization button at the top of the tile if you want to view this chart in a different format.
Select Save to save your view.
Publish device template
After create device template, Select Publish button at the right top of the tile

![Image text](https://github.com/shea666/N27_PNP/blob/master/picture/%E6%8D%95%E8%8E%B74.PNG)

On the Publish a Device Template dialog, choose Publish. After a device template is published, it's visible on the Devices page and to the operator.
Navigation to Devices and select the device template you create just now. Then select New

![Image text](https://github.com/shea666/N27_PNP/blob/master/picture/%E6%8D%95%E8%8E%B75.PNG)

Use the suggested Device ID or enter your own lowercase Device ID. You can also enter a name for your new device. Select Create.
Select the device and you will see details about it, Select the Connect button, you can get the device connection details. Record the ID Scope, Device ID and Primary key.

![Image text](https://github.com/shea666/N27_PNP/blob/master/picture/%E6%8D%95%E8%8E%B76.PNG)

<a name="preparethedevice"></a>
# Prepare the Device.

**Hardware Environmental setup**

Materials prepared: N27 EVB device, debug tool,5V/2A power adapter，Antenna, SIM card, USB cable

Connected N27 EVB device with USB cable
Use the 5V/2A power adapter to power the module
Connect the USB cable, power adapter, antenna, SIM card, etc. as shown in the picture

**Software Environmental Setup**

Compilation Environment 
OS: Windowns
Compiler: Snapdragon-llvm-4.0.3-windows64.zip .
Preparation:
This section describes how to use a device capability model to create an IoT Plug and Play Preview device.

Firstly, you should install Azure IoT tools on Windows 10

Use the following steps to install the [Azure IoT Tools for VS Code](https://marketplace.visualstudio.com/items?itemName=vsciot-vscode.azure-iot-tools) extension pack:
In VS Code, select the Extensions tab.
Search for Azure IoT Tools.
Select Install.

Then, Author your model on VS Code:

Create a pnp_app directory in your local drive. Download the [Device Capability Model](https://github.com/Azure/opendigitaltwins-dtdl/blob/9004219bff1e958b7cd6ff2a52209f4b7ae19396/samples/SampleDevice.capabilitymodel.json) and [Interface Samplefiles](https://github.com/Azure/opendigitaltwins-dtdl/blob/9004219bff1e958b7cd6ff2a52209f4b7ae19396/samples/EnvironmentalSensor.interface.json) to the pnp_app folder.

Note: the DCM file is the same with DCM file that used to create device template.


Open pnp_app folder with VS Code. In the files you downloaded, replace <YOUR_COMPANY_NAME_HERE> in the @id and schema fields with your own name.
Note: Only characters a-z, A-Z, 0-9, and underscore permitted).

Generate the C code stub

With the folder with DCM files open, use Ctrl+Shift+P to open the command palette, enter IoT Plug and Play, and select Generate Device Code Stub.

Enter the project name sample_device, it will be the name of your device application.
Choose Via DPS (Device Provisioning Service) symmetric key as connection method.
Choose ANSI C as your language.
Choose CMake Project on Linux as your project template.
Choose Via Source Code as the way to include the SDK.

VS Code opens a new window with generated device code stub files.


Get Azure IoT device SDK for C on Ubuntu

Open a command prompt. Execute the following command to clone the [Azure IoT C SDK](https://github.com/Azure/azure-iot-sdk-c) GitHub repository:
	git clone https://github.com/Azure/azure-iot-sdk-c --recursive -b public-preview


Build the code
The Microsoft Azure SDK porting layer package includes the following items from Qualcomm.  Qualcomm porting library (azure_sdk_port.lib). Sample LLVM build script to build the Microsoft Azure SDK library  (build_azure_sdk_lib_llvm.bat)  Sample LLVM build script to build the Azure application by linking to the Microsoft  Azure SDK and Qualcomm porting libraries (build_azure_sdk_app_llvm.bat).
Here is a sample setup for compiling the sample application:

![Image text](https://github.com/shea666/N27_PNP/blob/master/picture/%E6%8D%95%E8%8E%B77.PNG)

### Option 1

Copy the cloned Microsoft Azure SDK IoT C files to the Azure_SDK\azure-iot-sdk-c  folder.

### Option 2

Download the LTE IoT SDK package from the Qualcomm CreatePoint website.

### Option 3

Set up the environment for using LLVM and QFLOG. Also, a reference LLVM DAM module preamble is present in the package that is needed to build the application binary.

### Option 4

Copy the common folder of LTE IoT SDK package to the same level as the Microsoft Azure SDK.

![Image text](https://github.com/shea666/N27_PNP/blob/master/picture/%E6%8D%95%E8%8E%B78.PNG)

### Option 5

![Image text](https://github.com/shea666/N27_PNP/blob/master/picture/%E6%8D%95%E8%8E%B79.PNG)

### Option 6

Update LLVMROOT path in build_azure_sdk_lib_llvm.bat and build_azure_sdk_lib_llvm.bat build script files to point to the LLVM folder location. Ensure that the scripts point to the header files in the common folder.

### Option 7

Run the build_azure_sdk_lib_llvm.sh build script under Azure_SDK/build to generate the Microsoft Azure SDK IoT C library.
build_azure_sdk_lib_llvm.bat.

### Option 8

Run the build_azure_sdk_app_llvm.bat build script under Azure_SDK/build to compile the application and link to both the Azure Qualcomm platform library (azure_sdk_port.lib) and Microsoft Azure SDK IoT C library (azure_sdk.lib) to generate binary file under Azure_SDK/build/bin.
build_azure_sdk_app_llvm.bat.

**Test**

### Option 1

Install binary file to the device
Use the QFLOG tool to push the bin files to the devices, and then restart the device.

![Image text](https://github.com/shea666/N27_PNP/blob/master/picture/%E6%8D%95%E8%8E%B710.PNG)

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

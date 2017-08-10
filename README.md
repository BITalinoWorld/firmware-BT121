# firmware-BT121
The BT121 firmware is available in source code and in a prebuilt image ready to be programmed in a device.
# Programming the firmware
The preferred method of programming the BT121 is by using the Bluegiga DFU through the UART host interface.
This can be done through various methods, however here we follow the one that uses the official Silabs Tools. For that is needed the BT121 Development Kit and to have installed the latest Smart Ready SDK, that can be found on the [Silabs website](https://www.silabs.com/products/wireless/bluetooth/bluetooth-low-energy-modules/bt121-bluetooth-smart-ready-module). The SDK provides the tools to compile and flash the BT121 module.
To upload the firmware to the BT121 BLE Module the BT121 Development Board should be connected to the BT121 through the following pins:

| BT121 Dev Board | BT121 |
| ------------- |-------------|
| VDD (PIN40)   | DVCC |
| GND (PIN2)    | GND |
| UART RX (PIN7) | TX (PA9) |
| UART TX (PIN5) | RX (PA10) |
| UART RTS (PIN3) | CTS (PA11) |
| UART CTS (PIN1) | RTS (PA12) |
| BOOT0 (PIN24) | BOOT0 |
| RESET (PIN36) | RESET |

Where the BT121 has the following pin-out:

![bt121_pinout](https://user-images.githubusercontent.com/7913981/29179550-a80b6dae-7dec-11e7-9c53-c6cd701c2b85.png)

After that, the firmware image can be uploaded to the BT121 using the bgupdate tool that can be found in the bin folder of the Smart Ready SDK installation directory.
The program command has the following syntax:

`<smart-ready-sdk dir>\ bgupdate.exe <COM port> fwimage.bin`

Where the `<COM port>` corresponds to the COM port assigned to the development kit board.
A prebuilt image is provided alongside with the source code and can be found under BT121_BITalino.bin

For further information on other methods to program the the BT121, please check to the following knowledge base:
http://community.silabs.com/t5/Bluetooth-Wi-Fi-Knowledge-Base/Programming-the-BT121/ta-p/173579

# Compiling the firmware
To compile the firmware from the source code instead of using the provided firmware image, make use of the BGBuild tool. The BGBuild compiler is a simple compiler that is used to build firmware images for the Bluetooth Smart Ready modules. The BGBuild compiler compiles the Bluetooth Smart Ready stack, the GATT database and optionally also a BGScript application into a single firmware binary image that can be uploaded to the BT121 module.
To compile, make sure the latest Smart Ready SDK is installed and the project.xml file is correctly configured. The syntax can be checked [here](https://www.silabs.com/documents/login/user-guides/ug212-bt-smart-ready.pdf).
The compile command has the following syntax:

`<smart-ready dir>\bgbuild.exe project.xml`

For further knowledge on the BGAPI serial protocol, BGLIB C API and BGScript scripting language please check the following reference:
https://www.silabs.com/documents/login/reference-manuals/bluegiga-bluetooth-smart-ready-bt121-api-rm.pdf

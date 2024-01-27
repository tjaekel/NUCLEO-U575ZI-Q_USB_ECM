# NUCLEO-U575ZI-Q_USB_ECM
 USB_ECM with NUCLEO-U575ZI-Q

## "Ethernet via USB"
This is a ported project, from STM32U575I-EV to a NUCLEO-U575ZI-Q board.

It uses the USB-C user connection to access MCU with network (TCP/IP, MCU runs a HTTPD web server). The NUCLEO-U575 does not have an ETH PHY neither a chip on board for ETH. But the USB can be used also to forward network traffic via USB to MCU.

## USB_ECM and Windows?
Unfortunately, Windows does not support USB_ECM. But it works fine on all Linux b based systems, such as Linux, MacOS, and even Android.
I have tested the system with an Android phone - it works fine.

## Web pages are on SD Card!
Attention: you need an external SD Card adapter on the NUCLEO-U575 board. The web pages are stored on SD Card.
I am in progress to make it working without an SD Card (see below, "FileX with flash files").

## Remark
This project is based on the CubeMX_U5xx and it has a similar folder structure.
I have remove all not needed files and I have converted it to a self-contained standalone project.

## "FileX with flash files"
The curent project uses AZURE RTOS and FileX. Therefore, the SD Card is needed to act as the file system storage.
But I want to change to use the internal MCU Flash memory (where the web pages are stored). So, I do not need anymore an SD Card adapter.

## How to test?
Compile and flash the project on a NUCLEO-U575ZI-Q board. Have an SD Card adapter connected and copy the Web_Content files to the SD Card.

Use an Android phone. Connect MCU and Android phone via a USB-C cable.

On Android phone go to "Connections" and find "Ethernet teathering": enable it. When you can enable it - a good sign! The MCU provides the USB_ECM properly.

On the ST-LINK VCP UART (baudrate 115200) it a log and you can see the assigned IP address for the MCU board.

Now you can enter the URL on your Android phone, but with the file name, e.g. as:
    192.168.133.7/index.html
and you will see the web page provided by the MCU, connected via USB.


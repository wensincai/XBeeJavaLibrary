  Introduction
  ------------
  This sample Java application shows how CoAP data messages are received from 
  another XBee device connected to a network.

  The application prints the received CoAP data to the standard output in ASCII 
  and hexadecimal formats after the sender's IPv6 address.

  NOTE: This example uses the Thread device (ThreadDevice) class.


  Files
  -----
    * com.digi.xbee.api.receivecoapdata.MainApp.java:
      Main application class. It instantiates a Thread device and establishes a 
      serial connection with it.

    * com.digi.xbee.api.receivecoapdata.MyCoAPDataReceiveListener.java:
      Class that handles the received CoAP data messages.


  Requirements
  ------------
  To run this example you will need:

    * At least two XBee Thread radios in API mode and their corresponding carrier
      boards (XBIB or equivalent).
    * The XCTU application (available at www.digi.com/xctu).


  Compatible protocols
  --------------------
    * Thread


  Example setup
  -------------
    1) Plug the XBee radios into the XBee adapters and connect them to your
       computer's USB or serial ports.

    2) Ensure that the modules are in API mode and connected to the same network.
       For further information on how to perform this task, read the 
       'Configuring Your XBee Modules' topic of the Getting Started guide.

    3) Set the port and baud rate of the receiver XBee radio in the MainApp 
       class.
       If you configured the modules in the previous step with the XCTU, you 
       will see the port number and baud rate in the 'Port' label of the device 
       on the left view.


  Running the example
  -------------------
  First, build and launch the application. Then, you need to send a data frame 
  to the receiver (local) module from another device. Follow the steps below to 
  do so:

    1) Launch the XCTU application.

    2) Add the sender (remote) XBee module to the XCTU, specifying its port 
       settings.

    3) Once the module is added, change to the 'Consoles' working mode and 
       open the serial connection.

    4) Create and add a frame using the 'Frames Generator' tool with the 
       following parameters:

       - Protocol:                        Select the protocol of your device.
       - Frame type:                      0x1C - CoAP Tx Request
       - Frame ID:                        01
       - Transmit options:                02
       - Method                           PUT [03]
       - IPv6 128-bit dest. address:      The IPv6 address ('MY', 'GA' or 'LA') of 
                                          the receiver module in hexadecimal format.
       - URI length:                      05
       - URI:                             XB/TX
       - Payload (ASCII):                 Hello XBee!

    5) Send this frame by selecting it and clicking the 'Send selected Frame' 
       button.

  When the CoAP data frame is sent, verify that a line with the IPv6 address and 
  the data included in the 'Payload' field is printed out in the console of the 
  launched application:

    CoAP data from XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XXXX >> 48 65 6C 6C 6F 20 58 42 65 65 21 | Hello XBee!

     - Where XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XXXX:XXXX is the IPv6 address of the 
       remote XBee device that sent the IPv6 data frame.

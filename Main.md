# **THIS GOOGLE CODE PAGE IS OUTDATED. PLEASE VISIT OUR NEW WEBSITE FOR THE MOST RECENT FILES AND UPDATES ABOUT THE OPENPLC PROJECT** #

## **http://www.openplcproject.com** ##

# Introduction #

OpenPLC is an open hardware alternative for industrial and home automation. It uses the well known ATmega chips as main processor, the same used on Arduino. This means that OpenPLC is code-compatible with all arduino sketches.



# Details #

The main features of the OpenPLC are:


● Protected 24V Digital Inputs (8 inputs for each module)

● Protected 24V Digital Outputs (8 inputs for each module)

● USB Communication (used for programming)

● RS-485 bus for communication between modules

● Open Source IDE with c++ programming

● Open Source IDE with Ladder programming

● Integrated Ethernet

● 16MHz ATmega2560 as main processor


# News #

**November 29, 2013**

Finally the boards are done! Earlier this month we received the first prototypes of the boards. We were so excited to see the OpenPLC working for the first time. And for our big surprise, everything worked as expected! Here is a photo of the boards fully assembled:

https://open-plc.googlecode.com/files/foto%20OpenPLC.PNG

We made a benchmark with a Siemens S7-200 PLC. There was an application running with this plc at the university. We printed out the ladder diagram for the application, insert that on the OpenPLC Ladder and uploaded the code to the OpenPLC. After that, we unplugged the siemens plc and plugged our PLC. The application worked exactly the same way it was working before with the siemens plc. It was amazing!


**September 9, 2013**

I'm very happy to announce here that the OpenPLC Ladder is finally ready for it's first public beta! We are developing it for the last couple months and we are really excited about how it can compile ladder code directly to the OpenPLC processor. It was based on [LDmicro](http://cq.cx/ladder.pl) by Jonathan Westhues, an awesome piece of software that can generate ANSI C code from a ladder diagram. We added to it the AVR compiler and a nice user interface made in C# so that you can compile your ladder diagram in one click. Check out some screenshots:

http://open-plc.googlecode.com/files/ladder_screenshot1.PNG

http://open-plc.googlecode.com/files/ladder_screenshot2.PNG

http://open-plc.googlecode.com/files/ladder_screenshot3.PNG

If you want to download the binary files, just click [HERE](https://docs.google.com/file/d/0BwyThwktWLAlSG9Uc3FfYmlHcnc/edit?usp=sharing). For now, only the binary files are available. As soon as the project is done, we will make all the code available for public access.

NOTE: You can upload the openplc ladder code to a standard Arduino Mega as it has the same processor of the OpenPLC


**May 25, 2013**

You may have noticed that we changed some of the main features of the OpenPLC. During this semester, instead of creating new boards, we started to review our project and to improve it. We realized that our architecture must be modular, witch means that we need to create a bus and a protocol for the modules to communicate. We also realized that there are many hardware project errors. So, what we did was a start over. We learned a lot from this first stage of the OpenPLC development, but we need to create another one, completely different. Here are one of the main changes that we will apply to the project:

1) Every module will have a processor, and it will be the ATMega328P for compatibility reasons.

2) There will be a board that will interconnect all the other boards. We want to call it the **bus board**.

3) The bus board will have RS-485 drivers to establish the communication between modules. RS-485 is a hardware protocol, and it has proven to be really stable and immune to noise.

4) The CPU board (name has changed from main board to CPU board) will have integrated ethernet with a MODBUS TCP implementation in software. The CPU board will also be the RS-485 master on the bus. It means that all communication will start from the CPU board.

5) We will create a protocol for the boards to communicate. It will be universal, witch means that as new modules arrive, with different functionalities, they will be able to communicate using the same protocol.

6) There will be two new softwares for the OpenPLC. One is the OpenPLC Configuration Tool, where the user can get information about the PLC and its modules, change network configuration and change module's ID. The other will be the OpenPLC Ladder for graphical programming.

We are happy to announce that some of these new functionalities are already implemented. Using our old OpenPLC prototype, we changed the main board a bit to include an ethernet module. We also added ethernet and MODBUS TCP capabilities to our OpenPLC Library for the Arduino. Currently it's responding for the MODBUS FC01, FC02, FC05 and FC15. The OpenPLC Configuration Tool is partially done. It was coded in C# witch is a very modern and robust language. By now it can retrieve information from the OpenPLC prototype and change network configuration as IP, subnet mask, gateway and MAC Address.

We also created a beta version of our OpenPLC Ladder. We are really happy with that because now users can program our PLC using the standardized Ladder graphical language. It all has been made possible thanks to Jonathan Westhues and his LDmicro software. We used LDmicro as a base to generate ANSI C code from a ladder diagram and then integrated the generated code with our OpenPLC Library and compiled everything together using AVR-tools. It works like a charm! We are really excited to show everyone these new features, but first we need to develop our new system and adapt our files and libraries to it. As soon as the project is done, we will release all files to the public.


**February 20, 2013**

Brazilian summer is over, and now it's time to return to our researches. Our plans for this semester are very agressive. We want to improve our hardware and make new boards. For this semester we are planing to release a **Ethernet Network Interface** and an **I/O Expansion Board**. So keep checking here for more news!

**December 19, 2012**

After a long delay we finally have good news and a great Christmas gift to everybody. Many things happened during these past months, so I will try to resume everything here:
  * OpenPLC's analogboard is ready! Check out the [Design Files](Design.md) for more information
  * For the first time, OpenPLC went to a public presentation during Feira de Integração Curricular at PUC Minas. It caught attention of many visitors, teachers and students.
  * Hack-a-Day wrote about us! Check it out http://hackaday.com/2012/10/27/openplc-for-industrial-automation-to-halloween-displays/
  * As a Christmas gift to everybody we wrote the OpenPLC Library for Arduino. Its a small and simple library that will make easier the integration between OpenPLC and the Arduino Platform. Check it [here](OpenPLCLib.md)

Below you can check some pictures of our first OpenPLC prototype and it's first public presentation:

http://open-plc.googlecode.com/files/feira1.PNG

http://open-plc.googlecode.com/files/feira2.PNG

http://open-plc.googlecode.com/files/feira3.PNG

http://open-plc.googlecode.com/files/feira4.PNG

http://open-plc.googlecode.com/files/feira5.PNG

**October 18, 2012**

Our outputboard is done! Now we only have one board to go! Check out the renderization of the board below. It looks great! Also, with this board we have a new revision of our project: Rev0.4. You can get the full kicad project at our [Design Files](Design.md) section, or download separately only the schematics in pdf format.

![http://open-plc.googlecode.com/files/outputboard.png](http://open-plc.googlecode.com/files/outputboard.png)

**October 17, 2012**

The OpenPLC prototypes arrived! We are holding in our hads right now the first OpenPLC mainboard prototype. We will just assemble the components and test it out. As soon as we have our tests done, I will post the results here. Check out the pictures.

![http://open-plc.googlecode.com/files/board.jpg](http://open-plc.googlecode.com/files/board.jpg)
![http://open-plc.googlecode.com/files/board_components.jpg](http://open-plc.googlecode.com/files/board_components.jpg)

**October 10, 2012**

After a little delay we are finally back with great news: the inputboard is finished! Below you can check the first renderization of the board using wings render built in kicad. Also, I must say that we sent the mainboard to production and now we have the first prototype. In a few days I will post some pictures of it. We now need to get the components to assemble it and start the first tests. As soon as it's done I will post the results here. I hope you all are as excited as I am to see it working!

![http://open-plc.googlecode.com/files/inputboard.png](http://open-plc.googlecode.com/files/inputboard.png)

**September 12, 2012**

Finally, we concluded the development of our OpenPLC Main Board! We are excited to start producing the first prototypes and test it. Check out the [Design](Design.md) page for the download link and more information.

![http://open-plc.googlecode.com/files/mainboard-pcb1.png](http://open-plc.googlecode.com/files/mainboard-pcb1.png)


**September 10, 2012**

After some analysis, we realized that our linear 7805 power supply would not be a good idea. It would generate a lot of heat if the circuit starts to demand too much current. Also it has some conceptual problems (you can't short the output of two 7805's because the regulation in two CI's are not exactly the same). So we decided to substitute the linear power supply with a better and optimized switching power supply based on LM2576. We also added a Protection Circuit just in case someone try to use 220V instead of 24V :) [Check it out](Design.md)


**September 4, 2012**

We just finish building the first schematic of the OpenPLC Main Board. You may want to check our [Design](Design.md) page for more details

**August 28, 2012**

Today we presented the OpenPLC project for the first time at PUC University. You may want to check our presentation [here](http://open-plc.googlecode.com/files/OpenPLC%20Presentation.pdf)
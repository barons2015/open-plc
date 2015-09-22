# **THIS GOOGLE CODE PAGE IS OUTDATED. PLEASE VISIT OUR NEW WEBSITE FOR THE MOST RECENT FILES AND UPDATES ABOUT THE OPENPLC PROJECT** #

## **http://www.openplcproject.com** ##

# OpenPLC Architecture #

The image above shows the actual ATmega328 pinout used by OpenPLC:

![http://open-plc.googlecode.com/files/ATmega%20328%20pinout.png](http://open-plc.googlecode.com/files/ATmega%20328%20pinout.png)

Based on this idea we are designing the schematic of the OpenPLC main board. The digital inputs will be opto-isolated and the digital outputs will be divided in two parts: relay outputs (Pin7 & Pin8) and fast transistorized outputs (Pin6 & Pin9)
The analog inputs will have a circuitry based on op-amps to isolate and convert 4-20mA into 5V linearly
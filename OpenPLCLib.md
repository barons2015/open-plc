# **THIS GOOGLE CODE PAGE IS OUTDATED. PLEASE VISIT OUR NEW WEBSITE FOR THE MOST RECENT FILES AND UPDATES ABOUT THE OPENPLC PROJECT** #

## **http://www.openplcproject.com** ##

# OpenPLC Library #

We developed a small library to use our PLC with the Arduino Platform. To install, just download the library using the link above, and extract it inside the Libraries folder in your Arduino installation.

**Download Link: [OpenPLC-Lib.zip](http://open-plc.googlecode.com/files/OpenPLC-Lib.zip)**

You may also want to look at the [OpenPLC Talk](http://open-plc.googlecode.com/files/OpenPLC_Talk.zip), a small arduino software wrote using OpenPLC Library. It receives commands trough USB port and answers back activating outputs, reading inputs or calculating the 'pi' number. Try commands as:
  * read input X0
  * set output Y1
  * clear output Y2
  * set pwm Y0
  * write pi

**Note: if you are using the arduino serial monitor, you must select 'Carriage return' on the popup next to the baud rate selection for the OpenPLC Talk to understand your commands.**


# Library Functions #

**void PLCInit()**

Initializes the PLC with the proper output and input pins.

Example:
```
void setup() 
{
  PLCInit();
  Serial.begin(38400);
  Serial.println("System Loaded!");
}
```

---


**int readInput(int input)**

Returns the state of the selected input. The state can be ON or OFF.

**Note: OpenPLC inputs are called X0, X1, X2...**

Example:
```
void setup() 
{
  PLCInit();
  Serial.begin(38400);
  Serial.println("System Loaded!");
}
void loop()
{
  Serial.print("Input X0: ");
  Serial.println(readInput(X0)); //prints X0 input's state
  delay(500);
}
```

---


**int setOutput(int output, boolean state)**

Defines the state of the selected output and returns zero if succeded or -1 in case of failure. This is a discrete function, so it will only set outputs to ON or OFF states. For pwm outputs, it will set the output to maximum duty cycle if the state is ON. If you need a variable pwm output, check setPWM() function.

**Note: OpenPLC outputs are called Y0, Y1, Y2...**

Example:
```
void setup() 
{
  PLCInit();
  Serial.begin(38400);
  Serial.println("System Loaded!");
}
void loop()
{
  Serial.println("Output Y0 ON"); //set output Y0
  setOutput(Y0, ON);
  delay(1000);

  Serial.println("Output Y0 OFF"); //clear output Y0
  setOutput(Y0, OFF);
  delay(1000);
}
```

---


**int setPWM(int output, float pwmvalue)**

Defines the duty cycle of the pwm-able outputs. The pwm will range from 0-100. It will return zero if succeded or -1 in case of failure.

Example:
```
int pwmvalue = 0;
void setup() 
{
  PLCInit();
  Serial.begin(38400);
  Serial.println("System Loaded!");
}
void loop()
{
  setPWM(Y3, pwmvalue); //set Y3 output to pwmvalue
  pwmvalue++; //increases pwmvalue
  if(pwmvalue > 100) //compares if pwmvalue got its maximum value
    pwmvalue = 0; //reset pwmvalue
  delay(10);
}
```

---


**float readAnalog(int analog)**

Returns the value read by the desired analog input.

**Note: OpenPLC Analog Inputs are called A0, A1, A2...**

Example:
```
void setup() 
{
  PLCInit();
  Serial.begin(38400);
  Serial.println("System Loaded!");
}
void loop()
{
  Serial.print("Analog A0: ");
  Serial.println(readAnalog(A0)); //prints A0 value
  delay(500);
}
```
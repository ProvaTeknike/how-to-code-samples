# Plant Lighting System in Python*

## What it is

Using a compatible Intel-based platform, this project lets you create an automatic plant lighting monitor system that:<br>
- uses a light sensor to determine if a separate automated lighting system is turned on or off based on a configurable schedule.<br>
- can be accessed with your mobile phone via the built-in web interface to set the lighting times.<br>
- monitors the water levels using a connected moisture sensor.<br>
- logs events from the lighting system using cloud-based data storage.<br>
- sends text messages to alert recipients if the system if not working as expected.

## First time setup
For all the samples in this repository, see the ![General Setup Instructions](./../../README.md#setup) for required boards and libraries.  You need either Grove\* or DFRobot\* sensors but not both.

## Hardware requirements

### Grove\*

Sensor | Pin
--- | ---
Grove\* Light Sensor | A0
Grove\* Moisture Sensor | A1
Grove\* RGB LCD | I2C

### DFRobot\* 

Sensor | Pin
--- | ---
Analog Ambient Light Sensor | A1
Moisture Sensor | A2

For more specific information on the hardware requirements see ![Hardware Details](./../README.md#hardware-requirements)

## Software requirements

1. ![MRAA](https://github.com/intel-iot-devkit/mraa) and ![UPM](https://upm.mraa.io/) 
2. Python 2.7
3. Packages as listed in the ![setup.py](setup.py) file in this directory
1. Microsoft Azure\*, IBM Bluemix\*, AT&T M2X\*, AWS\*, Predix\*, or SAP\* account (optional)
2. Twilio\* account (optional)

You can install the dependencies.

### Twilio\* API key (optional)

To optionally send text messages, you need to register for an account and get an API key from the Twilio\* website:

<a href="https://www.twilio.com">https://www.twilio.com</a>

You cannot send text messages without obtaining a Twilio API key first. You can still run the example, but without the text messages.

## Configuring the example

When the example is installed through `pip` the `config.json` file that holds the configuration for the example lives in `~/python/examples/iot_plant_lighting_system/plant-lighting-system/python/iot_plant_lighting_system/config.json`.

To configure the example for the Grove\* kit, just leave the `kit` key in the `config.json` set to `grove`. To configure the example for the DFRobot\* kit, change the `kit` key in the `config.json` to `dfrobot` as follows:

```JSON
{
  "kit": "dfrobot"
}
```

To configure the example for the Arduino 101\* (branded Genuino 101\* outside the U.S.), add a `platform` key with the value `firmata` to the `config.json`, as follows:

```JSON
{
  "kit": "grove",
  "platform": "firmata"
}
```

To configure the example for sending optional text messages, obtain an API key from the Twilio\* web site as explained above, and then add the `TWILIO_ACCT_SID` and `TWILIO_AUTH_TOKEN` keys to the `config.json` file as follows:

```JSON
{
  "kit": "grove",
  "TWILIO_ACCT_SID": "YOURAPIKEY",
  "TWILIO_AUTH_TOKEN": "YOURTOKEN"
}
```

To configure the example for both the text messages and the Microsoft Azure\*, IBM Bluemix\*, or AWS\* data store, add the `TWILIO_ACCT_SID`, `TWILIO_AUTH_TOKEN`, `SERVER`, and `AUTH_TOKEN` keys to the `config.json` file as follows:

```JSON
{
  "kit": "grove",
  "TWILIO_ACCT_SID": "YOURAPIKEY",
  "TWILIO_AUTH_TOKEN": "YOURTOKEN",
  "SERVER": "http://Intel-examples.azurewebsites.net/logger/lighting-system",
  "AUTH_TOKEN": "s3cr3t"
}
```

For information on how to configure the example for an optional Microsoft Azure\*, IBM Bluemix\*, AT&T M2X\*, AWS\*, Predix\*, or SAP\* IoT cloud server, go to:

[https://github.com/intel-iot-devkit/iot-samples-cloud-setup](https://github.com/intel-iot-devkit/iot-samples-cloud-setup)

## Running the program

Once the example is installed through `pip` you can run the program by running the following command in an SSH session to the board:

    $ python -m iot_plant_lighting_system
    
You will see output similar to below when the program is running.

```
MQTT message published: { d: { value: 'off 2016-04-22T03:39:36.101Z' } } 
SMS sent { sid: 'SM14faee6a517f44db91d985c9ee68b3b2', 
	date_created: 'Fri, 22 Apr 2016 03:39:36 +0000', 
	date_updated: 'Fri, 22 Apr 2016 03:39:36 +0000', 
	date_sent: null, 
```

Refer to ![How it Works](./../README.md#how-it-works) for details on the functionality.

## IoT cloud setup (optional)

You can optionally store the data generated by this sample program using cloud-based IoT platforms from Microsoft Azure\*, IBM Bluemix\*, AT&T M2X\*, AWS\*, Predix\*, or SAP\*.

For information on how to connect to your own cloud server, go to:

[https://github.com/intel-iot-devkit/iot-samples-cloud-setup](https://github.com/intel-iot-devkit/iot-samples-cloud-setup)

IMPORTANT NOTICE: This software is sample software. It is not designed or intended for use in any medical, life-saving or life-sustaining systems, transportation systems, nuclear systems, or for any other mission-critical application in which the failure of the system could lead to critical injury or death. The software may not be fully tested and may contain bugs or errors; it may not be intended or suitable for commercial release. No regulatory approvals for the software have been obtained, and therefore software may not be certified for use in certain countries or environments.

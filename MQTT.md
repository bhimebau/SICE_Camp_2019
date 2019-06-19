## Overview

MQTT is a publish subscribe protocol used by lightweight devices to publish data to a server where one or more clients for the data is subscribed. 

## Resources
* [Mosquitto Download](https://mosquitto.org/download/)

## Running Mosquitto Subscribe

The following command will allow you to see all of the messages on **test.mosquitto.org". The # character is a wildcard that allows you to see all of the topics. 

```bash
mosquitto_sub -h test.mosquitto.org -t #
```

```bash
25
57
{"lux": 1141.3}
-6.093477667009211
{"sTimestamp":"2019-06-19 17:10:35.247","sMessagetype":"livedata","rActualVoltageL1":0.02355123870074749,"rActualVoltageL2":0.023687919601798059,"rActualVoltageL3":0.02365374006330967,"rActualCurrentL1":0.002368750050663948,"rActualCurrentL2":0.0007525000255554915,"rActualCurrentL3":0.0012862500734627247,"rActualEnergyL1":9.662591082815197e-8,"rActualEnergyL2":3.0874080181320099e-8,"rActualEnergyL3":5.269699343557477e-8,"rFormingStationPreheaterTopActualValue1":59.79999923706055,"rFormingStationPreheaterBottomActualValue1":58.5,"rFormingStationPreheaterTopActualValue2":0.0,"rFormingStationPreheaterBottomActualValue2":0.0,"rFormingStationUpperPlugHeaterActualValue":38.79999923706055,"rFormingStationBottomToolHeaterActualValue":0.0,"rSealingStationHeaterActualValue":0.0}
20
25
��
{"lux": 0.0}
�{
c

>
```

## Running Mosquitto Publish 

A more practical use for MQTT is to publish to a specific topic that
you are subscribed.

```bash 
mosquitto_sub -h test.mosquitto.org -v -t bryce/data
```

This command subscribes to the topic **bryce/data** on the server **test.mosquitto.org**. You will note that, unlike subscribing to all messages, there are no messages printed. 

**Leave mosquitto_sub running and open a new command window.**

In the new window, run the following command:

```bash
mosquitto_pub -h test.mosquitto.org -t bryce/data -m "stuff"
```

You will notice that the **mosquitto_sub** window has changed and it should look like: 

```bash
bhimebau@mercury:~/forge$ mosquitto_sub -h test.mosquitto.org -v -t 'bryce/data'bryce/data stuff
```

Note that each line includes the topic, **bryce/data**, and the data, **stuff**.

## MQTT API

There are program libraries for many languages that allow your system to publish and subscribe. Here are links to a couple of the libraries. 

* [MQTT C Library](https://www.eclipse.org/paho/clients/c/)
* [MQTT Java Library](http://mqtt.org/tag/java)
* [MQTT Python Library](https://pypi.org/project/paho-mqtt/)


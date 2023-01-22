# Home energy project 2023: Bluetooth sensors

## Sensors

Available from many sources, lowest cost (~£3.70 each) appears to be Aliexpress when buying 5 off:
https://www.aliexpress.com/item/1005002008144309.html

The standard firmware can be replaced to allow the sensors to broadcast unencrypted data:

https://hackaday.com/2020/11/17/custom-firmware-for-cheap-bluetooth-thermometers/

### Loading custom firmware (use mobile phone)

1. Download firmware from https://github.com/atc1441/ATC_MiThermometer/releases
2. Load https://atc1441.github.io/TelinkFlasher.html
3. Click `Connect` and wait... it can take a minute (if you can't see any devices try switching off WiFi)
4. Click `Do Activation`
5. Select firmware file
6. Click `Start flashing`
7. Reload page to disconnect

## Gateway

I used OpenMQTTGateway from https://docs.openmqttgateway.com/upload/web-install.html which was loaded onto an ESP32.

After a number of failed attempts loading, I realised that the webpage gives no feedback when the ESP32 is being loaded and thus I can't assuming it had failed. After open the broswers JS development tools and looking at the console output I got the ESP32 flashed. Setting it up onto the WiFi was easy as was setting the MQQT broker.

By default the OpenMQTTGatway publishers every BT packact it receives, you can whitelist/blacklist and this involves publishing configuration via MQTT.

# Feedback

## Pros

* Low cost sensors
* Tidy small sensors, easy to hide around the home

## Cons

* Flashing the sensors, working out the unique ID of each device is not simple, it took a few hours in total to get 5 sensors working
* Sensors need labing as you go else it's not easy to see which is which
* The low range of the sensors mean at least two BLE receivers are need in an average home

## General

* The OpenMQTTGateway works well, although it's not simple to get it fully configured.

## Wishlist

* Sensors that are pre-flashed ready to go
* Sensors that are labelled
* Proconfigure Gateway, with an easy way to set the WiFi details
* Easy to configure Gateway whitelist

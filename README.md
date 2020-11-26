# Hiking-DDS238-2-WIFI-Din-Rail-Energy-Meter-flashing-Tasmota

How to flash the [Hiking DDS238-2 WIFI Din Rail Energy Meter](https://www.aliexpress.com/item/4000571797301.html) with Tasmota...
<p align="center"> <img src="pictures/front.jpg" width="400" title="hover text"><img src="pictures/back.jpg" width="400" title="hover text"></p>

First try was with [tuya-convert](https://github.com/ct-Open-Source/tuya-convert) but this did not work (seems to be newer Firmware) i had to open the device, with the 2 screws on the backside:

Tasmota Version > 9.1 Template
```console
{"NAME":"Hiking DDS238-2 WIFI","GPIO":[0,2272,0,2304,0,0,0,0,0,0,320,0,32,0],"FLAG":0,"BASE":54}
```
Tasmota Config for TuyaMCU:
```console
Backlog TuyaMCU 33,20; TuyaMCU 32,18; TuyaMCU 31,19;
```
Tasmota Config : Publishing TuyaReceived to MQTT; Show Voltage with 1 Decimal
```console
Backlog SetOption66 1; VoltRes 1;
```
Rule to update Data on boot and every 5 seconds afterwards...
```console
Rule1 on System#Boot do RuleTimer1 5 endon on Rules#Timer=1 do backlog TuyaSend8; RuleTimer1 5 endon
```
Activate Rule1
```console
Rule1 1;
```
More pictures from the inside:
<p align="center"> <img src="pictures/sideview.jpg" width="400" > <img src="pictures/open_side.jpg" width="400" ></p>
<p align="center"> <img src="pictures/open_front.jpg" width="400" > <img src="pictures/open_side2.jpg" width="400" > </p>
<p align="center"> <img src="pictures/mainboard_front.jpg" width="400" ></p>
<p align="center"> <img src="pictures/displayboard_front.jpg" width="400" > <img src="pictures/displayboard_side2.jpg" width="400" ></p>
<p align="center"> <img src="pictures/displayboard_back_with_espboard.jpg" width="400" ></p>
<p align="center"> <img src="pictures/displayboard_back_without_espboard.jpg" width="400" ></p>
<p align="center"> <img src="pictures/displayboard_back_with_espboard_side_after.jpg" width="400" ></p>
<p align="center"> <img src="pictures/displayboard_back_with_espboard_side_before.jpg" width="400" ></p>
<p align="center"> <img src="pictures/espboard_back.jpg" width="400" > <img src="pictures/espboard_front.jpg" width="400" ></p>



to be able to flash the TYWE3S (an ESP8266EX) i had to disconnect it from the metering chip because otherwise it would not respond on the TX/RX Interface...


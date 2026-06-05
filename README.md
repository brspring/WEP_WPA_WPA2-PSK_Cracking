This project demonstrates practical attacks against legacy and modern Wi-Fi security protocols, including:

* WEP

* WPA

* WPA2-PSK

# Devices Used in Demonstration

## MitraStar GPT-2541GNAC-GV Router

![MitraStar GPT-2541GNAC-GV](/imgs/MitraStar-GPT-2541GNAC-GV.jpeg)

### Configuration

| Band    | Security Protocol |
| ------- | ----------------- |
| 2.4 GHz | WEP               |
| 5 GHz   | WPA2-PSK          |

One protocol per frequency

***

## ESP32

![ESP32](/imgs/ESP32.jpeg)

The ESP32 is used as access point with **WPA** configured

***

# Demonstration Goals

The following scenarios will be demonstrated:

### WEP

* Packet capture

* IV collection

* Key recovery

### WPA/WPA2-PSK

* Handshake capture

* Password cracking using a dictionary attack

* Analysis of password strength impact

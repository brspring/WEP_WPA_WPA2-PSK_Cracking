This project demonstrates practical attacks against legacy and modern Wi-Fi security protocols, including:

* WEP

* WPA

* WPA2-PSK

# Devices Used in Demonstration

## MitraStar GPT-2541GNAC-GV Router

<img src="/imgs/MitraStar-GPT-2541GNAC-GV.jpeg" alt="MitraStar GPT-2541GNAC-GV" width="250">

### Configuration

| Band    | Security Protocol |
| ------- | ----------------- |
| 2.4 GHz | WEP               |
| 5 GHz   | WPA2-PSK          |

One protocol per frequency

***

## ESP32

<img src="/imgs/ESP32.jpeg" alt="ESP32" width="250">

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

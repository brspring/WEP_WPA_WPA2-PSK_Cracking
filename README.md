This project demonstrates practical attacks against legacy and modern Wi-Fi security protocols, including:

* [WEP](wep_attack.md)

* [WPA](wpa_attack.md)

* [WPA2-PSK](wpa2psk.md)

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

[Fixing usb device issues](usb_adapter_fix.md)

# Aircrack-ng

## Prerequisites Setup

### Configuring interface to monitor mode
Command to show the wireless interface details. By default, most interfaces operate in "Managed" mode, but the target interface needs to be in "Monitor" mode for packet capture and injection.
```
iwconfig
```

Killing Interfering Processes

```
sudo airmon-ng check kill
```

command show the wireless interface details, the target interface needs to be in "Monitor" mode.
When the interface are in the Managed mode, the aircrackng can configure interface with these command:

```
sudo airmon-ng start wlan0
```

## Discovering Available Access Points:´
Once the interface is successfully in Monitor mode, you can scan the area for available routers and clients using the airodump-ng tool
```
sudo airmon-ng start wlan0
```

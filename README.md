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


# Configuration for AC1300 USB Wi-Fi and Bluetooth adapter
Download drivers and follow the instructions in this [repo](https://github.com/shenmintao/aic8800d80/blob/main/INSTALL_SCRIPT.md)

## Find your USB ID
```
lsusb
```
1111:1111 in my case

## Prevent the device from acting as a pendrive
```
echo "options usb-storage quirks=1111:1111:i" | sudo tee /etc/modprobe.d/aic8800_ignore.conf

sudo update-initramfs -u
```
Reset your PC without desconect device

## Switch the device from pendrive to USB Wifi mode

```
sudo usb_modeswitch -W -c /etc/usb_modeswitch.d/1111:1111
```
If works correctly the command `iwconfig` show a wireless interface


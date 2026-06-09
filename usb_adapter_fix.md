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

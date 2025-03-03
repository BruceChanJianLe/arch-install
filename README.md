# Arch Install

This repository demonstrates steps to install Arch Linux from scratch...the hard way!

## Wi-Fi

Plug eternet cable directly to your laptop or connect to wi-fi with following command:  

**List available network devices**  
```bash
# Identify your wireless network interface
ip a show
```

**List available SSID**  
```bash
iwctl
# In my case, wlan0 is my wireless network interface
station wlan0 get-networks
# Connect to your preferred SSID
station wlan0 connect
```

## SSH

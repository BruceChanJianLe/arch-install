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

First, check whether ssh service is running and available.  
```bash
systemctl status sshd
```

If it is running and available, you can proceed to the next command.
Otherwise, just start it!  
```bash
systemctl start sshd
```

Now, identify your ip address!  
```bash
# Idenfitfy your ip address
ip a show
```

Now, provide a root password for the installer.
This is to allow remote access, otherwise, you won't be able to do that.  
```bash
passwd
```

Now use it on another machine to ssh in!  
```bash
ssh 
```

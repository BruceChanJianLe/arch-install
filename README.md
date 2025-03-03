# Arch Install

> This repository demonstrates steps to install Arch Linux alongside with Ubuntu...the easy way!

Prerequisite:
- Installed Ubuntu
- A free partition

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
ssh root@192.168.10.109
```

## Partition

**Obtain names of the blocks**  
```bash
lsblk
# For my case, it is nvme0n1
```

**Create partitions**  
```bash
# We will need a partition for boot and another for our OS
cfdisk /dev/nvme0n1
# I create these two partitions, ensure that the type is correct
# Then write!
# /dev/nvme0n1p5       1G EFI System
# /dev/nvme0n1p8       584.9G Linux filesystem
```

![img](./resources/create_partition.png)


## Filesystem

**Format EFI Partition**  
```bash
mkfs.fat -F32 /dev/nvme0n1p5
```

**Format OS Partition**  
```bash
mkfs.ext4 /dev/nvme0n1p8
```

## Installation

Use archinstall to install the rest!  

```bash
archinstall
```

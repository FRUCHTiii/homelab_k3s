---
title: Baremetall Setup
permalink: /baremetall/
has_children: false
nav_order: 2
---

# RPi Baremetall Setup
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
---

# Update EPROOM

## Flash image
Raspberry Pi OS Lite

## Update Raspi and EPROOM
```
apt update
apt full-upgrade
reboot
```


# Think about Topology

Hostname | IP | Netmask | Role
--- | --- | --- | ---
k3sc1 | 192.168.0.1 | 255.255.252.0 | Controll Plane Node #1
k3sc2 | 192.168.0.2 | 255.255.252.0 | Controll Plane Node #2
k3sc3 | 192.168.0.3 | 255.255.252.0 | Controll Plane Node #3
k3sc99 | 192.168.0.99 | 255.255.252.0 | Worker Node with AMD64 CPU


# Install OS - Ubuntu

## Base Image flashen
Ubuntu LTS Server 64bit
	
## Import SSH Keys
```
ssh-import-id-gh FRUCHTiii
```
	
## Fix Keyboard Layout
```
dpkg-reconfigure keyboard-configuration
```
```
Generic 105
German
German
Default
No Compose key
```

## Update
```
apt update
apt upgrade
```

## Install packages
```
apt install vim
```

## Set default editor
```
update-alternatives --config editor
```


## Setup Hostname
```
vim /etc/hostname
vim /etc/hosts
```

## Change to ifupdown
```
apt install ifupdown resolvconf
apt purge netplan.io
rm -rf /etc/netplan
rm -rf /usr/share/netplan
rm -rf /etc/cloud
vim /etc/network/interfaces
     ```
     Auto lo
	 Iface lo inet loopback
     ```
```

## Set static IP
```
vim /etc/network/interfaces.d/eth0
```
auto eth0
allow-hotplug eth0
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask 255.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx
dns-nameservers xxx.xxx.xxx.xxx
dns-search domain-name
```
```

## activate Cgroups
```
vim /boot/firmware/cmdline.txt
```
cgroup_enable=cpuset cgroup_memory=1 cgroup_enable=memory
```
```
must be added to the end of the line
```
Reboot
```

[Install K3s](/k3s/)


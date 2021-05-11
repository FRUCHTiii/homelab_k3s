---
title: Unfifi Controller
permalink: /applications/unifi/
has_children: false
parent: Homelab Applications
nav_order: 59
---

# Add AP to new controller
Because of we are using a container with only special open ports we have to inform the APs to get to the new controller.

IP von Access Point auslesen
Ssh auf access point User:ubnt PW:ubnt
```
mca-cli -> Enter
set-inform http://unifi.fruchtiii.de:8080/inform
```

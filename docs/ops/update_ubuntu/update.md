---
title: Update Ubuntu
permalink: /ops/update_ubuntu/
has_children: false
parent: Operational Tasks
nav_order: 51
---

# Update Ubuntu
Sometimes we need to update our Ubuntu os and all packages.

## Drain Node
First we have to disable the node in k3s
```
kubectl cordon <NODE>
kubectl drain <NODE> --ignore-daemonsets
```

## Update
To update the ubuntu we have to do the following steps
```
sudo -i
apt update
apt upgrade
apt dist-upgrade
```

## Release Node as Ready
Now the node will become Ready
```
kubectl uncordon <NODE>
```

## Remaining Nodes
Do the steps above for all nodes.

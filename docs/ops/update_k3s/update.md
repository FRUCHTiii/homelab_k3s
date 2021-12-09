---
title: Update K3s
permalink: /ops/update_k3s/
has_children: false
parent: Operational Tasks
nav_order: 52
---

# Update K3s
Sometimes we need to update our kubernetes cluster to a newer version.
As K3s came as single binary the update is pretty easy as we only need to swap the binary and restart the service.

## Drain Node
First we have to disable the node in k3s
```
kubectl cordon <NODE>
kubectl drain <NODE> --ignore-daemonsets
```

## Check for new version
* Go to https://github.com/k3s-io/k3s/releases
* Check for the newest version with tag "Latest"
* copy link to the Asset for your system

Now export that URL as env variable
```
export K3SURL=<COPY_LINK_HERE>
```

## Remove old binary
Delete the old version
```
cd /usr/local/bin
rm k3s
```

## Get new binary
We have to download the new binary and make it executable
```
wget $K3SURL
chmod 755 k3s
```

## Check
Now the node that was updated should the in a newer version
```
kubectl get nodes
```

## Release Node as Ready
Now the node will become Ready
```
kubectl uncordon <NODE>
```

## Remaining Nodes
Do the steps above for all nodes.

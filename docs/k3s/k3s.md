---
title: K3S Installation
permalink: /k3s/
has_children: false
nav_order: 3
---

# K3S Installation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
---

# About K3S

# K3sup - way

## Install K3sup

## Install first controlplane node
```
k3sup install \
  --ip 192.168.0.1 \
  --user ubuntu \
  --cluster \
  --local-path /dev/null \
  --context k3s \
  --k3s-extra-args '--disable servicelb --disable traefik' \
  --k3s-version v1.20.2+k3s1
```

## Add second controlplane node
```
k3sup join \
  --ip 192.168.0.2 \
  --user ubuntu \
  --server-user ubuntu \
  --server-ip 192.168.0.1 \
  --server \
  --k3s-extra-args '--disable servicelb --disable traefik' \
  --k3s-version v1.20.2+k3s1
```

## Add third controlplane node
```
k3sup join \
  --ip 192.168.0.3 \
  --user ubuntu \
  --server-user ubuntu \
  --server-ip 192.168.0.1 \
  --server \
  --k3s-extra-args '--disable servicelb --disable traefik' \
  --k3s-version v1.20.2+k3s1
```

## Add worker node
```
k3sup join --ip 192.168.0.99 --server-ip 192.168.0.1 --user ubuntu --k3s-version v1.20.2+k3s1
```

## Get Kubeconfig
```
k3sup install \
  --skip-install \
  --ip 192.168.0.1 \
  --user ubuntu \
  --local-path ~/.kube/config_homelab_k3s
```


# Curl | bash - way
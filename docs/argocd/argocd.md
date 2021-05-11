---
title: ArgoCD Installation
permalink: /argocd/
has_children: false
nav_order: 4
---

# ArgoCD Installation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
---

# About ArgoCD

## Short introduction

## How i use it

# Deploy ArgoCD

## Create Rpository

## Apply ArgoCD Deployment

`kubectl create namespace argocd`
`kubectl apply -n argocd -f argo.yml`

# Add applications to ArgoCD

`kubectl -n argocd apply -f argo_configure_traefik.yml`
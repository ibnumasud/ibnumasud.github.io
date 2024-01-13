+++ 
date = "2020-11-27"
title = "K3S & Traefic2"
slug = "k3s-traefic"
tags = ["k3s", "traefic"]
keywords = ["k3s", "traefic"]
authors = ["Ibnu Mas'ud"]
+++

## Note

1. K3S default sudah memakai traefic sebagai ingress, akan tetapi masih pakai versi yang 1.7
2. Traefic 2 sudah bisa pakai let's encrypt buat ingressnya
3. coba install pakai helm

## Install K3S tanpa traefic

```
curl -sfL https://get.k3s.io | sh -s - --disable=traefik
k3s check-config #cek konfigurasi
sudo cat /var/lib/rancher/k3s/server/node-token   #kalau mau pakai cluster
```

## Install Traefic pakai HELM 

Helm adalah paket marager kubernetes seperti apt atau yum tapi buat kuebernetes, cara installnya [disini](https://helm.sh/docs/intro/install/)

```
curl https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash  #pakai script

helm repo add traefik https://helm.traefik.io/traefik   #Tambah repo Traefic

kubectl create ns traefik-v2

```

### Config Traefic

edit value dari traefic [default](https://github.com/traefik/traefik-helm-chart/blob/master/traefik/values.yaml)
```
helm install --namespace=traefik-v2 --values=./values.yaml traefik traefik/traefik

atau

helm install --namespace=traefik-v2 traefik traefik/traefik
```

## Refernsi
* https://medium.com/@fache.loic/k3s-traefik-2-9b4646393a1c
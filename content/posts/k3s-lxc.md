+++ 
date = "2020-11-27"
title = "K3S & Microk8s"
slug = "k3s-microk8s"
tags = ["k3s", "microk8s","lxd"]
keywords = ["k3s", "microk8s","lxd"]
authors = ["Ibnu Mas'ud"]
+++

## Note

1. Perlu kernel module tambahan untuk container di lxc
2. Perlu security tambahan terkait root dan namespace
3. storage container overlay2 tidak bisa di zfs

## setup lxc compatible container

### Buat LXD nya dahulu

```
lxd init
```

### Buat Profile LXC
```
LXC_PROFILE="k3s"
lxc profile copy default ${LXC_PROFILE}
lxc profile set ${LXC_PROFILE} security.privileged true  
lxc profile set ${LXC_PROFILE} security.nesting true 
lxc profile set ${LXC_PROFILE} limits.memory.swap false
lxc profile set ${LXC_PROFILE} linux.kernel_modules overlay,nf_nat,ip_tables,ip6_tables,netlink_diag,br_netfilter,xt_conntrack,nf_conntrack,ip_vs,vxlan

lxc profile set ${LXC_PROFILE} linux.kernel_modules nf_nat,ip_tables,ip6_tables,netlink_diag,xt_conntrack,nf_conntrack,ip_vs,vxlan


lxc profile set ${LXC_PROFILE} linux.kernel_modules ip_tables,ip6_tables,netlink_diag,nf_nat,overlay


cat <<EOT | lxc profile set ${LXC_PROFILE} raw.lxc -
lxc.apparmor.profile = unconfined
lxc.cgroup.devices.allow = a
lxc.mount.auto=proc:rw sys:rw
lxc.cap.drop =
EOT

lxc profile show ${LXC_PROFILE}
```

### Buat LXC untuk K3S

```
lxc init images:debian/10 --profile k3s k3s-lxc
lxc config device add k3s-lxc "kmsg" unix-char source="/dev/kmsg" path="/dev/kmsg"  #dibaca dari k3s butuh kmsg
lxc start k3s-lxc
```

### Dari Dalam LXC install K3S

```
lxc exec k3s-lxc /bin/bash
apt update && apt install openssl curl -y
curl -sL get.k3s.io | sh -
```

## Done
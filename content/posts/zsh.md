+++ 
date = "2020-06-18"
title = "ZSH Cheat Sheet"
slug = "zsh-cheat"
tags = ["cheat", "zsh"]
keywords = ["cheat", "zsh"]
authors = ["Ibnu Mas'ud"]
+++

```
zfs create -V 20GB my-pool/docker/blah
mkfs.btrfs /dev/zvol/my-pool/docker/blah
lxc config device add my-container docker disk source=/dev/zvol/my-pool/docker/blah path=/var/lib/docker
```
+++ 
date = "2020-11-29"
title = "Architecture Decision Record"
slug = "adr-cheat"
tags = ["adr", "architec", "cheat"]
keywords = ["adr", "architec"]
authors = ["Ibnu Mas'ud"]
+++

Hello World!

Akhir-akhir ini sedang baca-baca buku tentang arsitektur. Salah satu yang menjadi bahan diskusi menarik adalah tools-tools dan artefacnya. Salah satunya adalah ADR ini.

ADR adalah kepanjangan dari architecture decision record, lebih detilnya disana dijelaskan mengenai pengambilan keputusan arsitektur dari zaman dahulu sampai sekarang. Hal ini dirasa penting karena beberapa saat ini suka menemukan proyek-proyek yang tidak ada sejarah dan history arsitekturnya, jadi kita tidak bisa mengetahui contextnya untuk apa, apakah hanya untuk goin with the flow atau memang untuk menyelesaikan masalah yang dihadapi customer.

Secara umum ADR terdiri dari beberapa topik seperti yang dibahas di [sini](https://adr.github.io/) :
1. Title : Judul
2. Date : Tanggal :D
3. Status : accepted, proposed, deprecated, suspended
4. Context : Nah ini yang dijadikan acuan untuk pengambilan keputusan ini, bisa dijabarkan beberapa alasan teknologi, social, dan alternatif
5. Decision : Pilihannya yang dipakai yang mana
6. Consequencies : Efek-efek yang dihasilkan baik positif maupun negatif

Oke sekarang kita mulai eksplorasi toolsnya 

## Install
Untuk yang pakai mac bisa langsung install pakai brew
```
brew install adr-tools
```
opsi yang lainnya bisa dilihat di [github](https://github.com/npryce/adr-tools/blob/master/INSTALL.md)

## Eksplorasi

seperti biasa kita mulai dengan command help ada apa saja kah
```
usage: adr help COMMAND [ARG] ...
COMMAND is one of:
  help
  new
  link
  list
  init
  config
  generate
  upgrade-repository
Run 'adr help COMMAND' for help on a specific command.
```

kita mulai dari bahwah, yang ```generate``` digunakan untuk membuat daftar isi atau graph, ```adr list``` untuk me-list adr yang telah dibuat, ```adr init``` untuk initialisasi repositori adr, ```adr link``` untuk mebuat korelasi antara 2 adr. ``` adr new ``` bisa dipakai untuk membuat adr yang baru, bisa juga kalau menganti adr yang lama pakai argument -s.

Hasil dari dari adr init itu tergenerate folder /doc/adr/xxx.md seperti ini
```
adr init
doc/adr/0001-record-architecture-decisions.md

# 1. Record architecture decisions

Date: 2020-11-29

## Status

Accepted

## Context

We need to record the architectural decisions made on this project.

## Decision

We will use Architecture Decision Records, as [described by Michael Nygard](http://thinkrelevance.com/blog/2011/11/15/documenting-architecture-decisions).

## Consequences

See Michael Nygard's article, linked above. For a lightweight ADR toolset, see Nat Pryce's [adr-tools](https://github.com/npryce/adr-tools).
```

Kita coba adr new untuk blog ini
```
adr new Static Blog Generator
doc/adr/0002-static-blog-generator.md
```
Hasilnya langsung menghasilkan dokumen adr seperti sebelumnya

Kita superseed blog ini karena sebelumnya memakai gatsby, sekarang memakai hugo
```
adr new -s 2 Using Hugo Because Gatsby diriku kurang paham frontend :D
```
didalam doc tersebut ada tanda Supercedes 2. Static Blog Generator 0002-static-blog-generator.md

Untuk melihatnya bisa pakai ```adr generate graph``` hasilnya bisa dicopy dan di visualkan ditools-tools [grapviz](https://graphviz.org/)








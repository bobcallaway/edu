---
title: "coredns Image Variants"
type: "article"
description: "Detailed specs for coredns Chainguard Image Variants"
date: 2023-03-07T11:07:52+02:00
lastmod: 2023-03-07T11:07:52+02:00
draft: false
tags: ["Reference", "Chainguard Images", "Product"]
images: []
menu:
  docs:
    parent: "coredns"
weight: 550
toc: true
---

This page shows detailed information about all available variants of the Chainguard **coredns** Image.

## Variants Compared
The **coredns** Chainguard Image currently has 2 public variants: 

- `latest`
- `latest-dev`

The table has detailed information about each of these variants.

|              | latest                          | latest-dev                      |
|--------------|---------------------------------|---------------------------------|
| Default User | `nonroot`                       | `nonroot`                       |
| Entrypoint   | `/usr/bin/coredns -dns.port=53` | `/usr/bin/coredns -dns.port=53` |
| CMD          | not specified                   | not specified                   |
| Workdir      | not specified                   | not specified                   |
| Has apk?     | no                              | yes                             |
| Has a shell? | no                              | yes                             |

## Image Dependencies
The table shows package distribution across all variants.

|                          | latest | latest-dev |
|--------------------------|--------|------------|
| `ca-certificates-bundle` | X      | X          |
| `wolfi-baselayout`       | X      | X          |
| `coredns`                | X      | X          |
| `apk-tools`              |        | X          |
| `bash`                   |        | X          |
| `busybox`                |        | X          |
| `git`                    |        | X          |


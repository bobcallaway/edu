---
title: "Image Overview: secrets-store-csi-driver"
type: "article"
description: "Overview: secrets-store-csi-driver Chainguard Image"
date: 2022-11-01T11:07:52+02:00
lastmod: 2022-11-01T11:07:52+02:00
draft: false
tags: ["Reference", "Chainguard Images", "Product"]
images: []
menu:
  docs:
    parent: "images-reference"
weight: 500
toc: true
---

[cgr.dev/chainguard/secrets-store-csi-driver](https://github.com/chainguard-images/images/tree/main/images/secrets-store-csi-driver)

| Tag (s)       | Last Changed | Digest                                                                    |
|---------------|--------------|---------------------------------------------------------------------------|
|  `latest-dev` | July 18th    | `sha256:6c4c487b4b266bed1518901c6325449100a299c5875711e4ea12a882ed7c902b` |
|  `latest`     | July 14th    | `sha256:69ea76caa8874e0d625fc1635c0641ead0811639f8656586c7e1f8af9f8bb2a3` |
|               | July 12th    | `sha256:eeae01ef333f38afc7aae575d90f19ab12127cadc34cb4f33bfc72118de3c51d` |



Minimal image with Kubernetes Secrets Store CSI Driver. **EXPERIMENTAL**

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/secrets-store-csi-driver:latest
```

## Using Kubernetes Secrets Store CSI Driver

The Chainguard Secrets Store CSI DRiver image contains the `secrets-store-csi-driver` binary and required utilities.

The driver typically requires a plugin to be installed and configured separately to run.


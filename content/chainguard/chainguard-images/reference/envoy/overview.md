---
title: "Image Overview: envoy"
type: "article"
description: "Overview: envoy Chainguard Image"
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

[cgr.dev/chainguard/envoy](https://github.com/chainguard-images/images/tree/main/images/envoy)

| Tag (s)   | Last Changed | Digest                                                                    |
|-----------|--------------|---------------------------------------------------------------------------|
|  `latest` | July 15th    | `sha256:d9cc2b120c9580966ed91a565a795465da2efe8ca1f5c27e534f1e062cc4efee` |
|           | July 11th    | `sha256:506c256432772a1973b56967d5a79046aa7cd855adc54a15d663740ff7fbe1f7` |
|           | July 4th     | `sha256:51da7b6f7aec02b514b989185f3bfb792027cb5502c709cffd9e3efcc69cb9d7` |



[Envoy](https://github.com/envoyproxy/envoy) Cloud-native high-performance edge/middle/service proxy

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/envoy
```

## Using Envoy

To run with Docker using default configuration

```sh
docker run --platform=linux/amd64 -p10000:10000 -p 9901:9901 --rm cgr.dev/chainguard/envoy envoy --config-path /etc/envoy/envoy.yaml
```

Or to use a customised envoy configuratiom see https://www.envoyproxy.io/docs/envoy/latest/configuration/overview/overview and mount your file into the envoy container, e.g. `-v $PWD/config:/etc/envoy`

```sh
docker run --platform=linux/amd64 -p10000:10000 -p 9901:9901 --rm -v $PWD/config:/etc/envoy cgr.dev/chainguard/envoy envoy --config-path /etc/envoy/envoy.yaml
```


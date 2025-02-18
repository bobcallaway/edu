---
title: "Image Overview: zot"
type: "article"
description: "Overview: zot Chainguard Image"
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

[cgr.dev/chainguard/zot](https://github.com/chainguard-images/images/tree/main/images/zot)

| Tag (s)       | Last Changed | Digest                                                                    |
|---------------|--------------|---------------------------------------------------------------------------|
|  `latest-dev` | July 18th    | `sha256:d7b56aa8b2a7c15bfc79e8b2fd7d05442180904e652863a879b3a71e3139d6cc` |
|  `latest`     | July 14th    | `sha256:f05866a66fd9a040a485e5276d1bdc3825f5fc8b88b0a734e3cfeae90255b4f3` |
|               | July 12th    | `sha256:5fd4c51d6e017fa0e4a627bd44f363b42093e75c4754bce4b294ba4a29df3723` |
|               | July 4th     | `sha256:e6bff645d2a74abc46beba15949e88c5e7bf79e92a56dc054ebcad86f81abd75` |



Minimal image with
[zot](https://github.com/project-zot/zot)
binary. **EXPERIMENTAL**

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/zot:latest
```

## Usage

Create a zot config file:

```
cat <<EOF > zot-config.yaml
distspecversion: 1.1.0-dev
http:
  address: 0.0.0.0
  port: 5000
storage:
  rootdirectory: /var/lib/zot/data
EOF
```

Create a fresh `data` directory (this will store all OCI blobs as
[OCI Image Layout](https://github.com/opencontainers/image-spec/blob/main/image-layout.md)):

```
rm -rf data && mkdir data && chmod go+wrx data
```

Run the server:

```
docker run --rm -p 5000:5000 \
  -v "${PWD}/zot-config.yaml":/zot-config.yaml \
  -v "${PWD}/data":/var/lib/zot/data \
  cgr.dev/chainguard/zot:latest \
  serve /zot-config.yaml
```

Then in another terminal, try pushing an image with crane:
```
crane cp \
  cgr.dev/chainguard/bash:latest \
  localhost:5000/demo:latest
```

Then try pulling and running the image:
```
docker run --rm \
  localhost:5000/demo:latest \
  -c 'echo hello world'
```


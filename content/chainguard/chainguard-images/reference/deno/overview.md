---
title: "Image Overview: deno"
type: "article"
description: "Overview: deno Chainguard Image"
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

[cgr.dev/chainguard/deno](https://github.com/chainguard-images/images/tree/main/images/deno)

| Tag (s)   | Last Changed | Digest                                                                    |
|-----------|--------------|---------------------------------------------------------------------------|
|  `latest` | July 14th    | `sha256:8d6e118c546065e14ca9dffcce85012ef0e2834d063cfc7f448e4f5e3df5b04a` |
|           | July 11th    | `sha256:47760da528bcb8e1c7217060f7ab2880b277b8efb9da5653962d3a0e55b6fcef` |
|           | June 26th    | `sha256:2014d142e4bf902bbb5367bec84f943ee197f36ed5c97de2779595a130f816ca` |



Minimal container image for running deno apps

The image specifies a default non-root `deno` user (UID 65532), and a working directory at `/app`, owned by that `deno` user, and accessible to all users.

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/deno:latest
```

## Usage Example

Navigate to the [`example/`](https://github.com/chainguard-images/images/tree/main/images/deno/example) directory:

```
cd example/
```

The Dockerfile is based on [Deno's webserver tutorial](https://deno.land/manual@v1.28.3/examples/http_server), but packages it up into a Chainguard deno image.

Build the application on the deno base image.

```
docker build \
  --tag deno-docker \
  .
```

Then you can run the image:

```
docker run \
  --rm -it \
  -p 8080:8080 \
  deno-docker
```

...and test to see that it works:

```
$ curl localhost:8080
Your user-agent is:

curl/7.84.0%
```


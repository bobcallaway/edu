---
title: "Image Overview: dive"
type: "article"
description: "Overview: dive Chainguard Image"
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

[cgr.dev/chainguard/dive](https://github.com/chainguard-images/images/tree/main/images/dive)

| Tag (s)   | Last Changed | Digest                                                                    |
|-----------|--------------|---------------------------------------------------------------------------|
|  `latest` | July 14th    | `sha256:bf321dac68b99b73e21493efb99e11fd4a132678aa8be9f1b1ef80963397b08e` |
|           | July 7th     | `sha256:e2b63337a5fb224f766768bd3f13d05e42259b083a2fd2879c1fbd3bfa0c46dc` |



Minimal [dive](https://github.com/wagoodman/dive) container image.

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/dive:latest
```

## Usage

```
This tool provides a way to discover and explore the contents of a docker image. Additionally the tool estimates
the amount of wasted space and identifies the offending files from the image.

Usage:
  dive [IMAGE] [flags]
  dive [command]

Available Commands:
  build       Builds and analyzes a docker image from a Dockerfile (this is a thin wrapper for the `docker build` command).
  help        Help about any command
  version     print the version number and exit (also --version)

Flags:
      --ci                                Skip the interactive TUI and validate against CI rules (same as env var CI=true)
      --ci-config string                  If CI=true in the environment, use the given yaml to drive validation rules. (default ".dive-ci")
      --config string                     config file (default is $HOME/.dive.yaml, ~/.config/dive/*.yaml, or $XDG_CONFIG_HOME/dive.yaml)
  -h, --help                              help for dive
      --highestUserWastedPercent string   (only valid with --ci given) highest allowable percentage of bytes wasted (as a ratio between 0-1), otherwise CI validation will fail. (default "0.1")
      --highestWastedBytes string         (only valid with --ci given) highest allowable bytes wasted, otherwise CI validation will fail. (default "disabled")
  -i, --ignore-errors                     ignore image parsing errors and run the analysis anyway
  -j, --json string                       Skip the interactive TUI and write the layer analysis statistics to a given file.
      --lowestEfficiency string           (only valid with --ci given) lowest allowable image efficiency (as a ratio between 0-1), otherwise CI validation will fail. (default "0.9")
      --source string                     The container engine to fetch the image from. Allowed values: docker, podman, docker-archive (default "docker")
  -v, --version                           display version number

Use "dive [command] --help" for more information about a command.
```


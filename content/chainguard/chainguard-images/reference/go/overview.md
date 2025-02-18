---
title: "Image Overview: go"
type: "article"
description: "Overview: go Chainguard Image"
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

[cgr.dev/chainguard/go](https://github.com/chainguard-images/images/tree/main/images/go)

| Tag (s)       | Last Changed | Digest                                                                    |
|---------------|--------------|---------------------------------------------------------------------------|
|  `latest-dev` | July 18th    | `sha256:df4ec2234180dd1261103eea0ecfc9a9c6a44eaf0f8256a0fe71b51868552223` |
|  `latest`     | July 18th    | `sha256:abcb7be3360f5151a53a44d71d67a81591c9a53b2245703f9dd77c4f977d8109` |
|               | July 18th    | `sha256:ef9b0a3e8d4aba6b0c8a8bbaa13171f24d506349c0a5a625d41c333274086af8` |
|               | July 18th    | `sha256:ef650e759e66428d9488cef7e7705da13b9ff9d3bfec412988eb8c74e49f6648` |
|               | July 18th    | `sha256:6eefc5402968dd465e2cd4c2368c34cba6d6dcbccad43ea2e4d3323ac6168cf3` |
|               | July 18th    | `sha256:044626f8ff3f9d353ab5bacbd52cefc61f1cebb639b82efd7b0adc6a3d9698b2` |
|               | July 12th    | `sha256:fecc5b671b063aa1e6bb8e6211cf84c0b945fbb6360df9d29236365465bf5e64` |
|               | July 12th    | `sha256:643d38bc0e21b87917241613962331927f4f0b006c550950dfbcc81591eaf41a` |
|               | July 11th    | `sha256:0a2b247527b7d57ef9fdfe0dfa1500915d4c1e58050c88d29e849b39caa4cbc3` |
|               | July 11th    | `sha256:6c32bcf38379fa1a9edd18ccbc26895907e995cbbdd0da2d9c4d59342d8b5180` |
|               | July 11th    | `sha256:daa971e728d10513821f36d339738d8e8d1a89979da67a6d2afddfb428265917` |
|               | July 11th    | `sha256:ae39fcd9fdc9d1a55361a5ef5c9ae9c11a212582731f26646a94c66a77a65d53` |
|               | July 11th    | `sha256:c52c640eaaa1c5032d9eaa25e81e8ab0b7543d0ab1e2c09a0baec98e28620c9c` |
|               | July 8th     | `sha256:f807658ebd070455c2ec930407fb4427c0761f5401c5c84e9b0dac3ee99c1da8` |
|               | July 8th     | `sha256:1a938f192199fc3a30ef5d1af6bbfb872f5df6871d0e522bb98c950adf432fe5` |



Container image for building Go applications.

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/go:latest
```

## Usage

**NOTE**: As of 12/30/2022, the default go image uses Wolfi, which is glibc based.

If you were using this image before and are now running into trouble, the musl/Alpine based image is
still available at `cgr.dev/chainguard/go:latest-musl`.

## Host architecture example

To build the Go application in [examples/hello/main.go](https://github.com/chainguard-images/images/blob/main/images/go/examples/hello/main.go)
using the host architecture:

```sh
docker run --rm -v "${PWD}:/work" -w /work/examples/hello \
    -e GOOS="$(go env GOOS)" -e GOARCH="$(go env GOARCH)" \
    cgr.dev/chainguard/go build -o /work/hello .
```

The example application will be built to `./hello`:
```
$ ./hello
Hello World!
```

## Secure-by-default Features

In Go 1.20, we default to using the new `GODEBUG` settings of `tarinsecurepath=0` and `zipinsecurepath=0`.
These can be disabled by clearing the `GODEBUG` environment variable, or by setting them to `1`.

Learn more about these settings in the [Go release notes](https://tip.golang.org/doc/go1.20).

## Dockerfile example

The following example Dockerfile builds a hello-world program in Go and copies it on top of the `cgr.dev/chainguard/static:latest` base image:

```dockerfile
# syntax=docker/dockerfile:1.4
FROM cgr.dev/chainguard/go:latest as build

WORKDIR /work

COPY <<EOF go.mod
module hello
go 1.19
EOF

COPY <<EOF main.go
package main
import "fmt"
func main() {
    fmt.Println("Hello World!")
}
EOF
RUN go build -o hello .

FROM cgr.dev/chainguard/static:latest

COPY --from=build /work/hello /hello
CMD ["/hello"]
```

Run the following command to build the demo image and tag it as `go-hello-world`:

```shell
docker build -t go-hello-world  .
```

Now you can run the image with:

```shell
docker run go-hello-world
```

You should get output like this:

```
Hello World!
```

It’s worth noting how small the resulting image is:

```shell
docker images go-hello-world
```

```
REPOSITORY       TAG       IMAGE ID       CREATED       SIZE
go-hello-world   latest    859fedabd532   5 hours ago   3.21MB
```


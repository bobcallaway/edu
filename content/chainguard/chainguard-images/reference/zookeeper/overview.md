---
title: "Image Overview: zookeeper"
type: "article"
description: "Overview: zookeeper Chainguard Image"
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

[cgr.dev/chainguard/zookeeper](https://github.com/chainguard-images/images/tree/main/images/zookeeper)

| Tag (s)       | Last Changed | Digest                                                                    |
|---------------|--------------|---------------------------------------------------------------------------|
|  `latest-dev` | July 18th    | `sha256:3a8f97e4291990738988f7b8782d2d24a6dfd96fba951be90f4d8f046f70bd6b` |
|  `latest`     | July 11th    | `sha256:6b745edc5c5c95c74741b09f58db257606cb71858495bd7c47f46fa89fd355c2` |
|               | July 4th     | `sha256:39583c633e88e392889c00ee0807620fc363be8dedfa57c7c7b2c54c2304831b` |
|               | July 4th     | `sha256:fd731e680a47cd6ceed0d82068f31a1b06e612314ba142e8785f2ad2351dd12b` |



Minimal image with Apache Zookeeper. **EXPERIMENTAL**

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/zookeeper:latest
```

## Using Zookeeper

Chainguard Zookeeper images come with a sample configuration file in the `zoo.cfg` file in `/usr/share/java/zookeeper/conf`.
Zookeeper startup binaries and scripts are in `/usr/share/java/zookeeper/bin`, and `zkServer.sh` is the default entrypoint.

To run Zookeeper image with the sample configuration, use:

```shell
$ docker run cgr.dev/chainguard/zookeeper start-foreground
/usr/bin/java
ZooKeeper JMX enabled by default
Using config: /usr/share/java/zookeeper/bin/../conf/zoo_sample.cfg
2023-03-12 20:38:22,340 [myid:] - INFO  [main:o.a.z.s.q.QuorumPeerConfig@177] - Reading configuration from: /usr/share/java/zookeeper/bin/../conf/zoo_sample.cfg
2023-03-12 20:38:22,341 [myid:] - INFO  [main:o.a.z.s.q.QuorumPeerConfig@440] - clientPortAddress is 0.0.0.0:2181
2023-03-12 20:38:22,342 [myid:] - INFO  [main:o.a.z.s.q.QuorumPeerConfig@444] - secureClientPort is not set
2023-03-12 20:38:22,342 [myid:] - INFO  [main:o.a.z.s.q.QuorumPeerConfig@460] - observerMasterPort is not set
2023-03-12 20:38:22,342 [myid:] - INFO  [main:o.a.z.s.q.QuorumPeerConfig@477] - metricsProvider.className is org.apache.zookeeper.metrics.impl.DefaultMetricsProvider
2023-03-12 20:38:22,343 [myid:] - INFO  [main:o.a.z.s.DatadirCleanupManager@78] - autopurge.snapRetainCount set to 3
2023-03-12 20:38:22,343 [myid:] - INFO  [main:o.a.z.s.DatadirCleanupManager@79] - autopurge.purgeInterval set to 0
2023-03-12 20:38:22,343 [myid:] - INFO  [main:o.a.z.s.DatadirCleanupManager@101] - Purge task is not scheduled.
2023-03-12 20:38:22,343 [myid:] - WARN  [main:o.a.z.s.q.QuorumPeerMain@139] - Either no config or no quorum defined in config, running in standalone mode
2023-03-12 20:38:22,344 [myid:] - INFO  [main:o.a.z.j.ManagedUtil@46] - Log4j 1.2 jmx support not found; jmx disabled.
2023-03-12 20:38:22,344 [myid:] - INFO  [main:o.a.z.s.q.QuorumPeerConfig@177] - Reading configuration from: /usr/share/java/zookeeper/bin/../conf/zoo_sample.cfg
2023-03-12 20:38:22,344 [myid:] - INFO  [main:o.a.z.s.q.QuorumPeerConfig@440] - clientPortAddress is 0.0.0.0:2181
2023-03-12 20:38:22,344 [myid:] - INFO  [main:o.a.z.s.q.QuorumPeerConfig@444] - secureClientPort is not set
2023-03-12 20:38:22,344 [myid:] - INFO  [main:o.a.z.s.q.QuorumPeerConfig@460] - observerMasterPort is not set
2023-03-12 20:38:22,344 [myid:] - INFO  [main:o.a.z.s.q.QuorumPeerConfig@477] - metricsProvider.className is org.apache.zookeeper.metrics.impl.DefaultMetricsProvider
2023-03-12 20:38:22,344 [myid:] - INFO  [main:o.a.z.s.ZooKeeperServerMain@123] - Starting server
2023-03-12 20:38:22,350 [myid:] - INFO  [main:o.a.z.s.ServerMetrics@64] - ServerMetrics initialized with provider org.apache.zookeeper.metrics.impl.DefaultMetricsProvider@1040be71
2023-03-12 20:38:22,351 [myid:] - INFO  [main:o.a.z.s.a.DigestAuthenticationProvider@47] - ACL digest algorithm is: SHA1
2023-03-12 20:38:22,351 [myid:] - INFO  [main:o.a.z.s.a.DigestAuthenticationProvider@61] - zookeeper.DigestAuthenticationProvider.enabled = true
2023-03-12 20:38:22,352 [myid:] - INFO  [main:o.a.z.s.p.FileTxnSnapLog@124] - zookeeper.snapshot.trust.empty : false
2023-03-12 20:38:22,356 [myid:] - INFO  [main:o.a.z.ZookeeperBanner@42] -
2023-03-12 20:38:22,356 [myid:] - INFO  [main:o.a.z.ZookeeperBanner@42] -   ______                  _
2023-03-12 20:38:22,356 [myid:] - INFO  [main:o.a.z.ZookeeperBanner@42] -  |___  /                 | |
2023-03-12 20:38:22,356 [myid:] - INFO  [main:o.a.z.ZookeeperBanner@42] -     / /    ___     ___   | | __   ___    ___   _ __     ___   _ __
2023-03-12 20:38:22,356 [myid:] - INFO  [main:o.a.z.ZookeeperBanner@42] -    / /    / _ \   / _ \  | |/ /  / _ \  / _ \ | '_ \   / _ \ | '__|
2023-03-12 20:38:22,356 [myid:] - INFO  [main:o.a.z.ZookeeperBanner@42] -   / /__  | (_) | | (_) | |   <  |  __/ |  __/ | |_) | |  __/ | |
2023-03-12 20:38:22,356 [myid:] - INFO  [main:o.a.z.ZookeeperBanner@42] -  /_____|  \___/   \___/  |_|\_\  \___|  \___| | .__/   \___| |_|
2023-03-12 20:38:22,356 [myid:] - INFO  [main:o.a.z.ZookeeperBanner@42] -                                               | |
2023-03-12 20:38:22,356 [myid:] - INFO  [main:o.a.z.ZookeeperBanner@42] -                                               |_|
2023-03-12 20:38:22,356 [myid:] - INFO  [main:o.a.z.ZookeeperBanner@42] -
2023-03-12 20:38:22,357 [myid:] - INFO  [main:o.a.z.Environment@98] - Server environment:zookeeper.version=3.8.1-74db005175a4ec545697012f9069cb9dcc8cdda7, built on 2023-03-12 20:32 UTC
2023-03-12 20:38:22,357 [myid:] - INFO  [main:o.a.z.Environment@98] - Server environment:host.name=f0739f928721
```


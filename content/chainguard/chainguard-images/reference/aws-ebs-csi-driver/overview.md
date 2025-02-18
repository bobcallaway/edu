---
title: "Image Overview: aws-ebs-csi-driver"
type: "article"
description: "Overview: aws-ebs-csi-driver Chainguard Image"
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

[cgr.dev/chainguard/aws-ebs-csi-driver](https://github.com/chainguard-images/images/tree/main/images/aws-ebs-csi-driver)

| Tag (s)       | Last Changed | Digest                                                                    |
|---------------|--------------|---------------------------------------------------------------------------|
|  `latest`     | July 17th    | `sha256:4a2374808e51d88aa485a42b948ad93e0e6be69a5ef44a1f42e363c5fb58a1b0` |
|  `latest-dev` | July 17th    | `sha256:c8c7a4cfd3f49674f2434b5984d0e4b93057f641a6e6abe73873f00f8855248c` |
|               | July 14th    | `sha256:d4e2105d5ec17e5143746d18777f77f7abac1e7f3771dcc89bd533f3923f8471` |
|               | July 14th    | `sha256:926c32c95eb6e49251598684ed761cf6b607e7ba527bac83d5444a746e86d2c0` |
|               | July 12th    | `sha256:820cde7b1776990bd718d2a7ea9d62c2ee5972104a2520fba07100dcab67fb93` |



Minimal images for aws-ebs-csi-driver.

## Get It

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/aws-ebs-csi-driver:latest
```

## Testing

Since this application requires AWS credentials to be set up, we should create the required permissions before deploying it.

To do that, you can follow up on the official documentation [here](https://github.com/kubernetes-sigs/aws-ebs-csi-driver/blob/master/docs/install.md#set-up-driver-permissions).

But for the sake of simplicity, we can create the Kubernetes secret resource called `aws-secret` with the proper options `key_id` and `access_key`:

```shell
kubectl create secret generic aws-secret \
    --namespace kube-system \
    --from-literal "key_id=${AWS_ACCESS_KEY_ID}" \
    --from-literal "access_key=${AWS_SECRET_ACCESS_KEY}"
```

There are several methods to deploy the driver, but we will use the `helm` method.

We should add the `aws-ebs-csi-driver` Helm repository to our repositories list:

```shell
helm repo add aws-ebs-csi-driver https://kubernetes-sigs.github.io/aws-ebs-csi-driver
helm repo update
```

Next, we can install the driver with the following command:

```shell
helm upgrade --install aws-ebs-csi-driver \
    --namespace kube-system \
    --set image.repository=cgr.dev/chainguard/aws-ebs-csi-driver \
    --set image.tag=latest \
    aws-ebs-csi-driver/aws-ebs-csi-driver
```

Once the driver has been deployed, verify the pods are running:

```shell
kubectl get pods -n kube-system -l app.kubernetes.io/name=aws-ebs-csi-driver
```


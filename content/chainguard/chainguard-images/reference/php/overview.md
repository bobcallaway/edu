---
title: "Image Overview: php"
type: "article"
description: "Overview: php Chainguard Image"
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

[cgr.dev/chainguard/php](https://github.com/chainguard-images/images/tree/main/images/php)

| Tag (s)       | Last Changed | Digest                                                                    |
|---------------|--------------|---------------------------------------------------------------------------|
|               | July 18th    | `sha256:7ed4bbb59eb0754a7b15cc707249d55a6ebd4939478262fafeaf951e0a81e1c7` |
|               | July 18th    | `sha256:5154f54010f11f14c6b12b47824941586c1ee1c30a826b88e3543ae68abb57c0` |
|  `latest`     | July 18th    | `sha256:a5e870ec3fb9c29f51c80f967fcb6b3e6b5234f374bd125ba8ebc26ef45669c3` |
|  `latest-dev` | July 18th    | `sha256:6e2d5e7ab3aac179094f97b18dcd2bbf52231899a9c44c42d17504626e2aa5bb` |
|               | July 4th     | `sha256:94e445056d899722dd030ebeeb67796c62d5d8905358699938b5ebffdfcfd06f` |
|               | July 4th     | `sha256:eec9aeeee5f62cc114b528bcee4de7d6e2beca6fcc91428d325c1bab848ee11b` |
|               | July 4th     | `sha256:374b91cf7c7b73f8144066c1d1b1018ce6e6f931cf4af625c3d9a8558600be71` |
|               | July 4th     | `sha256:466588b8c97a57ab279e3a0bd0946a2d5301f609d1aa4e70359c137275b362fb` |
|               | June 30th    | `sha256:9c43537d5c04c7f5e62533fc3a78bb7a06e89361de3dc1cc0ef007dff803a2d7` |
|               | June 30th    | `sha256:4ab1fb23a96504f1524b4d1e9b3804db28c88c78da03ce50aa6d9db40b3ee4d5` |
|               | June 30th    | `sha256:0ce2f6b49f2d14453a7f746d89e601cdb4b6fa30099ef59f81d188882ebf7310` |
|               | June 26th    | `sha256:5dd3e68175ae7656f14ae1645f3a8017c9ca34f2fb05d40f6cb9a55bf7ba75f4` |
|               | June 26th    | `sha256:1a219c040ba7c5fbe8535b54fe1ccef6d4386f0f6efab807d4d8080c65aeef4f` |
|               | June 26th    | `sha256:3815b133f4b6fc2e060c5efa9ff3ed28e1fdb2daf51054135252945de066fef6` |



Minimalist Wolfi-based PHP images for building and running PHP applications. Includes both `dev` and `fpm` variants.

- [Documentation](https://edu.chainguard.dev/chainguard/chainguard-images/reference/php)
- [Getting Started Guide](https://edu.chainguard.dev/chainguard/chainguard-images/reference/php/getting-started-php/)
- [Provenance Information](https://edu.chainguard.dev/chainguard/chainguard-images/reference/php/provenance_info/)

## Image Variants

Our `latest` tags use the most recent build of the [Wolfi PHP](https://github.com/wolfi-dev/os/blob/main/php.yaml) package. The following tagged variants are available without authentication:

- `latest`: This is a distroless image for running command-line PHP applications. It does not include Composer or busybox, so no shell will be available.
- `latest-dev`: This is a development / builder image that includes Composer, apk-tools, and busybox. This variant allows you to customize your final image with additional Wolfi packages.
- `latest-fpm`: This is the distroless `php-fpm` image variant, designed to be used together with our [Nginx](https://edu.chainguard.dev/chainguard/chainguard-images/reference/nginx) image.

### PHP Version
This will automatically pull the image to your local system and execute the command `php --version`:

```shell
docker run --rm cgr.dev/chainguard/php --version
```

You should see output similar to this:

```
PHP 8.2.1 (cli) (built: Jan  1 1970 00:00:00) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.2.1, Copyright (c) Zend Technologies
```

## Application Setup for End Users

When creating a Dockerfile to extend from these images, the recommended approach is to set up a multi-stage build so that you're able to install your Composer dependencies on a separate environment and then copy the files over to a smaller production image.

### CLI Scripts and Applications
The following example demonstrates how to set up a multi-stage Dockerfile build in the context of command line PHP applications:

```Dockerfile
FROM cgr.dev/chainguard/php:latest-dev AS builder
COPY . /app
RUN cd /app && \
    composer install --no-progress --no-dev --prefer-dist

FROM cgr.dev/chainguard/php:latest
COPY --from=builder /app /app

ENTRYPOINT [ "php", "/app/command" ]
```
### Web Applications / APIs
For web applications, you should follow the same principle, but using the `php-fpm` variant for the final image. You'll also need a custom `nginx.conf` file to set up your Nginx service with PHP-FPM.

A good way to test your setup locally is by using [Docker Compose](https://docs.docker.com/compose/compose-file/). The following `docker-compose.yaml` file demonstrates how to create a web server environment using the [Nginx Chainguard Image](https://edu.chainguard.dev/chainguard/chainguard-images/reference/nginx) :

```yaml
version: "3.7"
services:
  app:
    image: cgr.dev/chainguard/php:latest-fpm
    restart: unless-stopped
    working_dir: /app
    volumes:
      - ./:/app
    networks:
      - wolfi

  nginx:
    image: cgr.dev/chainguard/nginx
    restart: unless-stopped
    ports:
      - 8000:80
    volumes:
      - ./:/app
      - ./nginx.conf:/etc/nginx/nginx.conf
    networks:
      - wolfi

networks:
  wolfi:
    driver: bridge
```

You'll notice the Nginx service has a volume share to set up a custom config file. The following `nginx.conf` file sets up Nginx to serve pages from a `/app/public` folder and redirects requests to `.php` files to the `app` service on port `9000`.

```
events {
  worker_connections  1024;
}

http {
    server {
        listen 80;
        index index.php index.html;
        root /app/public;
        location ~ \.php$ {
            try_files $uri =404;
            fastcgi_split_path_info ^(.+\.php)(/.+)$;
            fastcgi_pass app:9000;
            fastcgi_index index.php;
            include fastcgi_params;
            fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
            fastcgi_param PATH_INFO $fastcgi_path_info;
        }
        location / {
            try_files $uri $uri/ /index.php?$query_string;
            gzip_static on;
        }
    }
}
```

For more detailed information on how to use these images, check the [Getting Started with the PHP Chainguard Images](https://edu.chainguard.dev/chainguard/chainguard-images/reference/php/getting-started-php/) guide.

## Detailed Environment Information

To obtain detailed information about the environment, you can run a `php --info` command on any of the image tags and use `grep` to look for a specific module or extension.

For instance, to check for `curl` settings, you can run:

```shell
docker run --rm cgr.dev/chainguard/php:latest --info | grep curl
```


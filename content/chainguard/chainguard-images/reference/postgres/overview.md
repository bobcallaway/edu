---
title: "Image Overview: postgres"
type: "article"
description: "Overview: postgres Chainguard Image"
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

[cgr.dev/chainguard/postgres](https://github.com/chainguard-images/images/tree/main/images/postgres)

| Tag (s)       | Last Changed | Digest                                                                    |
|---------------|--------------|---------------------------------------------------------------------------|
|  `latest`     | July 18th    | `sha256:0aa7e4ee1850d0b692ae99871b7e48cdc0016774441f6d078ba4a1b86e7654f5` |
|  `latest-dev` | July 18th    | `sha256:ef30389fc6b67deb342e683532b64d5ba926d70f86a3847b78338b20eb2dd4db` |



Minimal PostgreSQL image. **EXPERIMENTAL**

## Get It!

The image is available on `cgr.dev`:

```
docker pull cgr.dev/chainguard/postgres:latest
```

## Usage

The only mandatory environment variable needed by the PosgreSQL image is `POSTGRES_PASSWORD`

To test and __not__ persist PostgreSQL data run...
```sh
docker run --rm -e POSTGRES_PASSWORD=password -ti --name postgres-test cgr.dev/chainguard/postgres:latest
```

Alternatively, to persist PostgreSQL data you can mount a volume mapped to the data folder
```sh
docker run --rm -v $PWD/data:/var/lib/postgresql/data -e POSTGRES_PASSWORD=password -ti --name postgres-test cgr.dev/chainguard/postgres:latest
```

In a __new__ terminal exec into the running container and use the PosgreSQL client to create a DB and Table
```sh
docker exec -ti postgres-test bash
```

Connect using the postgres user
```sh
su postgres
```

Create a test DB
```sh
createdb test
```

Connect to the test DB
```sh
psql test
```

Create a table
```sh
CREATE TABLE accounts (
	user_id serial PRIMARY KEY,
	username VARCHAR ( 50 ) UNIQUE NOT NULL,
	password VARCHAR ( 50 ) NOT NULL,
	email VARCHAR ( 255 ) UNIQUE NOT NULL,
	created_on TIMESTAMP NOT NULL,
	last_login TIMESTAMP
);
```

List the tables
```sh
\dt
```

You should see the newly created `accounts` table
```sh
          List of relations
 Schema |   Name   | Type  |  Owner
--------+----------+-------+----------
 public | accounts | table | postgres
(1 row)
```


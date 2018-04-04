## Description

This repository contains the official [Elasticsearch](https://www.elastic.co/products/elasticsearch) Docker image from [Elastic](https://www.elastic.co/).

Documentation can be found on the [Elastic web site](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html).

**Make sure you have read all the instructions properly, just "skimming through" will not help you.**

## Supported Docker versions

The images have been tested on Docker 17.03.1-ce.

## Requirements

A full build and test requires:

- Docker
- GNU Make
- Python 3.5 with Virtualenv

## Contributing, issues and testing

Acceptance tests for the image are located in the test directory, and can be invoked with `make test`.

This image is built on [CentOS 7](https://github.com/CentOS/sig-cloud-instance-images/blob/CentOS-7/docker/Dockerfile).

## How to build for ppc64le arch:
Before building this for `ppc64le`, the first thing we need to do is build
elasticsearch. To do that, pull elasticsearch:
```
https://github.ibm.com/powercloud/elasticsearch
```
Checkout to ppc64le_changes:
```
git checkout ppc64le_changes
```
Build elasticsearch:
```
gradle assemble  # requires version >= 4
```
This creates the required tar.gz file for elasticsearch under `distribution/tar/build/distributions/elasticsearch-5.6.8-SNAPSHOT.tar.gz`.

Copy this tar.gz to elasticsearch-docker:
```
cp /path/to/elasticsearch-5.6.8-SNAPSHOT.tar.gz elasticsearch-docker/build/elasticsearch/elasticsearch-5.6.8.tar.gz
```
That's it, now go to elasticsearch-docker and do:

$ GIT_BRANCH=<BRANCH> make build

e.g:

`$ GIT_BRANCH=5.6 make build`

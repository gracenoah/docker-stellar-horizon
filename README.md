# Stellar Horizon Docker image

[![Docker Build Status](https://img.shields.io/docker/build/satoshipay/stellar-horizon.svg)](https://hub.docker.com/r/satoshipay/stellar-horizon/)

## Docker Hub

The Docker images are published at [satoshipay/stellar-horizon](https://hub.docker.com/r/satoshipay/stellar-horizon/).

## Configuration

All environment variables that Stellar Horizon accepts are supported. You can find out all available options by running `docker run --rm -it satoshipay/stellar-horizon horizon --help`. CLI options are exposed as upper/snake-case environment variables, e.g., `--stellar-core-url` can be set with the `STELLAR_CORE_URL` environment variable.

Make sure to set the following variables:

* `DATABASE_URL`: *Horizon* database URL, e.g., `postgres://horizon-db-host/stellar-horizon`. See also `DATABASE_PASSWORD` below.
* `STELLAR_CORE_DATABASE_URL`: *Stellar Core* database URL, e.g., `postgres://core-db-host/stellar-core`. See also `STELLAR_CORE_DATABASE_PASSWORD` below.
* `STELLAR_CORE_URL`: *Stellar Core* HTTP URL, e.g., `http://core-host:11626`.
* `INGEST`: ingest data from Stellar Core (true/false)

The following environment variables are optional and can be used to provide passwords separately (e.g., via Kubernetes secrets):

* `DATABASE_PASSWORD`: if it is provided the string `DATABASE_PASSWORD` in `DATABASE_URL` will be replaced with its value.
* `STELLAR_CORE_DATABASE_PASSWORD`: if it is provided the string `STELLAR_CORE_DATABASE_PASSWORD` in `STELLAR_CORE_DATABASE_URL` will be replaced with its value.

### Docker Compose

There is also an [example Docker Compose config](docker-compose.example.yml) – just run
`docker-compose -f docker-compose.example.yml up` to get a functional Stellar Core and Horizon.
**Make sure to use a new `NODE_SEED` if you intend to run this in production!*

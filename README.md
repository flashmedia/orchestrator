# Orchestrator

This repository contains Alpine Linux based Docker images that have been configured to run a Consul cluster via Docker Cloud.

These images are intended to be used to run a Consul cluster for specific web applications. They've been designed around specifics involved in running on Docker Cloud.

These images are used through all Idearium projects that run on Docker Cloud.

The images that are available through this project repository are:

- `flashmedia/conductor`
- `flashmedia/consul`
- `flashmedia/consului`

## Base images

For more info about the base images used in these images please checkout [docker-alpine](https://github.com/smebberson/docker-alpine)

## Development

To develop these images, please see the [development](./DEVELOPMENT.md) guide.

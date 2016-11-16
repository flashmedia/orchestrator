# Orchestrator

This repository contains Alpine Linux based Docker images that have been configured to run a Consul cluster via Docker Cloud.

These images are intended to be used to run a Consul cluster for specific web applications. They've been designed around specifics involved in running on Docker Cloud.

These images are used through all Idearium projects that run on Docker Cloud. The images that are available through this project repository are:

- `flashmedia/consul`
- `flashmedia/consului`

## Testing

There are two targets for testing and running these images, locally for development and Docker Cloud.

The `docker-compose.yml` and `stack.yml` file demonstrate how to configure a complete application using these images. They include other containers such as Node.js to demonstrate how they should be used in a real project. These other non-core images can be found in `./testing`.

### Locally

To run locally, use `c up` which uses `docker-compose.yml` for orchestration.

### Docker Cloud

To run on Docker Cloud, create a new node and run the `stack.yml` file.

## Base images

For more info about the base images used in these images please checkout [docker-alpine](https://github.com/smebberson/docker-alpine)

## Development

To develop these images, please see the [development](./DEVELOPMENT.md) guide.

## Production

These images are pushed to production by simply tagging and pushing to GitHub. Docker Cloud will pick up on these tags and automatically build the images remotely.

There are two tags used to initiate automated builds:

- `consul-vx.x.x` will build the `consul` image.
- `consului-vx.x.x` will build the `consului` image.

Whenever one of, or both of these tags are pushed, Docker Cloud will create an image with the same tag as the version, and a `latest`. For example, pushing a GitHub tag of `consul-v2.0.0` will produce `flashmedia/consul:2.0.0` and `flashmedia/consul:latest`.

`latest` is just a convenience which can be used in stack files, but should never be used in a Dockerfile (as these images are).

# Orchestrator

This repository contains Alpine Linux based Docker images that have been configured to run a Consul cluster via Docker Cloud.

These images are intended to be used to run a Consul cluster for specific web applications. They've been designed around specifics involved in running on Docker Cloud.

These images are used through all Idearium projects that run on Docker Cloud. The images that are available through this project repository are:

- `flashmedia/conductor`
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

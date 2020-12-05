# Architecture

> Docker uses a client-server architecture. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers.

## Docker daemon

The Docker daemon (`dockerd`) listens for Docker API requests from client and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.

## Docker client

The Docker client (`docker`) is the primary way that many Docker users interact with Docker. When you use commands such as `docker run`, the client sends these commands to `dockerd`, which carries them out.

The Docker client and daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon. The Docker client and daemon communicate using a REST API, over UNIX sockets or a network interface. This make Docker client able communicate with more than one daemon.

## Docker registries

A Docker registry stores Docker images. [Docker Hub](https://hub.docker.com) is a **public** registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. You can even run your own **private** registry.

## Diagram

![Docker architecture](assets/architecture.svg)

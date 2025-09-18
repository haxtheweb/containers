# containers

Containerization of HAXTheWeb dev environments and deployments — containers in hax land

## Project Overview

This repository provides Docker Compose configurations for both a simple hosting environment and a full-featured development environment for HAXTheWeb.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/)

## Usage

### Simple Host

To run a single, unmanaged site:

```sh
docker compose up -d simplehost
```

- Access your site at [http://localhost:8000](http://localhost:8000)
- Data is persisted in the `simplehost_data` volume.

### Developer Environment

To start the full-featured dev environment:

```sh
docker compose up -d devenv
```

- Access your dev environment at [http://localhost:8001](http://localhost:8001)
- Data is persisted in the `devenv_data` volume.

### Stopping and Removing Containers

```sh
docker compose down
```

## Services

- **simplehost**: Minimal environment for hosting a single site.
- **devenv**: Full dev environment with extra tools and utilities.

## Example Commands

- Build images: `docker compose build`
- View running containers: `docker compose ps`
- View logs: `docker compose logs <service>`

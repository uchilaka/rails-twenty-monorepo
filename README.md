# rails-twenty-monorepo

This is a monorepo concept for a Rails project, integrated with an instance of the Twenty CRM and managed with pnpm workspaces. It contains multiple packages and scripts for development, testing, and deployment.

## Project Structure

- `docker-compose.yml` — Top-level Docker Compose configuration for the monorepo.
- `package.json` — Root package configuration, including workspace settings.
- `pnpm-workspace.yaml` — pnpm workspace configuration file.
- `packages/` — Contains all project packages.
  - `twenty-crm/` — Example package (CRM service), may contain its own `docker-compose.yml` and codebase.
- `scripts/` — Utility scripts for managing the monorepo.
  - `list` — List packages or services.
  - `start` — Start services or development environment.
  - `teardown` — Stop and clean up services.

## Getting Started

The Twenty container uses port `16016` by default.

### Prerequisites

- [Node.js](https://nodejs.org/) (recommended: latest LTS)
- [pnpm](https://pnpm.io/) (for workspace management)
- [Docker](https://www.docker.com/) (for running services)

### Install Dependencies

```shell
pnpm install
```

### Running Services

To start all services using Docker Compose:

```shell
docker-compose up
```

Or use the provided scripts in the `scripts/` directory:

```shell
./scripts/start
```

### Stopping Services

```shell
./scripts/stop
```

Or:

```shell
./scripts/teardown
```

### Listing Packages/Services

```shell
./scripts/list
```

## Contributing

1. Fork the repository and create your branch from `main`.
2. Make your changes and add tests if applicable.
3. Commit your changes and push your branch.
4. Open a pull request.

## License

This project is licensed under the MIT License.

# rails-twenty-monorepo

This is a monorepo for the Twenty CRM project and related packages. It uses [pnpm](https://pnpm.io/) for package management and includes Docker Compose configurations for local development.

## Repository Structure

```shell
rails-twenty-monorepo/
|── .env.development             # Sample ENV file
|── .env.development.local       # Create this file to set ENV variables 
├── docker-compose.yml           # Root Docker Compose file
├── package.json                 # Root package.json for pnpm
├── pnpm-workspace.yaml          # pnpm workspace configuration
├── README.md                    # This file
└── packages/
    └── twenty-crm/
        ├── .env                # Service-specific ENV file
        └── data/
            └── development/
                └── postgres/
                    └── downloads/
```

## Getting Started

### Prerequisites

-- [Node.js](https://nodejs.org/) (recommended: latest LTS)
-- [pnpm](https://pnpm.io/) (for workspace management)
-- [Docker Compose](https://docs.docker.com/compose/) (for running services)

### Install Dependencies

```shell
pnpm install
```

### Setting up `direnv`

When the `direnv` library is working correctly, the output resemples this after `cd` into the project root:

```shell
direnv: loading ~/repos/sandbox/rails-twenty-monorepo/.envrc
🛠️ Loading /Users/uche/repos/sandbox/rails-twenty-monorepo/.env.development
🛠️ Loading /Users/uche/repos/sandbox/rails-twenty-monorepo/.env.development.local
🛠️ Loading /Users/uche/repos/sandbox/rails-twenty-monorepo/packages/twenty-crm/.env
direnv: export +APP_SECRET +CRM_SERVICE_PORT +NODENV_VERSION +PG_DATABASE_PASSWORD +PROJECT_ROOT +RAILS_ENV +SERVER_URL +STORAGE_TYPE +TAG
```

### Running Services

To start all services defined in the root Docker Compose file:

```shell
.docker/bin/start
```

### Setting up the local user role

```shell
# View your local user account (e.g. beck)
echo "$USER"

# Set your database user
DBUSER="${PG_DATABASE_USER:-postgres}"

# View your database login user (e.g. postgres)
echo "$DBUSER"

# Check your postgres container name (e.g. twenty-db-1)
docker compose --profile all ps -a

# View the command help menu
docker exec -it twenty-db-1 createuser --help

# Create a role for your local user
docker exec -it twenty-db-1 createuser \
  --createdb --no-createrole --superuser $USER \
  --host 127.0.0.1 --username $DBUSER
```

### Creating a new database backup

```shell
scripts/backup
```

### Restoring from the database backup

You should be able to access the app after performing a DB restore with the following credentials:

- username: `developer@fake.email`
- password: `Test1234`

After a successful login, you should have a "Acme Inc." company.

## Workspace Packages

- `packages/twenty-crm/`: Main CRM application and related resources.

## Notes

- A local Postgres resource directory for the `development` environment is mounted from `packages/twenty-crm/data/development/postgres/downloads/`. This can be used to load files into the postgres container
- Add additional packages under the `packages/` directory as needed.

---
For more details, see individual package README files (if present).


# Servicefront Rails Application

This is the **Servicefront** Rails application, managed as a package within the [rails-twenty-monorepo](../../) Yarn workspace. It is a modern Rails app with integrated frontend tooling, designed to work seamlessly alongside other packages in the monorepo.

## Project Structure

- **Monorepo root:** Contains shared configuration, scripts, and workspace management via Yarn.
- **This package:** All Rails backend and frontend code for Servicefront lives here.

## Getting Started

### Prerequisites

- Ruby (see `.ruby-version` or Gemfile for version)
- Node.js & Yarn (for JS dependencies and workspace management)
- PostgreSQL (or your configured database)

### Setup

#### 1. Install dependencies

- From the monorepo root:

    ```sh
    yarn install
    ```

- From this package directory:

    ```sh
    bundle install
    yarn install
    ```

#### 2. Database setup

- Create and migrate the database:

  ```sh
  bin/rails db:setup
  ```

#### 3. Start the app (development)

- Run Rails and frontend (Vite) in parallel:

   ```sh
   bin/dev
   ```

## Useful Commands

- `bin/rails` – Rails CLI
- `bin/dev` – Starts Rails and Vite for development
- `bin/vite` – Vite frontend bundler
- `bin/rake` – Rake tasks

## Configuration

- App configuration: `config/`
- Database config: `config/database.yml`
- Environment variables: `.env` or system environment

## Development

- Review the Rails guide on [working with Active Record using multiple databases](https://guides.rubyonrails.org/active_record_multiple_databases.html).

## Testing

Run the test suite with:

```sh
bin/rails test
```

## Deployment

Deployment is managed via the monorepo. See the root `README.md` and deployment scripts for details.

## Monorepo & Yarn Workspace

This Rails app is part of a Yarn workspace. Shared dependencies and scripts are managed at the monorepo root. Use `yarn workspaces` commands from the root to manage all packages.

---

For more details, see the monorepo [README](../../README.md).

- Deployment instructions

- ...

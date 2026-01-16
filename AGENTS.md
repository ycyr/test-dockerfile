# Repository Guidelines

## Project Structure & Module Organization
This is a Laravel 12 application with Vite/Tailwind assets and optional Docker setups.
- `app/` application code (controllers, models, jobs, etc.).
- `routes/` HTTP routes; `config/` framework and app configuration.
- `resources/` Blade views and frontend assets; built output goes to `public/`.
- `database/` migrations, factories, and seeders; runtime state in `storage/`.
- `tests/` Pest/PhpUnit tests (`tests/Unit`, `tests/Feature`).
- `docker/` custom images; `compose.dev.yaml`, `compose.prod.yaml`, `compose.yaml` for containerized runs.
- `vendor/` and `node_modules/` are generated dependencies.

## Build, Test, and Development Commands
- `composer run setup` installs PHP/JS deps, creates `.env`, generates key, runs migrations, and builds assets.
- `composer run dev` starts Laravel server, queue worker, log tailing, and Vite dev server concurrently.
- `composer run test` clears config cache and runs the test suite.
- `npm run dev` runs Vite in watch mode; `npm run build` builds production assets.
- Docker: `docker compose -f compose.dev.yaml up --build` for a full dev stack; use `compose.prod.yaml` for production-like runs. `compose.yaml` is Laravel Sail oriented.

## Coding Style & Naming Conventions
- PHP follows Laravel conventions and PSR-12; use 4 spaces and no tabs.
- Format PHP with `./vendor/bin/pint`.
- Class names are StudlyCase, methods/functions are camelCase, and migrations are descriptive (e.g., `create_users_table`).
- Frontend code lives in `resources/` and is built by Vite; follow the existing file’s style.

## Testing Guidelines
- Tests run through Pest/PhpUnit via `php artisan test` or `composer run test`.
- Place unit tests in `tests/Unit` and integration/HTTP tests in `tests/Feature`.
- Name tests `*Test.php` (e.g., `UserTest.php`).

## Commit & Pull Request Guidelines
- Commit messages are short, imperative, and scoped to a single change (e.g., “Fix CI build”).
- PRs should include a brief summary, test results, and links to related issues; include screenshots for UI changes.
- Call out configuration changes (e.g., `.env`, `compose*.yaml`, or Dockerfiles).

## Security & Configuration Tips
- Copy `.env.example` to `.env` and keep secrets out of Git.
- When using Docker, set ports and credentials via environment variables in `.env` or your shell.

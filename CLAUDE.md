# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

### Initial Setup
```bash
composer run setup
```
This runs: `composer install`, creates `.env`, generates `APP_KEY`, runs migrations, `npm install`, and `npm run build`.

### Development
```bash
composer run dev
```
Concurrently starts: Laravel server (`php artisan serve`), queue worker, Pail log viewer, and Vite dev server.

### Testing
```bash
composer run test          # Clear config cache + run all tests
php artisan test --filter TestName   # Run a single test
```

### Linting / Code Style
```bash
./vendor/bin/pint          # Laravel Pint (PHP code style fixer)
```

### Frontend
```bash
npm run dev    # Vite dev server with HMR
npm run build  # Production build
```

### Database
```bash
php artisan migrate
php artisan migrate:fresh --seed
```

## Architecture

**Servi** is a Laravel 12 application configured for MySQL with a standard MVC structure. The project is in early development — custom application code is minimal.

### Key Configuration
- **Database:** MySQL (`servi` database, root user). Configured in `.env`.
- **Session, Queue, Cache:** All use the `database` driver (tables created in migrations).
- **String length fix:** `AppServiceProvider` sets `Schema::defaultStringLength(191)` globally — required for MySQL with utf8mb4 on older engines.
- **Frontend:** Tailwind CSS v4 + Axios via Vite. Entry points are `resources/css/app.css` and `resources/js/app.js`.
- **Local URL:** `http://servi.local`

### Non-standard Directory
- `bodega/` — personal development notes (gitignored, not part of the application).

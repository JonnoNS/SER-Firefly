# Firefly III Project Context

## Project Overview
Firefly III is a free and open-source self-hosted personal finance manager. It helps users track expenses, income, budgets, and categories.

**Key Technologies:**
*   **Language:** PHP 8.4
*   **Framework:** Laravel 12
*   **Frontend:**
    *   **Workspace v2:** Vite, Bootstrap 5, Alpine.js, Chart.js, AdminLTE 4.
    *   **Templating:** Blade / Twig (via `twigbridge`).
*   **Database:** MySQL, PostgreSQL, or SQLite (SQLite used by default for testing).

## Building and Running

### Backend (PHP/Laravel)
1.  **Install Dependencies:**
    ```bash
    composer install
    ```
2.  **Configuration:**
    *   Copy `.env.example` to `.env`.
    *   Generate application key:
        ```bash
        php artisan key:generate
        ```
3.  **Database Setup:**
    ```bash
    php artisan migrate --seed
    ```
4.  **Serve Application:**
    ```bash
    php artisan serve
    ```

### Frontend (Assets)
The frontend assets are managed in workspaces. For the latest version (v2):
1.  **Navigate to directory:**
    ```bash
    cd resources/assets/v2
    ```
2.  **Install Dependencies:**
    ```bash
    npm install
    ```
3.  **Build for Production:**
    ```bash
    npm run build
    ```
4.  **Development Server:**
    ```bash
    npm run dev
    ```

## Testing & Quality Assurance

### PHPUnit (Backend Tests)
Configuration is in `phpunit.xml`. It defaults to using an in-memory SQLite database.

*   **Run All Tests:**
    ```bash
    vendor/bin/phpunit
    ```
*   **Run Unit Tests:**
    ```bash
    composer unit-test
    # or
    vendor/bin/phpunit --testsuite unit
    ```
*   **Run Integration Tests:**
    ```bash
    composer integration-test
    # or
    vendor/bin/phpunit --testsuite integration
    ```

### Static Analysis & Linting
*   **PHPStan:** Configured in `phpstan.neon` (or via composer scripts).
*   **Rector:** Used for automated refactoring (`rector.php`).
*   **Code Style:** `php-cs-fixer` is present in `.ci/php-cs-fixer`.

## Directory Structure Highlights
*   `app/`: Core application logic (Models, Http, Services).
*   `config/`: Application configuration files.
*   `database/`: Migrations, factories, and seeders.
*   `resources/assets/`: Frontend asset source code (divided into `v1` and `v2`).
*   `tests/`: Unit, Feature, and Integration tests.
*   `.ci/`: CI/CD scripts and configuration.

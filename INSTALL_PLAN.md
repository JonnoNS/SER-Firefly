# Firefly III Local Installation Plan

## 1. Prerequisites
*   **Node.js & NPM:** Installed (Verified).
*   **Docker:** Installed (Verified).
*   **PHP 8.4:** Not present on host. We will use Docker.

## 2. Configuration
*   `.env` file created from `.env.example`.
*   `docker-compose.dev.yml` created to provide PHP 8.4 + MariaDB.

## 3. Installation Steps

### Frontend (Host)
Dependencies are installed. Build the assets:
```bash
npm run build
```

### Backend (Docker)
Start the environment (requires sudo if user is not in docker group):
```bash
sudo docker compose -f docker-compose.dev.yml up -d
```

Install PHP dependencies inside the container:
```bash
sudo docker compose -f docker-compose.dev.yml exec app composer install
```

### Database Setup
Run migrations and seed the database:
```bash
sudo docker compose -f docker-compose.dev.yml exec app php artisan migrate --seed
```

Generate App Key (if not set):
```bash
sudo docker compose -f docker-compose.dev.yml exec app php artisan key:generate
```

## 4. Launch
Access the application at: **http://localhost:8080**

# Use Docker to run Next.js and Laravel with postgreSQL and Caddy as reverse proxy

This project is a template to use Docker to run Next.js and Laravel with postgreSQL and Caddy as reverse proxy.

Warning: This project is not intended for production use. Please adapt it before using it in production.

## Architecture

```plaintext
/
|-- backend/
|   |-- ... (fichiers Laravel)
|   |-- .env
|   |-- Dockerfile
|-- app/
|   |-- ... (fichiers Next.js)
|   |-- .dockerignore
|   |-- Dockerfile
|-- Caddyfile
|-- docker-compose.yml
|-- README.md
```

## Requirements

- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Configuration

In the backend directory:

1. Copy the `.env.example` file

```bash
cp .env.example .env
```

2. Adapt the following variables according to your needs:

```env
DB_CONNECTION=pgsql
DB_HOST=db
DB_PORT=5432
DB_DATABASE=laravel
DB_USERNAME=laravel
DB_PASSWORD=laravel
```

## Installation

In the root directory (docker-compose.yml):

1. Execute the following command to build the images:

```bash
docker compose up -d --build
```

This command will build the images and start the containers in the background.

2. Execute the following command to add a secret key to the Laravel project:

```bash
docker compose exec laravel php artisan key:generate
```

3. Execute the following command to migrate the database:

```bash
docker compose exec laravel php artisan migrate
```

## Current Usage

In the root directory (docker-compose.yml):

Execute the following command to start the containers:

```bash
docker compose up -d
```

This command will start the containers in the background and leave them running.

To check the status of the containers, execute the following command:

```bash
docker compose ps
```

To stop the containers, execute the following command:

```bash
docker compose down
```

This command will stop the containers and remove them, but it will keep the data in the volumes.

To show the logs of the containers, execute the following command:

```bash
docker compose logs -f
```

When the containers are running, you can access the following URLs:

- [Laravel](http://localhost:8000)
- [Next.js](http://localhost:3000)
- [pgAdmin](http://localhost:5050)

## Other useful commands:

To install the dependencies of the Laravel project, execute the following command:

```bash
docker compose exec laravel composer install
```

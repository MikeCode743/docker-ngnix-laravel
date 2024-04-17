
# Docker - Laravel project

Comand




## Installation

Install dependencies with composer and initial Installation

```bash
docker-compose up -d

docker compose exec backend composer install

docker compose exec backend cp .env.example .env

docker compose exec backend php artisan key:generate

```
    
Granting permissions

```bash
docker compose exec backend bash

chown -R $USER:www-data storage
chown -R $USER:www-data bootstrap/cache
chmod -R 775 storage
chmod -R 775 bootstrap/cache

docker compose exec backend chmod o+w ./storage/ -R

```

Initialization
```bash
docker compose exec backend php artisan optimize:clear

docker compose exec backend php artisan storage:link

docker compose exec backend php artisan migrate --seed
```

Utility

```bash
docker compose exec backend php artisan migrate:fresh
docker compose exec backend php artisan db:seed
docker compose exec backend php artisan route:list

```

CREATE 

```bash
docker compose exec backend php artisan make:migration
docker compose exec backend php artisan make:seed
docker compose exec backend php artisan make:model
docker compose exec backend php artisan make:controller Api/
```



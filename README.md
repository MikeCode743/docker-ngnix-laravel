
# Docker - Laravel project

Comand




## Installation

Install dependencies with composer and initial Installation

```bash
docker compose up -d

docker compose exec backend composer Install

docker compose exec backend mv .env.example .env

docker compose exec backend php artisan key:generate

```
    
Granting permissions

```bash
docker compose exec backend bash

docker compose exec backend chown -R $USER:www-data storage
docker compose exec backend chown -R $USER:www-data bootstrap/cache
docker compose exec backend chmod -R 775 storage
docker compose exec backend chmod -R 775 bootstrap/cache
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
docker compose exec backend php artisan make:model
docker compose exec backend php artisan make:controller Api/
docker compose exec backend php artisan make:seed
docker compose exec backend php artisan make:migrate

docker compose exec backend php artisan route:list

```



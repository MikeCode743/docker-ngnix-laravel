
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

sudo chown -R $USER:www-data storage
sudo chown -R $USER:www-data bootstrap/cache
sudo chmod -R 775 storage
sudo chmod -R 775 bootstrap/cache

```

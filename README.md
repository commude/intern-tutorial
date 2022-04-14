# laravel-todo

## Requirements
- PHP 8.1.2
- Laravel 9.7.0
- Any database system
- Composer 2.x
- Npm 7.21 (or anything near) & yarn
- Other PHP extension

## Environment
- Docker & Docker Compose
- Nginx 
- MySQL 5.7

## Directory Structure

```bash
├─docker (Docker Image builder)
│  ├─nginx
│  │  ├─conf
│  │  │   ├─conf.d
│  │  │   │   ├─default-local.conf
│  │  │   │   └─dedault-production.conf
│  │  │   └─nginx.conf
│  │  └─dockerfile
│  │
│  └─php-fpm
│     ├─conf
│     │   └─php.ini 
│     └─dockerfile 
│      
├─environments (Docker Composer environments)
│  └─local
│     ├─.env.example
│     └─docker-compose.yml
│
└─src (Laravel App)
    ├─app
    ├─bootstrap
    ├─config
    ├─database
    ├─node_modules
    ├─public
    ├─resources
    ├─routes
    ├─storag
    ├─tests
    ├─vendor
    ├─.env.example
    ├─artisan
    ├─composer.json
    ├─composer.lock
    ├─package-lock.json
    ├─package.json
    ├─phpunit.xml
    ├─README.md
    ├─server.php
    └─webpack.mix.js
```

## Setup
1. Build docker image first.

```bash
cd environments/local
cp .env.example .env
docker-compose build
```

2. Create Containers

```bash
docker-compose up -d
```

3. Entering the Container&Install libraries

```bash
docker exec -it laravel-todo.php-fpm bash
```

local %  →→　　bash-4.2#

```bash
composer install
```

4. Make & edit .env

```bash
cp .env.example .env
php artisan key:generate
```

Edit the .env under src folder
```
APP_URL=http://localhost
ASSET_URL=http://localhost
MIX_ASSET_URL=http://localhost
↓
APP_URL=http://localhost:8081
ASSET_URL=http://localhost:8081
MIX_ASSET_URL=http://localhost:8081



DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=
↓
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel-todo_db
DB_USERNAME=root
DB_PASSWORD=mysql



UNDER_CONSTRUCTION_ENABLED=
UNDER_CONSTRUCTION_HASH=
↓
UNDER_CONSTRUCTION_ENABLED=false
UNDER_CONSTRUCTION_HASH=



LOG_CHANNEL=stack
↓
LOG_CHANNEL=daily
```


save

```bash
php artisan config:cache
```
display
Configuration cache cleared!
Configuration cached successfully!

```bash
php artisan route:cache
```
display
Route cache cleared!
Routes cached successfully!


Preparing db
```bash
php artisan migrate
php artisan db:seed
```

refresh db
```bash
php artisan migrate:fresh --seed
```


５. Access your localhost:8081



## Preparing db
1. php artisan migrate:fresh
2. php artisan db:seed

## Access site
### user 
[http://localhost:8081](http://localhost：8081)
```bash
user : undecided(users Table の email)
password : undecided（password）
```



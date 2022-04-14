# laravel-todo

## Requirements
- PHP 7.4.26
- Any database system
- Composer 2.x
- Npm 7.21 (or anything near) & yarn
- Other PHP extension

## Environment
- Docker & Docker Compose
- apache 
- MySQL 5.7

## Directory Structure

```bash
├─docker (Docker Image builder)
│  └─amazonlinux2
│     └─conf
│     │   └─http.conf
│     │   └─supervisord.conf
│     └─dockerfile
│      
├─environments (Docker Composer environments)
│  └─local
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

4. Make .env

```bash
cp .env.example .env
php artisan key:generate
```

Edit the .env under src folder
```
APP_URL=http://localhost
ASSET_URL=http://localhost/assets
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

5. Install node modules and generate css/js files using yarn
Out of the container
```bash
exit
```
bash-4.2# →→ local % 

```bash
cd ../../src
npm install -g yarn       # execute this command if you don't have yarn installed yet.
yarn
yarn install
yarn dev #or yarn watch
```

6. Access your localhost:8081



## Preparing db
1. php artisan migrate:fresh
2. php artisan insert:code
3. php artisan insert:coupon
4. php artisan db:seed
5. 

## サイトにアクセス

### user
[http://localhost：８０８１/login](http://localhost：８０８１/login)
```
user : undecided(users Table の email)
password : undecided（password）
```

### admin
[http://localhost:8081/LS_Cmd_2022-06/login](http://localhost:8081/LS_Cmd_2022-06/login)

```
user : 
admin@admin.com 
password : 
password


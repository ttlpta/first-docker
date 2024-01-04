# Introduction
This project demo how to Dockerize Laravel realtime chat app
# Features
- Realtime chat app using Private and Presence channel in Laravel
- Schedule task
- Laravel Horizon
- Laravel Worker

# How to run
Docker and Docker-compose are required

Run the command:
```
cp .env.example .env
```

Open **.env** file and change the following sections:
```
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=laraveluser
DB_PASSWORD=laraveluserpass

BROADCAST_DRIVER=redis
CACHE_DRIVER=redis
QUEUE_CONNECTION=redis
SESSION_DRIVER=redis
SESSION_LIFETIME=120

REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379

....

LARAVEL_ECHO_SERVER_REDIS_HOST=redis
LARAVEL_ECHO_SERVER_REDIS_PORT=6379
LARAVEL_ECHO_SERVER_AUTH_HOST=http://webserver:80
LARAVEL_ECHO_SERVER_DEBUG=true

APP_PORT=4000
MIX_FRONTEND_PORT=4000
ADMINER_PORT=8080
```

Next, run the following commands:
```
docker run --rm -v $(pwd):/app -w /app composer install --ignore-platform-reqs --no-autoloader --no-dev --no-interaction --no-progress --no-suggest --no-scripts --prefer-dist

docker run --rm -v $(pwd):/app -w /app composer dump-autoload --classmap-authoritative --no-dev --optimize

docker run --rm -v $(pwd):/app -w /app node npm install --production

docker run --rm -v $(pwd):/app -w /app node npm run prod
```

Then run commands:
```
docker-compose exec app php artisan key:generate

docker-compose exec app php artisan migrate --seed
```

Finally open browser at **localhost:4000** an enjoy :)

> To visualize database open browser at **localhost:8080**
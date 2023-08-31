# Introduction
This repository serves as a foundational project designed to streamline the configuration process for the following components:
- PHP 8.1
- Apache web server
- PHP Composer
- SSL
- Remote XDebug
- Mariadb
- PHPMyAdmin

## Build images and launch containers
```
docker-compose up -d
```

## Stop but keep the container
```
docker-compose stop
```
## Stops containers and removes containers
```
docker-compose down
```

## Rebuild the images
```
docker-compose up -d --build
```

## Prune dangling images
```
docker image prune
```

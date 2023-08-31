# Usage

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
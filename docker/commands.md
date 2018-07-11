# commands

## docker

Create image using this directory's Dockerfile

```text
docker build -t friendlyname .
```

Run "friendlyname" mapping port 4000 to 80

```text
docker run -p 4000:80 friendlyname
```

Same thing, but in detached mode

```text
docker run -d -p 4000:80 friendlyname
```

Enter a running container

```text
docker exec -it [container-id] bash
```

See a list of all running containers

```text
docker ps
```

Gracefully stop the specified container

```text
docker stop <hash>
```

See a list of all containers, even the ones not running

```text
docker ps -a
```

Force shutdown of the specified container

```text
docker kill <hash>
```

Remove the specified container from this machine

```text
docker rm <hash>
```

Remove all containers from this machine

```text
docker rm $(docker ps -a -q)
```

Show all images on this machine

```text
docker images -a
```

Remove the specified image from this machine

```text
docker rmi <imagename>
```

Remove all images from this machine

```text
docker rmi $(docker images -q)
```

Log in this CLI session using your Docker credentials

```text
docker login
```

Tag &lt;image&gt; for upload to registry

```text
docker tag <image> username/repository:tag
```

Upload tagged image to registry

```text
docker run username/repository:tag
```

Inspect container

```text
docker inspect 1f438fbe6049
```

Get specific setting from container

```text
docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' 1f438fbe6049
```

Run image from a registry

```text
docker push username/repository:tag
```

## docker-compose

Create and start containers

```text
docker-compose up
```

Create and start containers in detached mode

```text
docker-compose up -d
```

Stop and remove containers, networks, images, and volumes

```text
docker-compose down
```

View output from containers

```text
docker-compose logs
```

Restart all service

```text
docker-compose restart
```

Pull all image service 

```text
docker-compose pull
```

Build all image service

```text
docker-compose build
```

Validate and view the Compose file

```text
docker-compose config
```

Scale special service\(s\)

```text
docker-compose scale <service_name>=<replica>
```

Display the running processes

```text
docker-compose top
```

Pass environment arguments to docker-compose

```text
### powershell (windows)
$env:BUILD_BUILDNUMBER="666";docker-compose -f docker-compose.yml up
### linux
BUILD_BUILDNUMBER=666 docker-compose -f docker-compose.yml up
```




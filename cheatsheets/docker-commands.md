# Docker Container Commands for Beginners

This README gives a quick, beginner-friendly reference for common Docker **container** commands. Most of these commands work with either a container **name** or **ID**, and `docker run` creates and starts a new container from an image.[1][2]

## Basic idea

A Docker **image** is the template, and a Docker **container** is the running instance created from that image.[2] When you use `docker run`, Docker can pull the image first if it is not already available locally.[1]

## Create and run containers

### Run a container

```bash
docker run image_name
```

Creates and starts a new container from the given image.[1][2]

### Run a container with a custom name

```bash
docker run --name container_name image_name
```

Creates the container and assigns a readable name instead of using a random one.[1]

### Run a container with port mapping

```bash
docker run --name container_name -p host_port:container_port image_name
```

Maps a port on your host machine to a port inside the container so you can access the application from outside the container.[1][3]

### Run in detached mode

```bash
docker run -d image:tag
```

Starts the container in the background, which is useful for servers and services.[1][3]

### Run in interactive mode

```bash
docker run -it image_name
```

Starts the container in interactive mode and attaches your terminal to it, which is useful when you want to work inside the container directly.[1]

> Note: use `-it`, not `it`.

## Connect to a running container

### Attach to a container

```bash
docker attach container_id_or_name
```

Attaches your terminal to the main process of a running container.[4]

### Execute a command in a running container

```bash
docker exec container_id_or_name <command>
```

Runs a new command inside an already running container.[5]

### Open a shell inside a running container

```bash
docker exec -it container_id_or_name /bin/bash
```

Opens an interactive Bash shell inside the container, if Bash is installed.[5][6]

If Bash is not available, try:

```bash
docker exec -it container_id_or_name /bin/sh
```

Many minimal images use `sh` instead of `bash`.[6]

## List containers

### Show running containers

```bash
docker ps
```

Lists currently running containers.[7][4]

### Show all containers

```bash
docker ps -a
```

Lists all containers, including stopped ones.[7][4]

## Stop and remove containers

### Stop a container

```bash
docker stop container_id_or_name
```

Stops a running container gracefully.[4]

### Remove a container

```bash
docker rm container_id_or_name
```

Deletes a container that you no longer need.[4]

> In most cases, you must stop the container before removing it.[4]

### Rename a container

```bash
docker rename old_container_name new_container_name
```

Changes the name of an existing container.[4]

## Work with images

### Pull an image without running it

```bash
docker pull image_name
```

Downloads an image from a registry, such as Docker Hub, without creating a container.[1][2]

### Remove an image

```bash
docker rmi image_id_or_name
```

Deletes an image from your local system if it is no longer needed.[8]

## Useful beginner additions

### Start an existing stopped container

```bash
docker start container_id_or_name
```

Starts a container that already exists but is currently stopped.[4]

### Restart a container

```bash
docker restart container_id_or_name
```

Stops and starts the container again.[4]

### View container logs

```bash
docker logs container_id_or_name
```

Shows the logs produced by the container, which is helpful for troubleshooting.[4]

### Remove a stopped container immediately

```bash
docker rm -f container_id_or_name
```

Force-removes a container by stopping it and deleting it in one step.[4]

## Quick example

```bash
docker pull nginx
docker run --name my-nginx -d -p 8080:80 nginx
docker ps
docker logs my-nginx
docker stop my-nginx
docker rm my-nginx
```

This example pulls the `nginx` image, runs it in the background, maps host port `8080` to container port `80`, checks the running container, views logs, then stops and removes it.[1][3][7]

## Common mistakes

- Use `docker run -it image_name`, not `docker run it image_name`.[1]
- Use `container_id_or_name` as a placeholder; either value works in many Docker container commands.[4]
- `docker exec` works only when the target container is already running.[5]
- `docker ps` shows running containers, while `docker ps -a` shows both running and stopped containers.[7][4]
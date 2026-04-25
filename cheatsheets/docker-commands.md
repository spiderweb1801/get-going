docker run image_name --> create a container
docker run --name container_name image_name
docker run --name container_name -p host_port:container_port image_name
docker run -d image:tag --> in dettach mode
docker attach container_id/container_name
docker run it image--> interactive/logged into the container while running it
docker exec container_id/container_name <command> --> executing <command> in the container
docker ps
docker ps -a
docker stop container_id/container_name
docker rm container_id/container_name
docker rmi image_id/image_name
docker pull image --> pull the image from docker repo without running the container
docker rename old_container_name new_container_name
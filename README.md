## Docker Getting Started
---
### Useful Commands
- Build the docker image
`docker build -t <container-name> .`
- Run an instance (ie container) of the built image
`docker run -dp 3000:3000 <container-name>`
- Browse to `localhost:3000` and enjoy

### Persist data
#### Volumes
- Named Volumes
  - Create a named volume as `docker volume create <volume-name>`
  - Run the container with the named volume as `docker run -dp 3000:3000 -v <volume-name>:<data-dir-in-container> <container-name>`
- Bind Mounts
  - Choose a location from where data to persist go. It is common for local development environment.
#### Networks
With more than one container, we need networks to make containers to communicate.
- create a network as `docker network create <network-name>`
- Run another container with the created network, for instance mysql as`docker run -d \
    --network todo-app --network-alias mysql \
    -v todo-mysql-data:/var/lib/mysql \
    -e MYSQL_ROOT_PASSWORD=secret \
    -e MYSQL_DATABASE=todos \
    mysql:5.7`
### Using Docker Compose
Is a tool more adapted to multi-container applications. It consists of creating a yml file where to define the services and with a single command, can spin everything up or tear it all down.
- Run containers with `docker compose up -d`
- Down containers with `docker compose down`

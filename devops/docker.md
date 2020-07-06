# Docker

## Installation

See [Getting Started](https://www.docker.com/get-started).

## Docker Hub

Contains open-sourced images. See [Docker Hub](https://hub.docker.com/search?q=&type=image).

## Crash Start on Dockerfile

Docker container for creating and including images.

```text
$ touch Dockerfile  # Create Dockerfile
```

For instance, we want to include the Node version:

```text
# Include the docker image, for instance, install nodejs with specific version of image
FROM node:<version>

# Execute command
CMD ["/bin/bash"]
```

Run the command and build the docker container:

```text
$ docker build -t <tag-name> <dockerfile-dir>
```

Run the docker container:

```text
$ docker run -it <tag-name>
```

> Hint: What is `bin/bash`?
>
> Check out "[What are the contents of bin/bash and what do I do if I accidentally overwrote](https://unix.stackexchange.com/questions/398543/what-are-the-contents-of-bin-bash-and-what-do-i-do-if-i-accidentally-overwrote)"

## Docker Commands

* `docker build` : Building the container, with `-t` to give it a tag
* `docker run`: Run the docker container
  * `-it`: to run it interactive
  * `-d`: run it at the background, returns the hash of the container
  * `-p`: since docker container is different from localhost, therefore we need to expose port via port forwarding; for instance: `-p 3000:3000` means to expose docker container's port 3000 to `localhost:3000`
* `docker ps`: Browse the current running docker containers
* `docker exec`: Going into a specific container and execute a command, for instance: `docker exec -it <container-hash> bash` which enters the container's bash
* `docker stop <container-hash>`: Stop a docker container

## More on Docker File

```text
# Include the docker image
FROM node:<version>

# Enter to specific work directory in docker container
WORKDIR /usr/src/<dir-name>

# Copy the current directory files into docker work directory
COPY ./ ./

# Run the command
RUN npm install

# Execute command
CMD ["/bin/bash"]
```

> Hint: `RUN` v.s. `CMD` 
>
> `RUN` command will commit changes into the docker container while `CMD` command will execute the command in the terminal.
>
> Usually, `CMD` will only appear only once and placed in the end of the docker file.

See: [https://docs.docker.com/engine/reference/builder/\#usage](https://docs.docker.com/engine/reference/builder/#usage)

## Docker Compose

A tool to orchestrate multiple docker containers at once. You'll need to create `docker-compose.yml` file to set it up as configuration:

```yaml
# Specify the version of the docker compose
version: "<version>"

# Container as a service
services:
  <service-1>:
    container_name: <name-of-the-service-1>

    # Either build directly from image
    image: <image>
    # or build from custom docker file
    build: <docker-file-directory>

    command: npm start
    working_dir: <working-directory>
    
    # Environment variables
    environment:
      POSTGRES_USER: maxwell
      POSTGRES_DB: postgres
      # ...
    
    # Port forwarding
    ports:
      - "3000:3000"
      
    # Project files mapping to the working directory
    volumes:
      - ./:<working-directory>
      
  <service-2>:
    container_name: <name-of-the-service-2>
    # ...
```

You can run the following command to build the docker containers:

```text
docker-compose build
```

To build up all of the services and also start up the docker containers:

```text
docker-compose up --build
```

To launch the docker container in the background:

```text
docker-compose up -d
```

To ensure all services are down:

```text
docker-compose down
```

Execute command \(e.g. entering the bash\), but be sure that you already launched the docker container \(use `docker-compose up -d`\):

```text
docker-compose exec <name-of-the-service> bash
```


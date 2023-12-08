

# Docker

## Introduction to Docker

Docker is a platform for developing, shipping, and running applications in containers. Containers allow a developer to package an application and its dependencies together, ensuring consistency across different environments.

### Key Concepts

1. **Image:**
   - A lightweight, stand-alone, executable package that includes everything needed to run a piece of software, including the code, runtime, libraries, and system tools.

2. **Container:**
   - An instance of a Docker image that runs a software application. It encapsulates the application and its dependencies, ensuring consistency in any environment.

3. **Dockerfile:**
   - A text file that contains instructions to build a Docker image. It specifies a base image and the steps to add layers, configure settings, and install software.

4. **Registry:**
   - A centralized repository for Docker images. Docker Hub is a public registry, and private registries are also common for storing proprietary images.

## Docker Installation

### Docker Desktop (Windows/Mac)

1. Download and install Docker Desktop from [Docker Hub](https://hub.docker.com/).

### Docker Engine (Linux)

1. Follow the distribution-specific instructions on the [official Docker website](https://docs.docker.com/install/).

## Basic Docker Commands

### Image Commands

1. **Pull an Image:**
   ```bash
   docker pull image_name:tag
   ```

2. **List Images:**
   ```bash
   docker images
   ```

3. **Remove Image:**
   ```bash
   docker rmi image_id
   ```

### Container Commands

1. **Run a Container:**
   ```bash
   docker run -p host_port:container_port image_name
   ```

2. **List Running Containers:**
   ```bash
   docker ps
   ```

3. **Stop a Container:**
   ```bash
   docker stop container_id
   ```

4. **Remove a Container:**
   ```bash
   docker rm container_id
   ```

### Dockerfile Basics

1. **Create a Dockerfile:**
   ```dockerfile
   # Use an official base image
   FROM base_image

   # Set the working directory
   WORKDIR /app

   # Copy application code
   COPY . .

   # Install dependencies
   RUN command

   # Expose a port
   EXPOSE container_port

   # Define the command to run the application
   CMD ["executable"]
   ```

2. **Build Image from Dockerfile:**
   ```bash
   docker build -t image_name:tag .
   ```

### Networking

1. **List Networks:**
   ```bash
   docker network ls
   ```

2. **Create a Network:**
   ```bash
   docker network create network_name
   ```

### Volumes

1. **List Volumes:**
   ```bash
   docker volume ls
   ```

2. **Create a Volume:**
   ```bash
   docker volume create volume_name
   ```

## Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications.

### Docker Compose Commands

1. **Compose File:**
   - Create a `docker-compose.yml` file to define services, networks, and volumes.

2. **Run Services:**
   ```bash
   docker-compose up
   ```

3. **Scale Services:**
   ```bash
   docker-compose up --scale service_name=num_instances
   ```

4. **Stop Services:**
   ```bash
   docker-compose down
   ```

## Docker Swarm

Docker Swarm is a native clustering and orchestration solution for Docker.

### Docker Swarm Commands

1. **Initialize Swarm:**
   ```bash
   docker swarm init
   ```

2. **Join Swarm as Worker:**
   ```bash
   docker swarm join --token token manager_ip:port
   ```

3. **Join Swarm as Manager:**
   ```bash
   docker swarm join-token manager
   ```

4. **Deploy Stack:**
   ```bash
   docker stack deploy -c docker-compose.yml stack_name
   ```

5. **List Stacks:**
   ```bash
   docker stack ls
   ```

## Conclusion

This markdown file provides a comprehensive overview of Docker, covering installation, basic commands, Dockerfile basics, port mapping, networking, volumes, Docker Compose, and Docker Swarm. Feel free to explore each section further based on your needs.
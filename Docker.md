# Jenkins:

## >Deployment Process:

## Application Architecture

1) Frontend : Angular / React, Vue

2) Backend : Java / .NET/ Python

3) Database : MySQL, SQL Server, MangoDB


## Application Tech Stack

-Frontend : React Js

-Backend : Java 17v

-Database : MySQL 8.5v

## Environment setup to Run our Application :   >> DevOps team is responsible to do this

1. Take one machine (physical/ virtual)

2. Install Angular 13v

3. Install Java 17v

4. Install Tomcat Server 9.0v

5. Install MySQL DB server 8.5v

## Application Environments :

### DEV : Developers will use it for integration testing

### SIT : Testing team will use it for system integration testing

### UAT : Client will use it for acceptance testing
 
### PILOT : Pre Production Environment

### PROD : Live Environment (end users can access our application running in prod)

## Challenges in Deployment Process :

1. Environment Setup

2. Setting up required dependencies (Softwares)

3. Version Conflicts

4. Environment Maintenance

5. Enviroment Issues


==> Challenge : version conflict may occur in above environments and application my not be working. 
==> Environment setup is time taking process and Error Prone

-------------------------------------------------------------------------------------------------------------------------

# Docker

- Free and open source software.
- It is used to containerization.
- Containerization -> Means package our [ application code + required dependencies =Docker Image ] as a single unit for execution.
- If we use Docker in our project then we can run our project in any system without bothring about underlying softwares.

## Docker Architecture:
### DockerFile : 
-A DockerFile is a script used to create Docker Container Image. It Contains instructions that Docker uses to build the image layer by layer.
### Docker Image : 
-It is a package which contains code + Dependencies.
 - MORE ::A Docker image is a lightweight, standalone, and executable package that includes everything needed to run  
                         a piece of software, including the code, runtime, libraries, and system tools.
### Docker Registry (DockerHub) : 
-It is a place where we can store docker images.
   -MORE :: Docker Hub is a cloud-based registry service provided by Docker for sharing and managing Docker Images.

### Docker Container : 
-When we run docker Image then docker container will be created. Our application will execute inside the  docker container.
     -MORE :: A Docker container is a lightweight, standalone, and executable software package that includes 
              everything needed to run a piece of software, including the code, runtime, libraries, and settings.

<> With one image we can create n no of containers.
<> Containers means Virtual Box
<> Containers created based on virtualization.
<> Every Docker container is a virtual machine.

### <> Virtualization : Running one OS on another OS.

## Docker Setup:
```
sudo install docker
sudo usermod -aG docker ec2-user
docker -v 
```

## Docker Commands:

```docker images : to diaplay list of images available in our system```

```docker ps : to display liost of containers runnning in our system```

```docker pull <image-id / image-name> : to download docker image```

```docker run <image-id / image-name> : to run docker image(container creation)```

```docker rmi <image-id / image-name> : to delete docker image```

```docker rm <container-id> : to delete docker container```

```docker system prune -a : delete stopped container and unused images```

```docker run -p 9090:9090 <image-id / image-name> : running and port mapping to run the app on host machine```

```docker run -d -p 9090:9090 <image-id / image-name> : port mapping to run the app on host machine in detached mode```

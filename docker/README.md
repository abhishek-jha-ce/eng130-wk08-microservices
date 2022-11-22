# Docker

Docker is an platform for developing, shipping, and running applications. 

- Docker enables you to separate your applications from your infrastructure so you can deliver software quickly.
- We can manage your infrastructure in the same ways you manage your applications.
- We can significantly reduce the delay between writing code and running it in production.

![image](https://user-images.githubusercontent.com/110366380/203262210-4c8ed2e3-ce65-42c1-adbc-40f279964119.png)

# Containerisation with Docker

Containerisation is defined as a form of operating system virtualization, through which applications are run in isolated user spaces called containers, all using the same shared operating system (OS).

Benefits of Containerisation:

- **Speed**: Containers are lightweight, they share the machine’s operating system (OS) kernel and are not bogged down with this extra overhead.
- **Portability**: A container creates an executable package of software that is abstracted away from the host operating system. It is portable and able to run uniformly and consistently across any platform or cloud.
- **Fault Isolation**: Each containerized application is isolated and operates independently of others. The failure of one container does not affect the continued operation of any other containers.
- **Ease of Management**: Container orchestration platforms can ease management tasks such as scaling containerized apps, rolling out new versions of apps, and providing monitoring, logging and debugging.

## Docker vs Container

Docker containers and virtual machines are both ways of deploying applications inside environments that are isolated from the underlying hardware. The chief difference is the level of isolation.
- Docker is lightweight and user-friendly
- Docker shares the resources of OS as opposed to using the OS completely
- Docker engine connects the container with the OS and only uses the resources required
- VM works with Hypervisor to connect guest OS/VM with Host OS

![image](https://user-images.githubusercontent.com/110366380/203069679-800c577d-4e6c-456d-9a2c-94b111302bb4.png)

## Docker Architecture

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/203069196-75d3fc7a-a013-43f8-af7e-9b8cf8c126e2.png">
</p>

## Common Docker Commands

#### Docker Basics Commands
```
docker --version              # Gets the current Version of docker
docker                        # Cheat Sheet for docker, displays all available versions 
docker login                  # If the need for login arises
alias docker="winpty docker"  # If we get errors like - cannot perform interactive login from a non tty device.
```

#### Download & Run Containers
```
docker pull hello-world     # Downloads the hello-world container
docker images               # Displays the images we have
docker run hello-world      # Runs the image we downloaded before, if not present downloads it as well
```

#### Checking the processes
```
docker ps     # Displays current running processes
docker ps -a  # Displays all the available processes.
```

#### Port mapping in our containers with localhost
```
docker run -d -p localhost-port:container-port # d - detached mode runs in background

Examples:
docker run -p 2368:2368 ghost # Pull and run ghost image in one go and select the correct port
```

#### Running containers from Docker Hub
````
docker run -d -p 4000:4000 docs/docker.github.io # Making docker docs available on our localhost

Running the nginx server

docker run -p 80:80 nginx     # Download & Run nginx server
docker run -d -p 80:80 nginx  # nginx in detached mode
````

#### View Logs
```
docker logs [container-id]
```

#### Container Basic Commands
```
docker stop [container-id]   # Stops the process running with all the
docker start [container-id]  # Starts the process where it left off
docker rm [container-id] -f  # Force delete container that is running
```

#### Logging into a running container
```
docker exec -it [container-id] bash
```

#### To copy files 
```
docker cp <file to copy> <container_id>:path/to/file

Example: Replacing nginx default page

```
#### Commit and Push to Docker Hub
```
```

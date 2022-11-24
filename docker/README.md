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

## Installing Docker

#### Download & Install

- Download for windows: https://www.docker.com/products/docker-desktop/
- Open the `.exe` to run the installer.
- Restart machine.

#### Create Account
- Sign up for docker at https://hub.docker.com/
- Open the Docker desktop application & Sign in.

#### Download WSL2
- We Might need to install WS2 separately: https://learn.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package
- If getting errors, kill the old Docker process in Task Manager and run it again.

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
docker cp /c/Users/abhis/OneDrive/Desktop/abhishek.html c53ec895e261:/usr/share/nginx/html/index.html
```

#### Task - To change the index.html file for `nginx` image and push it to your Docker Host.
- Tag the current container
```
docker tag <image name>:[version] <docker hub username>/eng130_abhishek
```
- Stop the container
- Run the new version of the container
```
docker run -d -p 80:80 abhishekjha21/eng130_abhishek
```
- Commit the container

```
docker commit [container Name/ID] abhishekjha21/eng130_abhishek:latest
```

- Push it
```
docker push abhishekjha21/eng130_abhishek:latest
```

## Docker Commands Cheat-Sheet

```
Options:
      --config string      Location of client config files (default
                           "C:\\Users\\abhis\\.docker")
  -c, --context string     Name of the context to use to connect to the
                           daemon (overrides DOCKER_HOST env var and
                           default context set with "docker context use")
  -D, --debug              Enable debug mode
  -H, --host list          Daemon socket(s) to connect to
  -l, --log-level string   Set the logging level
                           ("debug"|"info"|"warn"|"error"|"fatal")
                           (default "info")
      --tls                Use TLS; implied by --tlsverify
      --tlscacert string   Trust certs signed only by this CA (default
                           "C:\\Users\\abhis\\.docker\\ca.pem")
      --tlscert string     Path to TLS certificate file (default
                           "C:\\Users\\abhis\\.docker\\cert.pem")
      --tlskey string      Path to TLS key file (default
                           "C:\\Users\\abhis\\.docker\\key.pem")
      --tlsverify          Use TLS and verify the remote
  -v, --version            Print version information and quit

Management Commands:
  builder     Manage builds
  buildx*     Docker Buildx (Docker Inc., v0.9.1)
  compose*    Docker Compose (Docker Inc., v2.12.2)
  config      Manage Docker configs
  container   Manage containers
  context     Manage contexts
  dev*        Docker Dev Environments (Docker Inc., v0.0.3)
  extension*  Manages Docker extensions (Docker Inc., v0.2.13)
  image       Manage images
  manifest    Manage Docker image manifests and manifest lists
  network     Manage networks
  node        Manage Swarm nodes
  plugin      Manage plugins
  sbom*       View the packaged-based Software Bill Of Materials (SBOM) for an image (Anchore Inc., 0.6.0)
  scan*       Docker Scan (Docker Inc., v0.21.0)
  secret      Manage Docker secrets
  service     Manage services
  stack       Manage Docker stacks
  swarm       Manage Swarm
  system      Manage Docker
  trust       Manage trust on Docker images
  volume      Manage volumes

Commands:
  attach      Attach local standard input, output, and error streams to a running container
  build       Build an image from a Dockerfile
  commit      Create a new image from a container's changes
  cp          Copy files/folders between a container and the local filesystem
  create      Create a new container
  diff        Inspect changes to files or directories on a container's filesystem
  events      Get real time events from the server
  exec        Run a command in a running container
  export      Export a container's filesystem as a tar archive
  history     Show the history of an image
  images      List images
  import      Import the contents from a tarball to create a filesystem image
  info        Display system-wide information
  inspect     Return low-level information on Docker objects
  kill        Kill one or more running containers
  load        Load an image from a tar archive or STDIN
  login       Log in to a Docker registry
  logout      Log out from a Docker registry
  logs        Fetch the logs of a container
  pause       Pause all processes within one or more containers
  port        List port mappings or a specific mapping for the container
  ps          List containers
  pull        Pull an image or a repository from a registry
  push        Push an image or a repository to a registry
  rename      Rename a container
  restart     Restart one or more containers
  rm          Remove one or more containers
  rmi         Remove one or more images
  run         Run a command in a new container
  save        Save one or more images to a tar archive (streamed to STDOUT by default)
  search      Search the Docker Hub for images
  start       Start one or more stopped containers
  stats       Display a live stream of container(s) resource usage statistics
  stop        Stop one or more running containers
  tag         Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE
  top         Display the running processes of a container
  unpause     Unpause all processes within one or more containers
  update      Update configuration of one or more containers
  version     Show the Docker version information
  wait        Block until one or more containers stop, then print their exit codes

Run 'docker COMMAND --help' for more information on a command.
```

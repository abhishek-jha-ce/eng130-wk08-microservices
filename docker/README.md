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


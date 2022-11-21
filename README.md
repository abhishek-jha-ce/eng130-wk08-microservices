# Micro-sevices architecture

The microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms.


![image](https://user-images.githubusercontent.com/110366380/203054975-8ca73eee-b688-4d06-9d9a-6e7de35d212f.png)

### Advantage of Micro-service architecture
- Very very small application that focusing on a single thing
- Independent application
- Individual team can work on it
- Easy to scalable

### Micorseverces Architecture vs Monolithlic Architecture
A monolithic application is built as a single and indivisible unit. Usually, such a solution comprises a client-side user interface, a server side-application, and a database.

A Microservices architecture breaks it down into a collection of smaller independent units. These units carry out every application process as a separate service. So all the services have their own logic and the database as well as perform the specific functions.

![2](https://user-images.githubusercontent.com/110366380/203068685-324a1087-5ca7-4525-920d-743eb005e01d.png)

# Docker

Docker is an open platform for developing, shipping, and running applications. Docker enables you to separate your applications from your infrastructure so you can deliver software quickly. With Docker, you can manage your infrastructure in the same ways you manage your applications. By taking advantage of Docker’s methodologies for shipping, testing, and deploying code quickly, you can significantly reduce the delay between writing code and running it in production.

![image](https://user-images.githubusercontent.com/110366380/203069196-75d3fc7a-a013-43f8-af7e-9b8cf8c126e2.png)

## Docker vs Container

Docker containers and virtual machines are both ways of deploying applications inside environments that are isolated from the underlying hardware. The chief difference is the level of isolation.

- Container: With a container runtime like Docker, the application is sandboxed inside of the isolation features that a container provides, but still shares the same kernel as other containers on the same host. As a result, processes running inside containers are visible from the host system (given enough privileges for listing all processes). For example, if you start a MongoDB container with Docker, then run ps -e | grep mongo in a regular shell on the host (not in Docker), the process will be visible. Having multiple containers share the same kernel allows the end user to bin-pack lots and lots of containers on the same machine with near-instant start time. Also, as a consequence of containers not needing to embed a full OS, they are very lightweight, commonly around 5-100 MB.

- Virtual machine: In VM everything running inside the VM is independent of the host operating system, or hypervisor. The virtual machine platform starts a process (called virtual machine monitor, or VMM) in order to manage the virtualization process for a specific VM, and the host system allocates some of its hardware resources to the VM. However, what’s fundamentally different with a virtual machine is that at start time, it boots a new, dedicated kernel for this VM environment, and starts a (often rather large) set of operating system processes. This makes the size of the VM much larger than a typical container that only contains the application.

![image](https://user-images.githubusercontent.com/110366380/203069679-800c577d-4e6c-456d-9a2c-94b111302bb4.png)


## Advantage of Docker

A single docker image can be applied to multiple 

![3](https://user-images.githubusercontent.com/110366380/203070564-7da8cc98-65f2-49eb-adff-626ca9f510aa.png)


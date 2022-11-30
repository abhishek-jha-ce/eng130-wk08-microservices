## KUBERNETES

Kubernetes, also known as K8s, is an open-source orchestration system for automating deployment, scaling, and management of containerized applications. 

<img align="right" height="100" width="300" src="https://user-images.githubusercontent.com/110366380/204751702-f27c65ac-7f7a-4fc2-87d6-eb0926a2ec66.png">

- Developed by **google**.
- It facilitates both declarative configuration and automation.
- Large rapidly growing ecosystem.
- It is also known as `K8s` or `K8`.

### Benefits of Kubernetes

- Automates Containerized Environments
- Easy to Scale Up and Down
- Can be Run Anywhere
- Multi Cloud

### Installation

We can install kubernets from docker desktop settings.

### Kubernetes Pods

A Kubernetes pod is a collection of one or more Linux® containers, and is the smallest unit of a Kubernetes application. 

- A pod containes a single container.
- A pod can also be composed of multiple, tightly coupled containers for advanced use case.
- containers in the same pod will share the same compute resources.

### Kubernetes Service

Kubernetes Service is an abstract way to expose an application running on a set of Pods as a network service. It is a REST object in the API that we define in a manifest file and post to the API server.

- It is a very crucial component in Kubernetes as it lets us expose an application running in Pods to be reachable from outside your cluster.

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/204752934-670653cb-4c40-4150-a9b8-fc9d9b50c13d.png">
</p>

Further Reading: [Kubernetes Service](https://blog.learncodeonline.in/kubernetes-core-concepts-services)

## Common Commands

### Display the Service
```
kubectl get service
NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   25h

kubectl get svc  # short form for service - same result
NAME         TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)   AGE
kubernetes   ClusterIP   10.96.0.1    <none>        443/TCP   25h
```

### Delete a Service
```
$ kubectl delete svc nginx-svc
service "nginx-svc" deleted
```

### Display Deployment
```
$ kubectl get deployment # Currently we get- no resource found in default namespace - as nothing is deployed yet
No resources found in default namespace.

$ kubectl get deploy # same as above
No resources found in default namespace.
```

### Delete Deployments
```
$ kubectl delete deploy nginx-deployment
deployment.apps "nginx-deployment" deleted
```

### Display Pods
```
$ kubectl get pods # Shows the pods # We don't have any yet
No resources found in default namespace.
```

## Kubernetes Cheet Sheet

```
Basic Commands (Beginner):
  create          Create a resource from a file or from stdin
  expose          Take a replication controller, service, deployment or pod and expose it as a new Kubernetes service
  run             Run a particular image on the cluster
  set             Set specific features on objects

Basic Commands (Intermediate):
  explain         Get documentation for a resource
  get             Display one or many resources
  edit            Edit a resource on the server
  delete          Delete resources by file names, stdin, resources and names, or by resources and label selector

Deploy Commands:
  rollout         Manage the rollout of a resource
  scale           Set a new size for a deployment, replica set, or replication controller
  autoscale       Auto-scale a deployment, replica set, stateful set, or replication controller

Cluster Management Commands:
  certificate     Modify certificate resources.
  cluster-info    Display cluster information
  top             Display resource (CPU/memory) usage
  cordon          Mark node as unschedulable
  uncordon        Mark node as schedulable
  drain           Drain node in preparation for maintenance
  taint           Update the taints on one or more nodes

Troubleshooting and Debugging Commands:
  describe        Show details of a specific resource or group of resources
  logs            Print the logs for a container in a pod
  attach          Attach to a running container
  exec            Execute a command in a container
  port-forward    Forward one or more local ports to a pod
  proxy           Run a proxy to the Kubernetes API server
  cp              Copy files and directories to and from containers
  auth            Inspect authorization
  debug           Create debugging sessions for troubleshooting workloads and nodes

Advanced Commands:
  diff            Diff the live version against a would-be applied version
  apply           Apply a configuration to a resource by file name or stdin
  patch           Update fields of a resource
  replace         Replace a resource by file name or stdin
  wait            Experimental: Wait for a specific condition on one or many resources
  kustomize       Build a kustomization target from a directory or URL.

Settings Commands:
  label           Update the labels on a resource
  annotate        Update the annotations on a resource
  completion      Output shell completion code for the specified shell (bash, zsh, fish, or powershell)

Other Commands:
  alpha           Commands for features in alpha
  api-resources   Print the supported API resources on the server
  api-versions    Print the supported API versions on the server, in the form of "group/version"
  config          Modify kubeconfig files
  plugin          Provides utilities for interacting with plugins
  version         Print the client and server version information

Usage:
  kubectl [flags] [options]

Use "kubectl <command> --help" for more information about a given command.
```

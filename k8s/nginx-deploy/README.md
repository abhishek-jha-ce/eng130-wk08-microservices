## Deploying nginx using K8s

**Step 1**: Create a `nginx-deployment.yml` file for the deployment of nginx
```
# use spaces not a tab
apiVersion: apps/v1 # which api to use for deployment
kind: Deployment # what kind of service/object you want to create

# what would you like to call it - name the service/object
metadata:
  name: nginx-deployment # naming the deployment - Good idea to name it same as the filename

# create a kubernetes nginx-service.yml to create a k8 service
spec:
  selector:
    matchLabels:
      app: nginx # look for this label to match with k8 service

  # Let's create a replica set of this with instances/pods
  replicas: 3

  # Template to use it's label for k8 service to launch in the browser
  template:
    metadata:
      labels:
        app: nginx # This label connects to the service or any other k8s components

  # Let's define the container spec
    spec:
      containers:
      - name: nginx
        image: abhishekjha21/eng130_abhishek
        ports:
        - containerPort: 80
```
**Step 2**: Create a `nginx-service.yml` file to create K8 Service
```
---
# Select the type of API version and type of service/object
apiVersion: v1
kind: Service

# Metadata for name
metadata:
  name: nginx-svc
  namespace: default # sre

#Specification to include ports Selector to connect to the deployment
spec:
  ports:
  - nodePort: 30001 # range is 30000-32768
    port: 80

    targetPort: 80

# Let's define the selector and label to connect to nginx depoyment
  selector:
    app: nginx # this label connects this service to deployment

# Creating NodePort type of deployment
  type: NodePort # also use LoadBalancer - for local use cluster IP
```
**Step 3**: Run the deploy file `nginx-deployment.yml`
```
$ kubectl create -f nginx-deployment.yml
deployment.apps/nginx-deployment created

# Check it's successfully deployed.
$ kubectl get deployment
NAME               READY   UP-TO-DATE   AVAILABLE   AGE
nginx-deployment   3/3     3            3           55s

# Check if the pods are running
$ kubectl get pods
NAME                                READY   STATUS    RESTARTS   AGE
nginx-deployment-69576b8788-q6ljp   1/1     Running   0          91s
nginx-deployment-69576b8788-r8dwh   1/1     Running   0          91s
nginx-deployment-69576b8788-xvl4p   1/1     Running   0          91s
```
**Step 4**: Run the service file `nginx-service.yml`
```
$ kubectl create -f nginx-service.yml
service/nginx-svc created

# Check if the service is running
$ kubectl get service
NAME         TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
kubernetes   ClusterIP   10.96.0.1        <none>        443/TCP        25h
nginx-svc    NodePort    10.110.174.111   <none>        80:30001/TCP   43s
```

**Step 5**: Now if we type `http://localhost:30001/` in the browser, we can see our image being displayed.

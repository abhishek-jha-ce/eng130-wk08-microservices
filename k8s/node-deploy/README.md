## Deploying node using K8s

**Step 1**: Create a `node-deployment.yml` file for the deployment of our node app
```
# use spaces not a tab
apiVersion: apps/v1 # which api to use for deployment
kind: Deployment # what kind of service/object you want to create

# what would you like to call it - name the service/object
metadata:
  name: node-deployment # naming the deployment - Good idea to name it same as the filename

# create a kubernetes nginx-service.yml to create a k8 service
spec:
  selector:
    matchLabels:
      app: node-app # look for this label to match with k8 service

  # Let's create a replica set of this with instances/pods
  replicas: 3

  # Template to use it's label for k8 service to launch in the browser
  template:
    metadata:
      labels:
        app: node-app # This label connects to the service or any other k8s components

  # Let's define the container spec
    spec:
      containers:
      - name: node-app
        image: abhishekjha21/node-app
        ports:
        - containerPort: 3000
```
**Step 2**: Create a `node-service.yml` file to create K8 Service
```
---
# Select the type of API version and type of service/object
apiVersion: v1
kind: Service

# Metadata for name
metadata:
  name: node-svc
  namespace: default # sre

#Specification to include ports Selector to connect to the deployment
spec:
  ports:
    - port: 3000
      targetPort: 3000

# Let's define the selector and label to connect to nginx depoyment
  selector:
    app: node-app # this label connects this service to deployment

# Creating NodePort type of deployment
  type: LoadBalancer
```
**Step 3**: Run the deploy file `node-deployment.yml`
```
abhis@AJ-Desktop MINGW64 ~/sparta/eng130-wk08-microservices/k8s/node-deploy (main)
$ kubectl create -f node-deployment.yml
deployment.apps/node-deployment created

# Check it's successfully deployed.
$ kubectl get deployment
NAME              READY   UP-TO-DATE   AVAILABLE   AGE
node-deployment   3/3     3            3           39s

# Check if the pods are running
$ kubectl get pods
NAME                               READY   STATUS    RESTARTS   AGE
node-deployment-6876f8c6db-67zsx   1/1     Running   0          37s
node-deployment-6876f8c6db-82jm6   1/1     Running   0          37s
node-deployment-6876f8c6db-gx5cl   1/1     Running   0          37s
```
**Step 4**: Run the service file `node-service.yml`
```
$ kubectl create -f node-service.yml
service/node-svc created

# Check if the service is running
$ kubectl get service
NAME         TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
kubernetes   ClusterIP      10.96.0.1       <none>        443/TCP          25h
node-svc     LoadBalancer   10.109.137.33   localhost     3000:32277/TCP   54s
```

**Step 5**: Now if we type `http://localhost:3000/` in the browser, we can see our app. We can test it further by checking if **fibonacci** works.

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/204790976-f32fba53-2a84-40fb-8280-7afc0a5523c8.png">

</p>

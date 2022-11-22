## Dockerfile

- A Dockerfile is a text document that contains all the commands we could call on the command line to assemble an image.
- Docker can build images automatically by reading the instructions from a Dockerfile.
- The filename is `Dockerfile` without any extension. 

### To Create a Dockerfile

- Navigate to the location where you want to create `Dockerfile`.
- `nano Dockerfile`
- Sample Dockerfile - [Dockerfile](ngnx/Dockerfile)

### Build the image from dockerfile
```
docker build -t abhishekjha21/130-nginx .
# Don't forget the . at the end, it means the path of the Dockerfile is in the local directory.
```

### Run the image
```
docker run -d -p 80:80 abhishekjha21/130-nginx
```

##### Note: We don't need the `commit` command if we haven't made any changes to the image after it's build.

### Push the Image to the Docker Hub
```
docker push abhishekjha21/130-nginx
```

##### Note: If we don't specify any tags while building or afterwards, Docker automatically add the `latest` tag.

## Creating an Image for our `app`

**Step 1**: Create a new folder and create a new `Dockerfile` in that folder.

**Step 2**: Add the required files in that folder. We copy the `app` and `environment` folder in that folder.

**Step 3**: Add the following script to the `Dockerfile`.

```
  FROM nginx

  LABEL MAINTAINER=abhishek@sparta

  COPY app /home/
  COPY environment /home/

  EXPOSE 80
  EXPOSE 3000

  RUN apt-get update
  RUN apt-get install -y
  RUN apt-get install software-properties-common -y
  RUN apt-get install npm -y

  CMD ["nginx", "-g", "daemon off;"]
  WORKDIR /home/app
  RUN npm install
  CMD ["npm", "start"]
```
**Step 4**: Build the node app.
```
docker build -t node-app .
```
**Step 5**: Run the app locally. Check if its working as intended.
```
docker run -d -p 80:3000 node-app
```
**Step 6**: Push the changes
```
docker push abhishekjha21/node-app:v1
```
**Step 7**: Delete the existing image
```
docker rm [image-id] -f
```
**Step 8**: Download the image from Docker Hub & run it.
```
docker run -d -p 80:3000 abhishekjha21/node-app:v1
```
**Step 9**: Check if it's working properly in the browser by typing `localhost`. We should see:

![image](https://user-images.githubusercontent.com/110366380/203330491-23aae4e7-ea70-46af-af07-560045ff5aad.png)

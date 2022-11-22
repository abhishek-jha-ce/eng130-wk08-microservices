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


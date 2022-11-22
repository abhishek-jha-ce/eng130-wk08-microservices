# This code works perfectly fine, but the image size is very large.
# We create a new Dockerfile inside the app folder.

# FROM nginx

# LABEL MAINTAINER=abhishek@sparta

#  COPY app /home/
#  COPY environment /home/

#  EXPOSE 80
#  EXPOSE 3000

#  RUN apt-get update
#  RUN apt-get install -y
#  RUN apt-get install software-properties-common -y
#  RUN apt-get install npm -y

#  CMD ["nginx", "-g", "daemon off;"]
  
#  WORKDIR /home/app
  
#  RUN npm install
#  CMD ["npm", "start"]

FROM node as app

LABEL MAINTAINER=abhishekjha21/node-app

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install -g npm@7.20.6

# Copy everything from current location to default location 
COPY . .

EXPOSE 3000

CMD [ "node", "app.js" ]

# Let's build a built-stage production ready image

FROM node:alpine

COPY package*.json ./

RUN npm install -g npm@7.20.6

#This line does the magic to compress the image
COPY --from=app /usr/src/app /usr/src/app

EXPOSE 3000

CMD ["node", "app.js"]

# From which image
FROM nginx

# Person Creating This - For Reference
LABEL MAINTAINER=abhishek@sparta

# Copy the html file to the default location
COPY index.html /usr/share/nginx/html/

# Which port to expose
EXPOSE 80

# Launch the server
# -g stands for global
# daemon off directive tells Nginx to stay in the foreground
CMD ["nginx", "-g", "daemon off;"]

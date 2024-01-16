# Image Building with Docker Compose
Docker Compose can build your images at runtime. It checks the cache for images and, if necessary, builds the image using the provided build options when you use the `up` command. The image is not rebuilt every time; it's only built if it's not found in the cache.

To rebuild your images after changes, use either `docker compose build`  or `docker compose up --build`.


## This example scenario

we have a Docker Compose file with two services: an Nginx proxy and an Apache web server. The Nginx service uses a custom Docker image, specified in the Compose file with build arguments. The Dockerfile for this service is named nginx.Dockerfile, which is used to build a custom Nginx image including specific configurations.

The Docker Compose file is structured to mount HTML source files into the Apache server. This setup is ideal for a web developer who wants to emulate a production environment with an Nginx proxy, which acts as an intermediary for requests from clients, forwarding them to the Apache server.
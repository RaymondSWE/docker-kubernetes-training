# Custom Nginx Docker Image with basic html

This Dockerfile extends the official Nginx image from Docker Hub with custom content. Instead of seeing nginx at localhost, a html will be displayed.

## Features
- **Base Image**: `nginx:latest`. It's recommended to pin to a specific version for production.
- **Custom Content**: Adds a custom `index.html` to the Nginx web root.

## How It Works
1. **WORKDIR**: Sets the working directory to Nginx's web host root (`/usr/share/nginx/html`).
2. **COPY**: Copies `index.html` from the same directory as the Dockerfile to the container's web host root.

## Usage
1. Build the image: `docker build -t my-custom-nginx .`
2. Run a container: `docker run -p 80:80 my-custom-nginx`

Access your custom Nginx server at `http://localhost`.

## Notes
- No need to specify `EXPOSE` or `CMD`. These are inherited from the `nginx:latest` base image.

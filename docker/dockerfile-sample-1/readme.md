# Introduction to Dockerfiles


- **Dockerfile:** A Dockerfile is a text document containing a series of instructions for building a Docker image. It's not a shell script but a unique language specific to Docker. The purpose of this is to create custom docker images, you could always use docker pull for images but, this is more for specific tailored needs.

- **Structure:** Each instruction in a Dockerfile creates a layer in the Docker image. The order of instructions matters as Docker processes them top-down.

## Features
- **Base Image**: Debian bullseye-slim.
- **Nginx**: Pre-installed and configured.
- **Environment Variables**: Set for Nginx version and more.

## Usage
1. Build the image: `docker build -t my-nginx-image .`
2. Run a container: `docker run -p 80:80 my-nginx-image`

This will start Nginx inside a container. Access it via `http://localhost` on your browser.

You could also include tag, example `docker build -t my-nginx-image:1.0 .`, however Docker automatiically assign tag 'latest', which is their default and a good practice.

## Explaination of key words in dockerfile:

- **FROM:** Specifies the base image for the Docker image. It's the starting point and is required in every Dockerfile. Common base images include minimal distributions like Debian or Alpine.
- **ENV:** Sets environment variables in the image. These variables are important for configuring the container's behavior.
- **RUN:** Executes shell commands inside the container during the build process. Commonly used for installing software, unzipping files, or running scripts.
- **EXPOSE:** Indicates which ports the container should listen to. It's important for network services but doesn't automatically open ports on the host.
- **CMD:** Specifies the default command to run when the container starts. This is a required parameter and defines the container's primary purpose.


## Notes
- Ports: Exposes port 80 (HTTP)
- CMD: Starts Nginx when the container launches.

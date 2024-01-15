# Docker compose

Docker Compose is a tool that combines both a command line interface and a configuration file, aimed at simplifying the management of multi-container Docker applications. 

## Why use docker compose?
As you dive deeper into Docker, you'll discover that most applications are not standalone but involve multiple services. Docker Compose facilitates the management of such multi-container setups. It allows you to define and run multi-container Docker applications, connecting services like SQL databases, key-value stores, proxies, web frontends, backend workers, and more.


## Docker Compose: The Two Parts
1. YAML File: This is the configuration file for Docker Compose, written in YAML (Yet Another Markup Language). It's straightforward and hierarchical, outlining the various services, networks, volumes, environment variables, images, and other configurations needed for your application.

2. CLI Tool: The docker-compose command line interface is primarily used for local development and testing. It leverages the YAML file to streamline Docker commands, making it easier to start, stop, and manage your application components.

Understanding the Docker Compose File
1. Versions: Docker Compose files have evolved over time, with different versions adding new features. The version statement is the first line in the file, indicating which features are supported.

2. Services: These are essentially containers. Each service can have multiple instances for redundancy. The service section includes details like the image to use, commands to run, environment variables, and volumes.

# Docker Compose CLI
The Docker Compose CLI tool simplifies local development and testing, allowing you to manage your application's lifecycle with simple commands.
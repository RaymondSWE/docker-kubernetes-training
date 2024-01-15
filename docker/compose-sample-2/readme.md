# Docker Compose example usage overview

## Starting and Managing Containers

- `docker compose up`: Starts containers, creates a private network, and opens ports.
- Automatic bind mount handling and log output to the screen.
- `docker compose up -d`: Runs containers in detached mode (background).

## Web Server and Proxy example explaination
- Setup includes Apache server and Nginx reverse proxy.
- Demonstrates traffic routing through Nginx to Apache.
- Color-coded logs for easy differentiation between container outputs. such as web-1 and proxy-1

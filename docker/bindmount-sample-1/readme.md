# Lecture Summary: Bind Mounts and Jekyll with Docker

In this lecture, we explored using bind mounts in Docker, particularly for running a Jekyll website without installing Jekyll directly on our machine.

## Key Takeaways:

1. **Bind Mounts Usage**: Demonstrated how to use bind mounts to mount a directory (containing a Jekyll site) from the host into the Docker container.

2. **Avoiding Direct Installation**: Highlighted the advantage of using Docker to run Jekyll, avoiding the need to install Jekyll and its dependencies (like a specific version of Ruby) on the host machine.

3. **Running Jekyll inside Docker**: Showed how to use `docker run` (or `docker container run`) to start a Jekyll server inside a container. This included forwarding port 80 on the host to port 4000 in the container and mounting the host directory into the container.

4. **Live Updates**: Demonstrated that changes made to files on the host (like modifying a post title) are immediately reflected in the container. This was observed by the container detecting changes and updating the site, visible upon refreshing the browser.


5. **Jekyll for Static Sites**: Briefly touched on Jekyll being a useful tool for creating static sites, especially for hosting on platforms like GitHub, which offers free hosting.


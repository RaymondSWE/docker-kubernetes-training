# Docker Swarm secret practice 1
This README documents the process of using Docker Swarm secrets in the context of deploying a PostgreSQL database service. Docker Swarm secrets provide a secure way to store and manage sensitive data, such as passwords and configuration files, without exposing them in service configurations or API inspections.




## Understanding Docker Secrets

- Secret Storage: Secrets are stored in the Docker Swarm database and are encrypted during transit and at rest.
- Access Control: Only assigned services and their containers can access the decrypted secrets.
- Implementation: Secrets appear as files inside the containers, but they are securely stored in a tmpfs (temporary file system in RAM) and are not written to the container's file system.

## Commands in terminal ubuntu used:
1. `docker secret create psql_user psql_user.txt` = This command creates a new secret named psql_user from the file psql_user.txt.

2. `docker secret ls` = Lists all the secrets managed by Docker Swarm, providing an overview of what secrets are available.

3. `docker service create --name psql --secret psql_user --secret psql_pass -e POSTGRES_PASSWORD_FILE=/run/secrets/psql_pass -e POSTGRES_USER_FILE=/run/secrets/psql_user postgres:9.4` = Creates a PostgreSQL service named psql, assigning it the psql_user and psql_pass secrets. Environment variables point to the secret files for the PostgreSQL user and password.
4. `docker service ps psql` = Displays information about the running instances of the psql service, including which node it's running on.
5. `docker exec -it <container name> = Provides a bash shell inside the specified container, allowing for direct interaction and inspection.
6. `ls /run/secret` = Lists the secret files available in the /run/secrets directory inside the container.
7. `docker service update --secret-rm <secret_name> psql` = Removes a specified secret from the psql service. This operation will cause the service to redeploy its containers. This is not ideal, a more appropate will be shown in other samples

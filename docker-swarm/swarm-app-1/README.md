# Assignment: Create A Multi-Service Multi-Node Web App

## Goal: create networks, volumes, and services for a web-based "cats vs. dogs" voting app

Here is a basic diagram of how the 5 services will work:

![diagram](./architecture.png)

- All images are on Docker Hub, so you should use editor to craft your commands locally,
then paste them into swarm shell (at least that's how I'd do it)
- a `backend` and `frontend` overlay network are needed.
Nothing different about them other than that backend will help protect database from the voting web app.
(similar to how a VLAN setup might be in traditional architecture)
- The database server should use a named volume for preserving data.
Use the new `--mount` format to do this: `--mount type=volume,source=db-data,target=/var/lib/postgresql/data`

### Services (names below should be service names)

- vote
  - bretfisher/examplevotingapp_vote
  - web frontend for users to vote dog/cat
  - ideally published on TCP 80. Container listens on 80
  - on frontend network
  - 2+ replicas of this container

- redis
  - redis:3.2
  - key-value storage for incoming votes
  - no public ports
  - on frontend network
  - 1 replica NOTE VIDEO SAYS TWO BUT ONLY ONE NEEDED

- worker
  - bretfisher/examplevotingapp_worker
  - backend processor of redis and storing results in postgres
  - no public ports
  - on frontend and backend networks
  - 1 replica

- db
  - postgres:9.4
  - one named volume needed, pointing to /var/lib/postgresql/data
  - on backend network
  - 1 replica
  - remember set env for password-less connections -e POSTGRES_HOST_AUTH_METHOD=trust

- result
  - bretfisher/examplevotingapp_result
  - web app that shows results
  - runs on high port since just for admins (lets imagine)
  - so run on a high port of your choosing (I choose 5001), container listens on 80
  - on backend network
  - 1 replica

# Commands to run in linux and why to solve this:

1. `docker swarm init` = Initializes the current machine as a Docker Swarm manager node.
2. `docker network create --driver overlay frontend` and `docker network create --driver overlay backend` = we need network creationg, thus two overlay networks, frontend and backend. Overlay networks enable containers on different Docker hosts to communicate with each other, essential for distributed applications like this one.
3. `docker service create --name vote --network frontend -p 80:80 bretfisher/examplevotingapp_vote` = This is part of the service deployment
4. `docker service create --name redis --network frontend redis:3.2`
5. `docker service create --name worker --network frontend --network backend bretfisher/examplevotingapp_worker` = Compared to the previous service, the worker should be inside of both network thus two --network was assigned (look at architecture.png for reference)
6. `docker service create --name db --network backend --mount type=volume,source=db-data,target=/var/lib/postgresql/data postgres:9.4`
7. `docker service create --name result --network backend -p 5001:80 bretfisher/examplevotingapp_result`
8. `docker service ls` = run docker service ls after each creation of service, for verification






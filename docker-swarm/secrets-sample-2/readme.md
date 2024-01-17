# Docker secret sample 2

Same as secret-sample-1 folder but all defined inside of yaml file. Read the readme for secret-sample-1 for better understanding

## The only commanded needed is: 
1. `docker stack deploy -c docker-compose.yml mydb` = Deploys a stack defined in docker-compose.yml, which can include service definitions that reference the created secrets. Replace mydb with your desired stack name.

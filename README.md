# Docker Swarm With Dynamic Reverse Proxy

Adapted from https://docs.docker.com/engine/swarm/stack-deploy/

```
docker swarm init

# Create local registry
docker service create --name registry --publish published=5000,target=5000 registry:2

# Build services (app)
docker-compose build

# Push build images to registry
docker-compose push

# Test locally
docker-compose up -d
docker-compose rm -fv

# deploy
docker stack deploy --compose-file docker-compose.yml stack

# Test
curl localhost:80/app/hello
```

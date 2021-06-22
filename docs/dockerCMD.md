### Docker provides a rich set of actions that can be used to build, run, tag, and push images. 

A list of handy Docker commands used in practice:
```bash
docker build [OPTIONS] PATH #build image
docker run [OPTIONS] IMAGE [COMMAND] [ARG...] #run image
docker logs CONTAINER_ID #get logs
docker images #list images
docker ps #list containers
docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG] #tag image
docker login #login to DockerHub
docker push NAME[:TAG] #push image
docker pull NAME[:TAG] #pull image
```
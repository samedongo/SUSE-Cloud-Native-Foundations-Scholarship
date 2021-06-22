### Containerization 
Example with [python-helloworld](../python-helloworld)
```bash
# build an image using the Dockerfile from the current directory
docker build -t py-helloworld .

# test it locally and verify if it meets the expected behavior
# run the `python-helloworld` image, in detached mode and expose it on port `5111`
docker run -d -p 5111:5000 py-helloworld

# to retrieve the Docker container logs use the 
docker logs {{ CONTAINER_ID }}
```

##### Pushing an image to a Docker registry
```bash
# to tag the Python hello-world application
docker tag py-helloworld codinoz/py-helloworld:v1.0.0

# login to DockerHub
docker login 

# push to the repository in DockerHub
docker push codinoz/py-helloworld:v1.0.0
```
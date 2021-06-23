# Deploy Kubernetes

Pod architecture, showcasing a container running a Docker image.
![](https://video.udacity-data.com/topher/2020/December/5fe07d2d_screenshot-2020-12-21-at-10.47.02/screenshot-2020-12-21-at-10.47.02.png)

Application management using a Deployment and ReplicaSet.

![](https://video.udacity-data.com/topher/2020/December/5fe082fd_screenshot-2020-12-21-at-11.11.46/screenshot-2020-12-21-at-11.11.46.png)

To create a deployment:

```bash
# create a Deployment resource
# NAME - required; set the name of the deployment
# IMAGE - required; specify the Docker image to be executed
# FLAGS - optional; provide extra configuration parameters for the resource
# COMMAND and args - optional; instruct the container to run specific commands when it starts
kubectl create deploy NAME --image=image [FLAGS] -- [COMMAND] [args]

# Some of the widely used FLAGS are:
# -r, --replicas - set the number of replicas
# -n, --namespace - set the namespace to run
# --port - expose the container port
# For example, to create a Deployment for the Go hello-world application in namespace `test`, the following command
# can be used:
kubectl create deploy go-helloworld --image=codinoz/go-helloworld:v1.0.0 -n test
```
It is possible to create headless pods or pods that are not managed through a ReplicaSet and Deployment, these are useful when creating a testing pod.
```bash
# create a headless pod
# NAME - required; set the name of the pod
# IMAGE - required;  specify the Docker image to be executed
# FLAGS - optional; provide extra configuration parameters for the resource
# COMMAND and args - optional; instruct the container to run specific commands when it starts 
kubectl run NAME --image=image [FLAGS] -- [COMMAND] [args...]

# Some of the widely used FLAGS are:
# --restart - set the restart policy. Options [Always, OnFailure, Never]
# --dry-run - dry run the command. Options [none, client, server]
# -it - open an interactive shell to the container
# example: create a busybox pod, with an interactive shell and a restart policy set to Never 
kubectl run -it busybox-test --image=busybox --restart=Never
```

Details about current deploy:
```bash
 kubectl get deploy #deployments currently running
 kubectl get rs #same command with the replica sets
 kubectl get po #pods running currently within the current namespace
```

Verify that application is running inside the port:
```bash
# Using port-forwarding command to access the container from the local host
kubectl port-forward [podName] [portApplication]:[portHost] #from VM 
kubectl port-forward --address 0.0.0.0 [podName] [portApplication]:[portHost] #fromt host
```

Rolling update of an application, to update between different application versions.

![](https://video.udacity-data.com/topher/2020/December/5fe087be_screenshot-2020-12-21-at-11.32.05/screenshot-2020-12-21-at-11.32.05.png)

```bash
# Edit deploy
kubectl edit deploy [deploymentName] [-o ouputFormat]

# Update image version

# Verify new replicaSet
kubectl get rs

# Verify pod age is updated
kubectl get po
```
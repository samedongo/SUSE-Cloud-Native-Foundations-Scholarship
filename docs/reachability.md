## Application Reachability

#### Service to expose a deployment
```bash
# current service running
kubectl get svc

# expose a Deployment through a Service resource 
# NAME - required; set the name of the deployment to be exposed
# --port - required; specify the port that the service should serve on
# --target-port - optional; specify the port on the container that the service should direct traffic to
# FLAGS - optional; provide extra configuration parameters for the service
kubectl expose deploy NAME --port=port [--target-port=port] [FLAGS]

# Some of the widely used FLAGS are:
--protocol - set the network protocol. Options [TCP|UDP|SCTP]
--type - set the type of service. Options [ClusterIP, NodePort, LoadBalancer]

# expose the `go-helloworld` deployment on port 8111
# note: the application is serving requests on port 6112
kubectl expose deploy go-helloworld --port=6111 --target-port=6111
kubectl get svc

# to access from a workload to service using the service ip
kubectl run test-$RANDOM --namespace=default --rm -it --image=alpine -- sh
#
wget -qO- CLUSTER_IP:PORT

```

#### Resources to pass data to application
```bash
# Configmaps non-confidential data in key-value pairs
# create a Configmap
# NAME - required; set the name of the configmap resource
# FLAGS - optional; define  extra configuration parameters for the configmap
kubectl create configmap NAME [FLAGS]
# create a Configmap to store the color value
kubectl create configmap test-cm --from-literal=color=yellow
kubectl get cm
kubectl describe cm test-cm

# Some of the widely used FLAGS are:
--from-file - set path to file with key-value pairs
--from-literal - set key-value pair from command-line

# Secrets, store and distribute sensitive data to the pods
# create a Secret
# NAME - required; set the name of the secret resource
# FLAGS - optional; define  extra configuration parameters for the secret
kubectl create secret generic NAME [FLAGS]

# Some of the widely used FLAGS are:
--from-file - set path to file with the sensitive key-value pairs
--from-literal - set key-value pair from command-line
# create a Secret to store the secret color value
kubectl create secret generic test-secret --from-literal=color=blue
kubectl get secrets
kubectl describe secrets test-sec
kubectl get secrets test-sec -o yaml
# to see an encoded value 
echo "ENCODED_VALUE" | base64 -D
```

#### Namespace
```bash
# create a Namespace
# NAME - required; set the name of the Namespace
kubectl create ns NAME
# create a `test-demo` Namespace
kubectl create ns test-demo
# list all namespaces
kunectl get ns

# to get any researchers from a particular namespace
# pods in the default namespace
kubectl get po
# get all the pods in the `test-demo` Namespace
kubectl get po -n test-demo

# create a resource within particular namespace
kubectl create deploy [...] -n test-demo
```
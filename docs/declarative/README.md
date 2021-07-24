## Declarative Kubernetes YAML Manifests
```bash
# create YAML template for a resource 
kubectl create RESOURCE [REQUIRED FLAGS] --dry-run=client -o yaml

# create the base YAML templated for a namespace demon
kubectl create ns demon --dry-run=client -o yaml
kubectl create ns demon --dry-run=client -o yaml > namespaces.yaml
cat namespaces.yaml

# create the base YAML templated for a demo Deployment running a nxing application
 kubectl create deploy demo --image=nginx --dry-run=client -o yaml

# apply declarative config to create a resource 
# defined in the YAML manifests with the name manifest.yaml
kubectl apply -f manifest.yaml
# to create namespace demon
kubectl apply -f namespaces.yaml
kubectl get ns

# create and YAML template to deploy and apply
kubectl create deploy busybox --image=busybox -r=5 -n demon --dry-run=client -o yaml
kubectl create deploy busybox --image=busybox -r=5 -n demon --dry-run=client -o yaml > deploy.yaml
cat deploy.yaml
kubectl apply -f deploy.yml
kubectl get deploy -n demon
kubectl get po -n demon

# create all resources in directory
kubectl apply -f DIRECTORY_PATH/
# inspect all resources
kubectl get all -n demon

# delete a resource defined in the YAML manifests with the name manifest.yaml
kubectl delete -f manifest.yaml
```
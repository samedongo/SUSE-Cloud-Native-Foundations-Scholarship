## Bootstrapping Cluster Kubernetes with [k3s](https://k3s.io/)

### Prerequisites
- Install VirtualBox 6.1.16 or higher installed.
- Install the latest version of Vagrant.

### Up & Running VM
```bash
# Inspect available vagrant boxes
vagrant status

# create a vagrant box using the Vagrantfile in the current directory
vagrant up

# SSH into the vagrant box
# Note: this command uses the .vagrant folder to identify the details of the vagrant box
vagrant ssh
```

### Create cluster
```bash
# Install cluster
# Download any binary requires to run an operational cluster.
curl -sfL https://get.k3s.io | sh -

# The kubeconfig file is stored locally within 
# /etc/rancher/k3s/k3s.yaml path.

# Create a node
kubectl get no 

# Inspect the endpoints for the cluster and installed add-ons
kubectl cluster-info

# List all the nodes in the cluster.
# To get a more detailed view of the nodes, the `-o wide` flag can be passed
kubectl get nodes [-o wide]

# Describe a cluster node.
# Typical configuration: node IP, capacity (CPU and memory), a list of running pods on the node, podCIDR, etc.
kubectl describe node {{ NODE NAME }}
```
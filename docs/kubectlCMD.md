## Useful Kubectl Commands
```bash
# Create Resources
kubectl create RESOURCE NAME [FLAGS]

# Describe Resources
kubectl describe RESOURCE NAME 

#Get Resources
kubectl get RESOURCE NAME [-o yaml]

# Edit Resources
kubectl edit RESOURCE NAME [-o yaml]

# Label Resources
kubectl label RESOURCE NAME [PARAMS]

# Port-forward to Resources
# To access resources through port-forward
kubectl port-forward RESOURCE/NAME [PARAMS]

# Logs from Resources
kubectl logs RESOURCE/NAME [FLAGS]

# Delete Resources
kubectl delete RESOURCE NAME
```
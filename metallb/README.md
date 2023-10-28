# Metallb Deployment 

## 🚀 Quick Start
```sh
kubectl create -f generated-manifests.yaml
```
This will kick off the deployment using the manifest file that we've pre-generated for you.



## 🛠️ Building the Manifest
### If you're looking to customize and build your own manifest, you can do so using the following command:
```sh
../kustomize build --enable-helm . > generated-manifests.yaml
```
This utilizes the powerful kustomize tool to compile resources with Helm support.



## 🗑️ Cleanup 
### Done testing or need to refresh your environment? Use the following command to delete the resources:
```sh
kubectl delete -f generated-manifests.yaml
```

### Delete all completed or failed pods
```sh
kubectl get pods -n metallb-system --field-selector=status.phase=Succeeded -o jsonpath='{.items[*].metadata.name}' | xargs kubectl delete pod -n metallb-system
kubectl get pods -n metallb-system --field-selector=status.phase=Failed -o jsonpath='{.items[*].metadata.name}' | xargs kubectl delete pod -n metallb-system
```

#### Note
Metallb needs to restart once because of crd are not yet present but IpAddressPool is defined so it needs to reboot once
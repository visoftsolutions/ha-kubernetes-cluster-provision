# TIKV Deployment 

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
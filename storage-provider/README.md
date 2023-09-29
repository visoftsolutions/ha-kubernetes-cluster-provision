# Rancher storage provider Deployment 

## 🚀 Quick Start
```sh
cd ansible
vim ./inventory/sample/inventory.ini # check the configuration
ansible-playbook -i ./inventory/sample/inventory.ini --become main.yaml
cd ../
kubectl create -f generated-manifests.yaml
```
This will kick off the deployment using the manifest file that we've pre-generated for you.
Ansible has a playbook that formats disks and prepares them for storage provisioner. Data on disks will be erased!



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
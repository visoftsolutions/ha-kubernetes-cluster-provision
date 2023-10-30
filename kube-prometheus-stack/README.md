# Kube Prometheus Stack Deployment 

## 🚀 Quick Start
```sh
kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.68.0/example/prometheus-operator-crd/monitoring.coreos.com_alertmanagerconfigs.yaml
kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.68.0/example/prometheus-operator-crd/monitoring.coreos.com_alertmanagers.yaml
kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.68.0/example/prometheus-operator-crd/monitoring.coreos.com_podmonitors.yaml
kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.68.0/example/prometheus-operator-crd/monitoring.coreos.com_probes.yaml
kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.68.0/example/prometheus-operator-crd/monitoring.coreos.com_prometheusagents.yaml
kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.68.0/example/prometheus-operator-crd/monitoring.coreos.com_prometheuses.yaml
kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.68.0/example/prometheus-operator-crd/monitoring.coreos.com_prometheusrules.yaml
kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.68.0/example/prometheus-operator-crd/monitoring.coreos.com_scrapeconfigs.yaml
kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.68.0/example/prometheus-operator-crd/monitoring.coreos.com_servicemonitors.yaml
kubectl create -f https://raw.githubusercontent.com/prometheus-operator/prometheus-operator/v0.68.0/example/prometheus-operator-crd/monitoring.coreos.com_thanosrulers.yaml
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
kubectl get pods -n kube-prometheus-stack --field-selector=status.phase=Succeeded -o jsonpath='{.items[*].metadata.name}' | xargs kubectl delete pod -n kube-prometheus-stack
kubectl get pods -n kube-prometheus-stack --field-selector=status.phase=Failed -o jsonpath='{.items[*].metadata.name}' | xargs kubectl delete pod -n kube-prometheus-stack
```
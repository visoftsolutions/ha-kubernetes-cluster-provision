# ha-kubernetes-cluster-provision

```
./kustomize build --enable-helm metallb/ > metallb/generated-manifests.yaml
kubectl apply -f metallb/generated-manifests.yaml 
```

# Remember to purge
/var/lib/rook
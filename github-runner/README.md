# Cert-Manager Deployment 

## 🚀 Quick Start
```sh
NAMESPACE="arc-systems"
helm install arc \
    --namespace "${NAMESPACE}" \
    --create-namespace \
    oci://ghcr.io/actions/actions-runner-controller-charts/gha-runner-scale-set-controller
```

```sh
INSTALLATION_NAME="arc-runner-set"
NAMESPACE="arc-runners"
GITHUB_CONFIG_URL="https://github.com/visoftsolutions"
GITHUB_PAT=""
helm install "${INSTALLATION_NAME}" \
    --namespace "${NAMESPACE}" \
    --create-namespace \
    --set githubConfigUrl="${GITHUB_CONFIG_URL}" \
    --set githubConfigSecret.github_token="${GITHUB_PAT}" \
    --set "containerMode.type=kubernetes" \
    --set "containerMode.kubernetesModeWorkVolumeClaim.accessModes[0]=ReadWriteOnce" \
    --set "containerMode.kubernetesModeWorkVolumeClaim.storageClassName=local-storage" \
    --set "containerMode.kubernetesModeWorkVolumeClaim.resources.requests.cpu=500" \
    --set "containerMode.kubernetesModeWorkVolumeClaim.resources.requests.memory=500" \
    --set "containerMode.kubernetesModeWorkVolumeClaim.resources.requests.storage=5Gi" \
    --set "containerMode.kubernetesModeWorkVolumeClaim.resources.limits.cpu=5000" \
    --set "containerMode.kubernetesModeWorkVolumeClaim.resources.limits.memory=10Gi" \
    oci://ghcr.io/actions/actions-runner-controller-charts/gha-runner-scale-set
```
# Install helm

```powershell
kubectl create -f ./helm/rbac-config.yaml
helm init --service-account tiller --history-max 200
```

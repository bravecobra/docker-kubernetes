# Helm

## Install helm on the cluster

```bash
kubectl create -f ./src/helm/rbac-config.yaml
helm init --service-account tiller --history-max 200
```

To test the correct installation of tiller, verify that the pods has been deployed

```bash
kubectl get pods --namespace kube-system | grep tiller
```

Current version of helm is incompatible with kubernetes 1.16. Some api versions got deprecated. To work around that, update those

```bash
helm init --service-account tiller --override spec.selector.matchLabels.'name'='tiller',spec.selector.matchLabels.'app'='helm' --output yaml > ./src/helm/tiller.yaml
sed 's@apiVersion: extensions/v1beta1@apiVersion: apps/v1@'
kubectl apply -f ./src/helm/tiller.yaml
```

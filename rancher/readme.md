# Installing rancher

## Install nginx ingress proxy

```powershell
helm install stable/nginx-ingress --name ingress-nginx --namespace ingress-nginx --wait
```

## Install cert-manager

Install the CustomResourceDefinition resources separately

```powershell
kubectl apply -f https://raw.githubusercontent.com/jetstack/cert-manager/release-0.10/deploy/manifests/00-crds.yaml
```

Create the namespace for cert-manager

```powershell
kubectl create namespace cert-manager
```

Label the cert-manager namespace to disable resource validation

```powershell
kubectl label namespace cert-manager certmanager.k8s.io/disable-validation=true
```

Add the Jetstack Helm repository

```powershell
helm repo add jetstack https://charts.jetstack.io
```

Update your local Helm chart repository cache

```powershell
helm repo update
```

Install the cert-manager Helm chart

```powershell
helm install --name cert-manager --namespace cert-manager --version v0.10.1 jetstack/cert-manager
```

```powershell
kubectl get pods --namespace cert-manager
```

## Install rancher

```powershell
helm repo add rancher-latest https://releases.rancher.com/server-charts/latest
helm install rancher-latest/rancher --name rancher --namespace cattle-system --set hostname=rancher.localhost --wait
```

Setting hosts file
If you set the hostname to something other than rancher.localhost, you may need to update your hosts file to access it.

- Windows:  c:\windows\system32\drivers\etc\hosts
- Mac/Linux: - /etc/hosts

Edit the appropriate file for your system and add an entry

```content
127.0.0.1 myrancher.mydomain.com
```

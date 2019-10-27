# Install dashboard

## Install

From <https://github.com/kubernetes/dashboard>

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-beta4/aio/deploy/recommended.yaml
```

Look into <https://github.com/kubernetes/dashboard/blob/master/docs/user/access-control/creating-sample-user.md>

```bash
kubectl apply -f ./dashboard/service-account.yaml  #create an account
kubectl create -f ./dashboard/dashboard-admin.yaml #give the account cluster-admin access
```

## Using the dashboard

Run the following to get the token with `cluster-admin` access

```bash
kubectl -n kubernetes-dashboard get secret
```

Look for `admin-user-token-xxxxx` and get the token with

```bash
kubectl -n kubernetes-dashboard describe secret admin-user-token-xxxxx
```

or

```bash
kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')
```

Now proxy the dashboard

```bash
kubectl proxy
```

and use the token return from the previous command to login at [dashboard](  http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/ ).

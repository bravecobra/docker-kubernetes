# Install dashboard

From <https://github.com/kubernetes/dashboard>

    kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml

Look into <https://github.com/kubernetes/dashboard/wiki/Access-control>

    kubectl create -f ./dashboard/dashboard-admin.yaml

Run the following to get the token with `cluster-admin` access

    kubectl -n kube-system get secret

Look for `kubernetes-dashboard-token-xxxxx` and get the token with

    kubectl -n kube-system describe secret kubernetes-dashboard-token-xxxxx

Now proxy the dasboard

    kubectl proxy

<http://docs.shippable.com/deploy/tutorial/create-kubeconfig-for-self-hosted-kubernetes-cluster/>

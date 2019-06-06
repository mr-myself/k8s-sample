This is a sample product to work on k8s. (This would be frequently updated.)

# Development

I expect that you use skaffold for development which helps reloading yaml files when we update them.
So basically, what we need to do is to run the below command.

```
$ skaffold dev
```
## Preparation

To add `ingress-nginx`, you need to run the below commands.
```
$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.24.1/deploy/mandatory.yaml
$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/nginx-0.24.1/deploy/provider/cloud-generic.yaml
```


## Dashboard
If you would like to see the current status of k8s, the dashboard can help you.

```
$ kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml
$ kubectl get pod --namespace=kube-system -l k8s-app=kubernetes-dashboard # Check if it's running
$ kubectl apply -f service-account.yaml
$ kubectl -n kube-system get secret
$ kubectl -n kube-system describe secret admin-user-token-xxx # The last part xxx is randomly decided. You can grab it from the previous list.

$ kubectl proxy
```

Then access to the below link. Please choose the "Token" method and paste the one you got from above command.
http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/overview?namespace=default



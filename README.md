# consul_up_and_running
notes while doing the consul up and running book

When starting

minikube start
minikube tunnel

Make sure to use the correct kubectl
``
kubectl config use-context minikube
```

verify it works
```
kubectl get nodes

NAME       STATUS   ROLES                  AGE     VERSION
minikube   Ready    control-plane,master   6d21h   v1.23.3
```

Consul should be available now on the link http://localhost:8500


minikube stop


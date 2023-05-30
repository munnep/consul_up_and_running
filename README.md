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


Location for the official github repository
https://github.com/consul-up/examples/tree/main/chapter5



# grafana installation
kubectl create secret generic grafana-admin --from-literal=admin-user=admin --from-literal=admin-password=admin

install with helm
helm install grafana grafana --version 6.17.1 --repo https://grafana.github.io/helm-charts --set service.type=LoadBalancer --set service.port=3000 --set persistence.enabled=true --set rbac.pspEnabled=false --set admin.existingSecret=grafana-admin --wait


sum(
  rate(
    envoy_http_downstream_rq_completed{
      consul_source_service="$Service",
      envoy_http_conn_manager_prefix="public_listener"
    }[$__rate_interval]
  )
)

sum(
  rate(
    envoy_http_downstream_rq_completed{
      consul_source_service="$Service",
      envoy_http_conn_manager_prefix=~"public_listener|ingress_upstream_8080"
    }[$__rate_interval]
  )
)

sum( 
  rate(
        envoy_http_downstream_rq_completed{
          consul_source_service="$Service",
          envoy_http_conn_manager_prefix=~"public_listener|ingress_upstream_8080"
        }[$__rate_interval]
      )
)

helm install jaeger jaeger-operator --version 2.26.0 --repo https://jaegertracing.github.io/helm-charts --wait
> WIP

# Implement istio with grafana

## Install Helm
```shell
brew install helm
```

## Istio
```shell
helm repo add istio.io https://storage.googleapis.com/istio-release/releases/1.5.4/charts/
kubectl create ns istio-system
helm install istio-init istio.io/istio-init --namespace istio-system
# check above result `kubectl get crds | grep 'istio.io\|certmanager.k8s.io' | wc -l` should gt 25
# wait a few minutes
helm install istio istio.io/istio --namespace istio-system --set grafana.enabled=true
kubectl label ns default istio-injection=enabled
# check above result `kubectl get namespace -L istio-injection`
# re-create your application's pods
```

#### Grafana part

`your-app-grafana.yml`

```yaml
apiVersion: networking.istio.io/v1alpha3
kind: Gateway
metadata:
  name: grafana-gateway
  namespace: istio-system
spec:
  selector:
    istio: ingressgateway
  servers:
  - port:
      number: 15031
      name: http-grafana
      protocol: HTTP
    hosts:
    - "*"
---
apiVersion: networking.istio.io/v1alpha3
kind: VirtualService
metadata:
  name: grafana-vs
  namespace: istio-system
spec:
  hosts:
  - "*"
  gateways:
  - grafana-gateway
  http:
  - match:
    - port: 15031
    route:
    - destination:
        host: grafana
        port:
          number: 3000
```

```shell
kubectl apply -f k8s/your-app-grafana.yml
# check above result `kubectl get gateway -n istio-system`
```

#### Istio part

`k8s/your-app-istio.yml`

```yaml
apiVersion: networking.istio.io/v1alpha3
kind: Gateway
metadata:
  name: your-app-gateway
spec:
  selector:
    istio: ingressgateway
  servers:
  - port:
      number: 80
      name: http
      protocol: HTTP
    hosts:
    - "*"
---
apiVersion: networking.istio.io/v1alpha3
kind: VirtualService
metadata:
  name: your-app-vs
spec:
  hosts:
  - "*"
  gateways:
  - your-app-gateway
  http:
  - route:
    - destination:
        host: your-app
```

```shell
kubectl apply -f k8s/your-app-istio.yml
# check above result `kubectl get gw,vs`
kubectl get svc -n istio-system
```

# Squad Server Chart
The first beta release includes a persistent volume and a ClusterIP Service
https://artifacthub.io/packages/helm/squad/squad
## Installation
### Add repository
`helm repo add squad https://nicobleiler.github.io/squad-chart`
### Install chart
`helm install my-squad squad/squad --version 1.0.0-beta`
## Expose using nginx ingress
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: udp-services
  namespace: ingress-nginx
data:
  7787: "default/squad:game-udp"
  27165: "default/squad:query-udp"
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: tcp-services
  namespace: ingress-nginx
data:
  27165: "default/squad:query-tcp"
```
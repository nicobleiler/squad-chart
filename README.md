# Squad Server Chart
The first beta release includes a persistent volume and a ClusterIP Service
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
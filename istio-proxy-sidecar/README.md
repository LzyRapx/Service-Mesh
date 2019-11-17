### 1. 自动注入 sidecar (namespace 级别)

```
kubectl label namespace xxxx istio-injection=enabled
kubectl get namespace -L istio-injection
```
取消自动注入 sidecar:
```
kubectl label namespace istio-system istio-injection=disabled --overwrite
kubectl get namespace -L istio-injection
```
### 2. 手动注入sidecar (pod 级别)
```
spec:
  replicas: 3
  template:
    metadata:
      annotations:
        sidecar.istio.io/inject: "true"
```
不注入sidecar:
```
spec:
  replicas: 3
  template:
    metadata:
      annotations:
        sidecar.istio.io/inject: "false"
```

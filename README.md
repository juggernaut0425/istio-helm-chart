# istio-helm-chart
istio尝试


## values
* istio version: 0.8.0
	
* mtls.enabled: false

* rbacEnabled: true
* galley.enabled: true

* grafana.enabled: true
* prometheus.enabled: true
* servicegraph.enabled: true
* tracing.enabled: true
* tracing.jaeger.enabled: true


## 解析模版
 
 ```
 helm template ./ --name istio --namespace istio-system > $HOME/istio.yaml
 ```
 or
 
 ```
 helm install --dry-run --debug ./ --name istio --namespace istio-system
 ```
 
### 创建namespace

kubectl create namespace istio-system

### 安装 istio

```
kubectl create -f $HOME/istio.yaml
```

or

```
helm install --debug ./ --name istio --namespace istio-system
```



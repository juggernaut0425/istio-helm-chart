# istio-helm-chart
istio尝试


## values
* istio version: 0.8.0
	
* mtls.enabled: false

* rbacEnabled: true
* galley.enabled: false

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


## 使用4层模型
使运维人员可以配置service层的属性

[rule config](https://istio.io/docs/concepts/traffic-management/rules-configuration/)

### virtualService
通常由运维设置，负责：A/B测试，平滑升级，版本控制，超时/重试等

### DestinationRule
通常由 开发人员设置，熔断，负载均衡，TLS 等。发生在 virtualService 路由之后

### ServiceEntry

### Gateway


## 访问集群外数据库
By default, Istio-enabled services are unable to access URLs outside of the cluster because iptables is used in the pod to transparently redirect all outbound traffic to the sidecar proxy, which only handles intra-cluster destinations.







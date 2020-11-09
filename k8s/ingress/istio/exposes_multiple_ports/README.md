Assuming that Istio Gateway is serving TCP network connections, you might be able to combine one Gateway configuration for two external ports 80 and 5556:
```yaml
apiVersion: networking.istio.io/v1alpha3
kind: Gateway
metadata:
  name: myapp-gateway
spec:
  selector:
    istio: ingressgateway # use istio default controller
  servers:
  - port:
      number: 80
      name: port1
      protocol: TCP
    hosts:
    - example.myhost.com
  - port:
      number: 8088
      name: port2
      protocol: TCP
    hosts:
    - example.myhost.com
```
Field hosts identifies here a list of target addresses that have to be exposed by this Gateway.

In order to make appropriate network routing to the nested Pods, you can specify VirtualService with the matching set for the ports:
```yaml
apiVersion: networking.istio.io/v1alpha3
kind: VirtualService
metadata:
  name: myapp-virtual-service
spec:
  hosts:
  - example.myhost.com
  gateways:
  - myapp-gateway
  tcp:
  - match:
    - port: 80
    route:
    - destination:
        host: myapp.prod.svc.cluster.local
        port:
          number: 5556
  - match:
    - port: 8088
    route:
    - destination:
        host: myapp.prod.svc.cluster.local
        port:
          number: 5555
```
Above VirtualService defines the rules to route network traffic coming on 80 and 8088 ports for example.myhost.com to the myapp service ports 5556, 5555 respectively.

I encourage you to get more information about Istio TCPRoute capabilities and further appliance. https://istio.io/docs/reference/config/istio.networking.v1alpha3/#TCPRoute

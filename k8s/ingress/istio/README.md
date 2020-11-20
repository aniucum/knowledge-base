### istio
https://istio.io/latest/docs/

istioworkshop
https://www.istioworkshop.io/09-traffic-management/01-ingress-gateway/

https://medium.com/google-cloud/back-to-microservices-with-istio-p1-827c872daa53
Istio in Practice – Routing with VirtualService
https://rinormaloku.com/istio-practice-routing-virtualservices/

```yaml
kind: VirtualService
metadata:
  name: sa-external-services
spec:
  hosts:
  - "*"
  gateways:
  - http-gateway                      # 1
  http:
  - match:
    - uri:
        exact: /
    - uri:
        exact: /callback
    - uri:
        prefix: /static
    - uri:
        regex: '^.*\.(ico|png|jpg)$'
    route:
    - destination:
        host: sa-frontend             # 2
        port:
          number: 80
```

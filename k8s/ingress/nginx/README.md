### ingress-nginx
https://github.com/kubernetes/ingress-nginx/

- Check the Ingress Resource Events
```bash
kubectl get ing -n <namespace-of-ingress-resource>
kubectl describe ing <ingress-resource-name> -n <namespace-of-ingress-resource>
```
- Check the Ingress Controller Logs
```bash
kubectl get pods -n <namespace-of-ingress-controller>
kubectl logs -n <namespace> nginx-ingress-controller-67956bf89d-fv58j
```
- Check the Nginx Configuration
```bash
kubectl get pods -n <namespace-of-ingress-controller>
kubectl exec -it -n <namespace-of-ingress-controller> nginx-ingress-controller-67956bf89d-fv58j -- cat /etc/nginx/nginx.conf
```
- Check if used Services Exist
```bash
kubectl get svc --all-namespaces
```

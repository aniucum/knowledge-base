#### abbreviations
`po`=pods, `rc`=replicationcontroller, `svc`=services
#### k8s
- `kubectl get pods --all-namespaces` - fetch all Pods in all namespaces
#### JSONPath Support
https://kubernetes.io/docs/reference/kubectl/jsonpath/


kubectl delete pod monitoringservices-deployment-5fc7b49fdb-nkzq5  --grace-period=0 --force -n stscmon


kubectl get po -n toolkit | grep Terminating | tr -s ' ' | cut -d ' ' -f 1 | head -n 1

kubectl delete pod $(kubectl get po -n toolkit | grep Terminating | tr -s ' ' | cut -d ' ' -f 1 | head -n 1)  --grace-period=0 --force -n toolkit

kubectl get pods | grep Evicted | while read line ; do echo "$line" | awk '{print $1}' | sort | while read line2; do kubectl delete pod "$line2" ; done; done


DUMP
// pod-name         name of the postgres pod
// postgres-user    database user that is able to access the database
// database-name    name of the database
kubectl exec [pod-name] -- bash -c "pg_dump -U [postgres-user] [database-name]" > database.sql

RESTORE
// pod-name         name of the postgres pod
// postgres-user    database user that is able to access the database
// database-name    name of the database
cat database.sql | kubectl exec -i [pod-name] -n namespace -- psql -U [postgres-user] -d [database-name]

#### abbreviations
`po`=pods, `rc`=replicationcontroller, `svc`=services
#### k8s
- `kubectl get pods --all-namespaces` - fetch all Pods in all namespaces
#### JSONPath Support
https://kubernetes.io/docs/reference/kubectl/jsonpath/


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

### Инициализация кластера docker swarm
1. docker swarm init --advertise-addr 10.10.10.71:2377
2. docker swarm join-token -q manager
3. docker swarm join-token -q worker
4. docker swarm join --token TOKEN 10.10.10.71:2377

### Команды docker swarm. manager 10.10.10.71, worker 10.10.10.73
1. `docker service ls` - список сервисов
2. `docker service logs namespace_service` - просмотр логов сервиса

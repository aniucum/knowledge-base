https://github.com/stefanprodan/swarmprom
https://github.com/vegasbrianc/prometheus
docker stack deploy -c {{ app }}.yml prometheus --with-registry-auth

The Grafana Dashboard is now accessible via: http://<Host IP Address>:3000

username - admin
password - foobar (Password is stored in the `/grafana/config.monitoring` env file)

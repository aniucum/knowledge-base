cat << EOF > /etc/systemd/system/postgres.service
[Unit]
Description=postgres
After=docker.service
Requires=docker.service

[Service]
ExecStartPre=-/usr/bin/docker pull postgres:10
ExecStartPre=-/usr/bin/docker rm -f DB1
ExecStart=/usr/bin/docker run --restart=always \\
-p 5432:5432 \\
-v /opt/pgsql/data:/var/lib/postgresql/data \\
-v /opt/pgsql/all.sql:/var/lib/postgresql/all.sql \\
-e POSTGRES_DB=pentaho \\
-e POSTGRES_USER=pentaho \\
-e POSTGRES_PASSWORD=password \\
--name DB1 postgres:10
ExecStop=/usr/bin/docker stop DB1
ExecStopPost=-/usr/bin/docker rm -f DB1
ExecReload=/usr/bin/docker restart DB1

[Install]
WantedBy=multi-user.target
EOF

docker exec -it DB1  psql -U pentaho -f /var/lib/postgresql/all.sql
psql -U pentaho -f /var/lib/postgresql/all.sql
ALTER ROLE pentaho WITH password 'password';
cd /var/lib/postgresql && cp db*  data/ && cp root* data/ && cp *.conf data/ && chown postgres:postgres -R ./data/* && chmod 600 ./data/db* ./data/root*

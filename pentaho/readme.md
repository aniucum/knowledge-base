
- $path_install_pentaho/pentaho-server/start-pentaho.sh
```bash
CATALINA_OPTS="-Xms2048m -Xmx6144m -XX:MaxPermSize=256m -Djavax.net.debug=all  -Dcom.sun.jndi.ldap.object.disableEndpointIdentification=true  -Djavax.net.ssl.trustStore=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.292.b10-1.el7_9.x86_64/jre/lib/security/cacerts  -Dsun.rmi.dgc.client.gcInterval=3600000 -Dsun.rmi.dgc.server.gcInterval=3600000 -Dfile.encoding=utf8 -DDI_HOME=\"$DI_HOME\""
```
```bash
-Djavax.net.debug=all - включаем подробное логирование
-Dcom.sun.jndi.ldap.object.disableEndpointIdentification=true  - отключаем идентификацию ldaps сервера при ошибке `No subject alternative names matching IP address found`
```

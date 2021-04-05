- PKCS#1 to PKCS#8
```bash
openssl pkcs8 -topk8 -inform PEM -outform PEM -nocrypt -in /opt/logstash/config/.cert/logstash.key  -out /opt/logstash/config/.cert/logstash.key.pk8
```

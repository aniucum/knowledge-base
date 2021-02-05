

```bash
[redis_master]
redis1 ansible_host=192.168.97.108
redis2 ansible_host=192.168.97.109
redis3 ansible_host=192.168.97.115
```
```bash
- name: master redis.conf
  copy:
    dest: "/opt/redis/master/redis.conf"
    content: |
      bind 0.0.0.0
      slave-read-only yes
      port {{ master['clientport'] }}
      protected-mode no

      requirepass {{ redis_masterpass }}
      masterauth {{ redis_masterpass }}

      cluster-config-file nodes.conf
      cluster-announce-ip {{ ansible_default_ipv4.address }}
      cluster-announce-port {{ master['clientport'] }}
      cluster-announce-bus-port {{ master['busport'] }}
      cluster-enabled yes
      cluster-node-timeout 5000
      appendonly yes
  delegate_to: "{{ item }}"
  loop: "{{ groups['redis_master'] }}"
  ```

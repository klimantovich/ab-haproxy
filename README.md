# ab-haproxy

В плейбуке определено 3 роли (apt, ntp, haproxy).  
Прописываем ip кибаны (webui) в переменную kibana_node_ip: 10.0.5.13, которая будет использована при создании бэкенда в темплейте конфигурации.  
Итого конфигурация файла `/etc/haproxy/haproxy.conf` содержит 1 backend, который перенаправляет на хост с kibana:  
```
...
frontend hafrontend
    bind *:80
    mode http
    default_backend habackend

backend habackend
    mode http
    balance roundrobin
    option forwardfor
    server node1 10.0.5.13:80 check
```

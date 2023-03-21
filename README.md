https://opensearch.org/docs/latest/quickstart/ - OpenSearch Quickstart  
Делаем настройки виртуальной машины (либо на windows WSL для Docker Desktop, зайти в консоль и выполнить):  
```
sudo vi /etc/sysctl.conf
# Set max map count to the recommended value of 262144.
vm.max_map_count=262144
# Reload the kernel parameters.
sudo sysctl -p
```

Keycloak, создать пользователя:  
```
docker exec local_keycloak /opt/jboss/keycloak/bin/add-user-keycloak.sh  -u admin -p admin
docker restart local_keycloak
```

Дальше надо разбираться, как заставить OpenSearch работать c keycloak - https://opensearch.org/docs/latest/security/authentication-backends/openid-connect/  
Параметры в конфигу добавил закоментил, не завелось!  

Ссылки:
```
http://localhost:5601/app/home#/
http://localhost:28080/
http://localhost:28080/auth/realms/master/.well-known/openid-configuration
curl https://localhost:9200 -ku admin:admin
```
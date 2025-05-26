# Docker_nginx-react-djangoapi-
### 概要
- dockerでNginx, React, Django, MySQLコンテナを立ててNginxでReactの画面を表示させる

### 場所
```
cd projects\docker\docker_nginx-react-djangoapi-mysql
```

### exec
- app(React)
```
docker exec -it app bash
```
- api(Django)
```
docker exec -it api bash
```
- db(MySQL)(rootではいる(passは.envを参照))
```
docker exec -it db bash -u root -p
```
- web(Nginx)
```
docker exec -it web bash
```


### memo
#### default.confのDocker_Nginx-Djangoと違った点
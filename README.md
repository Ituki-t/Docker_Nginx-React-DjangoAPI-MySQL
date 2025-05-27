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


## memo
#### default.confのDocker_Nginx-Djangoと違った点


#### Reactの画面が真っ白になる場合
- f12で確認すると以下のエラーが出る場合
```
index.js:11 Invalid hook call. Hooks can only be called inside of the body of a function component. This could happen for one of the following reasons:
1. You might have mismatching versions of React and the renderer (such as React DOM)
2. You might be breaking the Rules of Hooks
3. You might have more than one copy of React in the same app
See https://react.dev/link/invalid-hook-call for tips about how to debug and fix this problem.
```
```
index.js:11 Invalid hook call. Hooks can only be called inside of the body of a function component. This could happen for one of the following reasons:
1. You might have mismatching versions of React and the renderer (such as React DOM)
2. You might be breaking the Rules of Hooks
3. You might have more than one copy of React in the same app
See https://react.dev/link/invalid-hook-call for tips about how to debug and fix this problem.
```
- ```node_modules```をインストールしなおすと解決する(手順を以下に示す)
1. コンテナに入る
```
docker exec -it app bash
```
2. 現在の```node_modules```を削除
```
rm -rf /app/node_modules
```
3. 新たに```node_modules```をインストール
```
npm install
```
4. 上記のステップで解決した。
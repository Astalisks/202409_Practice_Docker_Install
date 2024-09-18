# ゴール
- wsl2上のubuntu：dockerとcomposeが使用できるか確認する


## 動作確認手順解説

```

基本的には/02_sampleがうごけばOK
locahost:8080にアクセスして、「Hello from Docker!」が表示されればOK
$ sudo docker compose up

別ターミナルで確認
$ sudo docker ps -a
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                     NAMES
20b8b56e0e37   nginx:alpine   "/docker-entrypoint.…"   7 minutes ago   Up 7 minutes   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   02_sample-web-1
になっているはず（PORTSとNAMES）

全部止めて消すには
$ sudo docker stop $(docker ps -q)
$ sudo docker rm $(docker ps -a -q)
イメージも削除していいならさらに
$ sudo docker system prune -a

```


### 参考リンク
https://docs.docker.com/engine/install/ubuntu/
# ゴール
- wsl2上のubuntuにdockerをインストールする
  - docker composeもインストールする
    - 注意：docker-composeは古いので使用しないようにする


## Dockerのインストール手順解説
```bash
# 1. 古いDockerバージョンの削除
sudo apt remove docker docker-engine docker.io containerd runc

# 2. パッケージリストの更新と依存関係のインストール
sudo apt update
sudo apt install ca-certificates curl gnupg

# 3. Docker用のディレクトリ作成とGPGキーの追加
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

# 4. Dockerリポジトリの追加
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# 5. パッケージリストの再更新とDockerのインストール
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# 6. Dockerデーモンを有効化して起動
sudo systemctl enable docker
sudo systemctl start docker

# 7. DockerとDocker Composeのバージョン確認
docker --version
docker compose version

# 8. ユーザーをdockerグループに追加（オプション）
sudo usermod -aG docker $USER
# この後、一度ログアウトして再ログインするか、以下のコマンドを実行する
newgrp docker

※以下で動作を確認済み
Docker version 27.2.1, build 9e34c9b
Docker Compose version v2.29.2
```


### 参考リンク
[公式サイト](https://docs.docker.com/engine/install/ubuntu/)

# groupsession_docker
## 事前準備

### Windowsの場合

Windowsの場合はDocker Desktop及びWSLをインストール後に、WSL上で実行してください。
git はWindows側またはWSL側にインストールした状態としてください。

### Group Sessionのダウンロード

以下URLより使用許諾の上、ダウンロードください。

https://groupsession.jp/dl/dl.html

ダウンロード対象は用途によって次のモジュールをダウンロードください。

- 動作させるのみの場合  gsession.war
- 開発まで行う場合  gsession_src.zip

## 実行方法

### (1)動作環境のダウンロード(初回のみ)

```bash
git clone https://github.com/kazuihitoshi/groupsession_docker.git
```

### (2)Group Sessionモジュールの配置(初回のみ)

```bash
cd groupsession_docker/webapps
cp ダウンロードフォルダ/gsession.war .
```

Windowsの場合、Exploler より \\wsl$ のパスにてWSLフォルダを開き、ダウンロードファイルをコピーしてください。

### (3)Group Session起動

```bash
docker compose up -d
```

ブラウザより http://localhost:8080/gsession にてアクセス可能。

次回より、(3)のみで起動可能

## 開発方法

### プログラムコードの展開(初回のみ)

ダウンロードした「gsession_src.zip」を (2)で使用した webapps/gsessionに展開してください。

```bash
cd groupsession_docker/webapps/gsession
unzip ダウンロードしたgsession_src.zip
```

### 開発コンテナの起動

```bash
docker compose --profile dev up dev -d
```

起動完了後、vscodeでコンテナに接続して開発を行ってください。

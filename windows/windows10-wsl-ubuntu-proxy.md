2019.4.17
# Windows10にWSL（Windows Subsystem for Linux）を設定

## スペック・環境
- OS: Windows10 Pro
- Version: 1803
- PC: 64Bit/ RAM:8GB
- ネットワーク環境はProxyあり


## WSLの有効化
- スタート -> 設定 -> アプリ -> アプリと機能 -> 関連設定 -> プログラムと機能
- Windowsの機能の有効化または無効化 -> Windows Subsystem for Linuxにチェック -> OK
- 再起動


## Ubuntuのインストール
- スタート -> Microsoft Store
- Ubuntuで検索 -> Ubuntu 18.04 LTS
- 入手 -> ダウンロード完了 -> 起動


## Ubuntu起動
- ターミナルが起動し、Ubuntuの設定がはじまる
- ユーザー名・パスワードを設定する


## Proxy設定
- `sudo apt update`が失敗する
- `curl https://www.yahoo.co.jp`が失敗する
- Proxyが設定されていない -> **Windowsの設定は引き継がない**

```bash
# 確認
$ printenv http_proxy https_proxy

# 何も表示されない -> 設定されていない

# 設定: http://proxy.xxxx.co.jp:8080 -> proxyサーバー:ポート
$ vim ~/.bashrc
export http_proxy="http://proxy.xxxx.co.jp:8080"
export https_proxy=$http_proxy
$ source ~/.bashrc

# aptの設定にも
$ cd /etc/apt/
$ sudo vim apt.conf
Acquire::http::Proxy "http://proxy.xxxx.xo.jp:8080";
Acquire::https::Proxy "http://proxy.xxxx.xo.jp:8080";
```


## apt update
```bash
# リポジトリ一覧を更新
$ sudo apt update
...
...
# パッケージを更新
$ sudo apt upgrade
...
...
```


## 日本語環境
```bash
# 確認
$ echo $LANG
c.UTF-8

# 日本語パッケージをインストール
$ sudo apt install language-pack-ja
$ sudo update-locale LANG=ja_JP.UTF-8
$ exit

# 確認
$ echo $LANG
ja_JP.UTF-8
$ date
2019年  4月 17日 水曜日 13:29:07 DST
```


## コンソールの色を見やすくする
暗い青が見にくかったので、色を変更。
- レジストリエディタ -> HKEY_CURRENT_USER\Console
- ColorTable01（暗い青）：00800000（10進数のRGB表記のR0/G0/B128に対応）-> 00ff4221（R33/G66/B255）
- ColorTable09（明るい青）：00ff0000（R0/G0/B255）-> 00ff8021（R33/G128/B255）
- WSLを再起動

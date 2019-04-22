2019.4.22
# Windows10 WSL環境にTerrfaormとawscliをインストールする

## 環境
- OS: Windows10 Pro
- Version: 1803
- PC: 64Bit/ RAM:8GB
- WSL: Ubuntu 18.04 LTS

## unzipのインストール
```bash
$ sudo apt install unzip
```


## tfenvインストール
- Terraformのバージョン管理ツールtfenvを利用する
- tfenvのインストール
```bash
# ダウンロード
$ git clone https://github.com/tfutils/tfenv.git ~/.tfenv
# PATHに追加
$ vim .bashrc
PATH="$HOME/.tfenv/bin:$PATH"
$ source .bashrc
```


## Terraformのインストール
- Terraformはtfenvを利用してインストールする
- version: 0.12.0-beta2
```bash
# Terraformバージョン確認
$ tfenv list-remote
0.12.0-beta2
...
0.12.0-alpha1
0.11.13
...
# インストール
$ tfenv install 0.12.0-beta2
# 確認
$ terraform --version
Terraform v0.12.0-beta2
```


## pipのインストール
- https://docs.aws.amazon.com/ja_jp/cli/latest/userguide/install-linux.html
- aptでインストールするより、pipでインストールする方が最新を使える
- 最新バージョン確認は以下
  - https://github.com/aws/aws-cli/blob/master/CHANGELOG.rst
```bash
# インストールスクリプトのダウンロード
$ curl -O https://bootstrap.pypa.io/get-pip.py
# pipのインストール
$ python3 get-pip.py --user
Traceback (most recent call last):
  File "get-pip.py", line 21361, in <module>
    main()
  File "get-pip.py", line 197, in main
    bootstrap(tmpdir=tmpdir)
  File "get-pip.py", line 82, in bootstrap
    import pip._internal
  File "/tmp/tmpryzxzqaw/pip.zip/pip/_internal/__init__.py", line 40, in <module>
  File "/tmp/tmpryzxzqaw/pip.zip/pip/_internal/cli/autocompletion.py", line 8, in <module>
  File "/tmp/tmpryzxzqaw/pip.zip/pip/_internal/cli/main_parser.py", line 8, in <module>
  File "/tmp/tmpryzxzqaw/pip.zip/pip/_internal/cli/cmdoptions.py", line 14, in <module>
ModuleNotFoundError: No module named 'distutils.util'
# エラーがでるので、必要モジュールのインストール
$ sudo apt install python3-distutils
# 再度pipのインストール
$ python3 get-pip.py --user
...
Successfully installed pip-19.0.3 setuptools-41.0.0 wheel-0.33.1
# PATHに追加 ※注意aws公式サイトでは.Localとなっているが、実際は.localだった
$ vim .bashrc
PATH="~/.local/bin:$PATH"
$ source .bashrc
# 確認
$ pip3 --version
pip 19.0.3 from /home/.../.local/lib/python3.6/site-packages/pip (python 3.6)
```


## awscliのインストール
```bash
# インストール
$ pip3 install awscli --upgrade --user
...
Successfully installed awscli-1.16.144 botocore-1.12.134 docutils-0.14 jmespath-0.9.4 python-dateutil-2.8.0 rsa-3.4.2 s3transfer-0.2.0
# 確認
$ aws --version
aws-cli/1.16.144 Python/3.6.7 Linux/4.4.0-17134-Microsoft botocore/1.12.134
```


## （補足）awscliを最新バージョンにアップグレードする
```bash
$ pip3 install awscli --upgrade --user
```

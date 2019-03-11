# python2, 3系の共存（Windows10）

## 1. インストール
- 公式サイトより3系と2系のインストーラーをダウンロード
  - 64bit版であることを確認
- インストール
  - 順序は考慮しなくていい（はず）
  - 3系のインストール時は以下に注意
    - Customize installationでインストール先を指定（デフォルトだと深くなる。2系に合わせる）
      - c:\Python37
    - Add Python3.7 to PATHにチェック
- PATH（環境変数）の追加
  - 3系は上でチェックを入れれば自動で追加される
  - 2系は自分で追加する
    - Path
      - C:\Python27\
      - C:\Python27\Scripts


## 2. 起動方法
- 2系: `py -2`
- 3系: `py -3`


## 3. 確認
```sh
# version
$ py -2 --version
Python 2.7.16

$ py -3 --version
Python 3.6.6

# インタープリタ
$ py -2
Python 2.7.16 (v2.7.16:413a49145e, Mar  4 2019, 01:37:19) [MSC v.1500 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>

$ py -3
Python 3.6.6 (v3.6.6:4cf1f54eb7, Jun 27 2018, 03:37:03) [MSC v.1900 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.

# ファイル実行
$ py -2 xxx.py

$ py -3 xxx.py
```


## 4. pip
```sh
# 2系
$ py -2 -m pip --version
pip 18.1 from C:\Python27\lib\site-packages\pip (python 2.7)

$ pu -2 -m pip install xxx

# 3系
$ py -3 -m pip --version
pip 18.1 from C:\Python36\lib\site-packages\pip (python 3.6)

$ py -3 -m pip install xxx
```


## 5. 仮想環境
```sh
# 2系 virtualenv
$ py -2 -m pip install virtualenv

$ py -2 -m virtualenv env2

$ ./env2/Scripts/activate
(env2) > python --version
Python 2.7.16
$ deactivate

# 3系 venv
$ py -3 -m venv env3
$ ./env3/Scripts/activate
(env3) > python --version
Python 3.6.6
$ deactivate
```

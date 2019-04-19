2019.4.19

# GitHubが認識する主要言語を変更する
- GitHubにはリポジトリ内が何言語で書かれているかを解析して、一番多い言語を主要言語として表示する
- データ用.htmlとかが一番多い場合、メイン言語が主要言語として表示されない

## 解決方法
- リポジトリ直下に「.gitattributes」ファイルを作成
- 認識されたくないファイルやディレクトリをベンダーパスとして定義する
```
data/* linguist-vendored
sample/xxx.html linguist-vendored
```

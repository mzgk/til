2019.4.1

# RDSのポイントインタイムリカバリは自動バックアップが必要
- 自動バックアップが有効になっていないと使えない
- 手動でスナップショットを採取してもダメ
- 自動バックアップが有効だとしても、データベース一覧画面で選択→アクションがグレーアウトされている場合がある
- その場合は、データベースを選択→データベース画面のアクションボタンから実行

## AWS CLIでリカバリポイントを取得する
- rds describe-db-instancesの"LatestRestorableTime"の値

```
aws rds describe-db-instances --db-instance-identifier DB識別子

# Pythonでインストールしたならば
py -3 -m awscli rds describe-db-instances --db-instance-identifier DB識別子
```

## その他
- https://aws.amazon.com/jp/rds/faqs/
>Amazon RDS の自動バックアップ機能によって、DB インスタンスのポイントインタイムリカバリが可能になります。DB インスタンスに対して自動バックアップがオンになっている場合、Amazon RDS は毎日、お客様のデータの完全なスナップショットを自動的に作成し (任意のバックアップウィンドウ中に実施)、トランザクションログを取得します (DB インスタンスに対する更新が実施される)。


- https://docs.aws.amazon.com/ja_jp/AmazonRDS/latest/UserGuide/USER_PIT.html
>RDS は、DB インスタンスのトランザクションログを 5 分ごとに Amazon S3 にアップロードします。DB インスタンスの復元可能な直近の時間を調べるには、AWS CLI の describe-db-instances コマンドを使用し、DB インスタンスの [LatestRestorableTime] フィールドに返される値を参照します。AWS マネジメントコンソール で、このプロパティは DB インスタンスの最新の復元時間として表示されます。バックアップ保持期間の任意の時点に復元できます。

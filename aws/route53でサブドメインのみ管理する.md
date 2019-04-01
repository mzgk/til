# Route53でサブドメインを管理する
Route53以外でドメイン管理をしていて、サブドメインのみをRoute53で管理（委任）する場合の手順。
例）
- sample.com: お名前.com
- stg.sample.com: Route53

## 1. Route53に委任先のHostedZoneを作成する
- 管理したいサブドメインのHosted Zoneを作成する
- Route53-Hosted Zone-Create Hosted Zone
  - Domain Name: サブドメイン名
  - Type: Public Hosted Zone


## 2. 作成したHosted ZoneにRecordを追加する
- 1.で作成したHosted Zoneにそのサブドメインを割り当てるリソース情報を登録する
- Route53-Hosted Zone-Create Record Set
  - Name: なし
  - Type: CNAME
  - Alias: Yes（AWSリソースを登録する場合。今回はALB）
  - Alias Target: example-1.us-east-2.elb.amazonaws.com（ALBのDNS名）


## 3. お名前.comのDNSにNSレコードを登録する
- 1.でHosted Zoneを作成した際に割り振られたNSレコードの値（Value項目のns-で始まる４つ）
- このNSレコードをstg.sample.comのネームサーバとして、お名前.comにDNS委任登録をする
  - お名前.com側で作成したstg.sample.comにNSレコードとして４つを登録する

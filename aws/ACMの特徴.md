# ACMの特徴
- リージョンを越えての適用はできない
- 複数リージョンで同じドメイン名で発行できる
  - ALB（東京）、CloudFront（グローバル）がある場合に、*.aaa.comを東京とバージニア北部で発行
- ワイルドカードのドメイン名で発行する中に、追加の名前でネイキッドドメインを設定できる
  - ドメイン名: *.aaa.com, 追加の名前: aaa.comで１つとして発行できる
- CloudFrontへの適用は、us-east-1で発行したACMのみ
- CloudForntに適用する際、初めてACMを発行した場合は、適用可能の選択ができるまでに時間がかかる
  - 3時間程度
- https://docs.aws.amazon.com/ja_jp/acm/latest/userguide/acm-certificate.html

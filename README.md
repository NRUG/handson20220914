# handson20220914
NRUG (New Relic User Group) Vol.4 のハンズオン資料です

# ハンズオン手順

##  あらかじめ用意するもの
- AWS EC2 Instance
EC2 Instanceの前提で進めますが、SSH接続ができるLinux環境であればなんでも構いません。  
t2.micro程度で問題ありません。
EC2 instanceの場合はAmazonLinux2の前提で進めます。  
EC2インスタンスのセットアップを行うAWS CloudFormationを提供します。
必要に応じてご利用ください。

また、EC2費用はご自身でご負担ください。
Macに直接インストールでも問題ないと思われます。その場合は適宜読み替えてください。

- New Relicに登録ができるメールアドレス

## 1 New Relicの登録
[New Relicの登録](ch1.md)
## 2 New Relic infrastructure agentの説明とinstall
[New Relic infrastructure agentの説明とinstall](docs/ch2.md)
## 3 Djangoのセットアップ、New Relic Python agentのinstall
[Djangoのセットアップ](ch3.md)
## 4 New Relic Python agent の説明
[New Relic Python agent の説明とinstall](ch4.md)
## 5 New Relicのコンソールを眺める
[New Relicのコンソールを眺める](ch5.md)
## よくある質問
[よくある質問](FAQ.md)

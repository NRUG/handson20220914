# handson20220914
NRUG (New Relic User Group) Vol.4 のハンズオン資料です

# ハンズオン手順

##  あらかじめ用意するもの

### AWS EC2 Instance

EC2 Instanceの前提で進めますが、SSH接続ができるLinux環境であればなんでも構いません。  
t2.micro程度で問題ありません。
EC2 instanceの場合はAmazon Linux2の前提で進めます。  
EC2インスタンスのセットアップを行う[AWS CloudFormation](aws_cfn.yml)を提供します。
必要に応じてご利用ください。EC2へのログインはSessionManagerから行う前提のものが作成されます。

また、EC2費用はご自身でご負担ください。
Macに直接インストールでも問題ないと思われます。その場合は適宜読み替えてください。

EC2の構築やログイン方法についての詳細の記述は省略しております。

### New Relicに登録ができるメールアドレス

FreeTier（無料枠）で完結する前提で進めます。FreeTierで登録するメールアドレスが必要です。

## 1 New Relicの登録
[New Relicの登録](ch1.md)
## 2 New Relic infrastructure agentの説明とinstall
[New Relic infrastructure agentの説明とinstall](docs/ch2.md)
## 3 Djangoのセットアップ、New Relic Python agentのinstall
[Djangoのセットアップ](ch3.md)
## 4 New Relic Python agent の説明
[New Relic Python agent の説明](ch4.md)
## 5 New Relicのコンソールを眺める
[New Relicのコンソールを眺める](ch5.md)
## よくある質問
[よくある質問](FAQ.md)

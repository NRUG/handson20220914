# New Relic アカウントの初期設定
新しく作成されたばかりのアカウントはガイド付きインストールの画面が表示されます。  
このままInstallを開始する場合は画面の指示に従って、InstallCommandをコピーして実行します。
![](https://github.com/qryuu/handson20220914/blob/main/ScreenShot/2022-09-19_19h30_55.png)

ガイド付きインストール画面で表示されるLicenseKeyは後から差し替える事ができません。  
LicenseKeyのローテーションを行いたい場合は、ガイド付きインストール画面を抜けて、LicenseKeyの作成を行います。  
`See other Option`をクリックするとガイド付きインストール画面が閉じます。
![](https://github.com/qryuu/handson20220914/blob/main/ScreenShot/2022-09-19_19h30_39.png)

# LicenseKeyの発行
Userメニューを開き、API Keys をクリックします。
![](https://github.com/qryuu/handson20220914/blob/main/ScreenShot/2022-09-19_19h31_52.png)

Create KeyをクリックしてLicenseKeyを作成します。
![](https://github.com/qryuu/handson20220914/blob/main/ScreenShot/2022-09-19_19h32_27.png)

## Keyの種類
- User Key 
  - NerdGraphやREST APIなどNRDBのData参照やNew Relicの操作を行う時に利用するKeyです。
- Ingest - License
  - Infrastructure AgentやAPM AgentなどDataをNew Relicに送る際に利用します。 非公開にする必要があるKeyです。
- ingest - Browser
  - Browser AgentがDataをNew Relicに送る際に利用します。 WEBページのヘッダーとして公開される事を前提としているKeyです。

Infrastructure AgentやAPM Agnetで利用するKeyは`Ingest - License` Keyです。
![](https://github.com/qryuu/handson20220914/blob/main/ScreenShot/2022-09-19_19h32_46.png)

作成したKeyの三点リーダーメニューをから`Copy Key` をクリックして、Keyをコピーしておきます。
コマンドの`license_key: YOUR_LICENSE_KEY` をこのコピーしたKeyに置き換えて実行します。
![](https://github.com/qryuu/handson20220914/blob/main/2022-09-19_19h34_09.png)

# インストールメニューの表示
UserメニューからAdd more data をクリックすると、ガイド付きインストールのメニューが表示されます。  
今回のハンズオン以外の様々なAgentやIntegrationをインストールする場合はここからメニューを選択します。  
![](https://github.com/qryuu/handson20220914/blob/main/ScreenShot/2022-09-19_19h34_35.png)

# インストール手順

## New Relicのライセンスキーを環境変数に入れます。
YOUR_LICENS_KEYの部分を書き換えます

```
# echo "license_key: YOUR_LICENSE_KEY" | sudo tee -a /etc/newrelic-infra.yml
```

## Agentをレポジトリからインストールします

```
# sudo curl -o /etc/yum.repos.d/newrelic-infra.repo https://download.newrelic.com/infrastructure_agent/linux/yum/amazonlinux/2/x86_64/newrelic-infra.repo
# sudo yum -q makecache -y --disablerepo='*' --enablerepo='newrelic-infra'
# sudo yum install newrelic-infra -y
```

## Agentの動作確認

```
# ps ax | grep newrelic
```

New Relic infrastructure agent は yum install したタイミングで起動しています。
プロセスでの確認で起動しているか確認します

例
```
 3494 ?        Ssl    0:00 /usr/bin/newrelic-infra-service
 3500 ?        Sl     0:00 /usr/bin/newrelic-infra
 4093 pts/0    S+     0:00 grep --color=auto newrelic
```

## New Relic にデータが送信されていることを確認する

New Relicにログインし、infrastructureのデータが取得できることを確認する。
（後で何か画像を貼る）


# 参考URL
https://docs.newrelic.com/docs/infrastructure/install-infrastructure-agent/linux-installation/install-infrastructure-monitoring-agent-linux/

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

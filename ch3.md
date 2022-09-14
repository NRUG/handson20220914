# デモアプリの設定
今回はデモアプリとして、Djangoを利用します。
Djangoの設定を行いつつ、同時にPython APM agentもインストールします。

## Djangoのセットアップ
```
$ python3 -m pip install Django
$ django-admin startproject demo-app
$ django-admin startproject demoapp
$ cd demoapp/
```

## Python APM agentのインストール
```
$ python3 -m pip install newrelic
$ newrelic-admin generate-config 〜ライセンスキー〜 newrelic.ini
$ vi manage.py
```

以下をimport sysの下に追記します
```
import newrelic.agent
newrelic.agent.initialize('newrelic.ini')
```

```
$ python3 manage.py runserver
```

## SQLiteのアップデート
amazon Linux2の場合、デフォルトではいるSQLiteが古いため、自分でコンパイルします。
以下のコマンドを脳死でコピーして実行してください

```
$ cd
$ wget https://www.sqlite.org/2020/sqlite-autoconf-3340000.tar.gz
$ tar xvfz sqlite-autoconf-3340000.tar.gz
$ cd sqlite-autoconf-3340000
$ ./configure --prefix=/usr/local
$ sudo yum groupinstall "Development Tools"
$ ./configure --prefix=/usr/local
$ make
$ sudo make install
$ sudo mv /usr/bin/sqlite3 /usr/bin/sqlite3_old
$ sudo ln -s /usr/local/bin/sqlite3 /usr/bin/sqlite3
$ echo export LD_LIBRARY_PATH="/usr/local/lib" >> ~/.bash_profile
$ source ~/.bash_profile
$ sqlite3 --version
```

## デモアプリの起動
```
$ cd ~/demoapp/
$ vi demoapp/settings.py
$ ALLOWED_HOSTS = ['35.78.205.93']

$ python3 manage.py runserver 0.0.0.0:8000
```

## 参考URL



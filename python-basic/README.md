# 作業手順

## １．作業環境を作成する

### 1-1 任意の場所に作業環境を作る。以下は実例

（ターミナル作業）

```bash
cd ~　　　　   # ホームに戻る
cd ~/source   # ここを起点にする
mkdir youtube # youtube学習をまとめるフォルダを作成
cd youtube    # 作ったフォルダに移動
mkdir web-life-ch   # 今回のプロジェクトルートを作成
cd web-life-ch      # プロジェクトルートに移動
```

### 1-2 Python3で仮想環境をつくる

「python3 -m venv python-basic」コマンドを打って仮想環境をつくる

- python3のエイリアスをpythonで登録しておくと「python」コマンドがつかえる
- -m はモジュール実行させるためのオプションで、ここではpython2に標準装備されているモジュールvenvの実行を指示している
- python-basicは仮想環境名で、任意の名を指定できる。ここでは環境名としてpython-basicを指定している

```bash
python3 -m venv python-basic
```

### 1-3 Djangoをインストールする

```bash
pip install django
```

## ２ アプリケーション（ひな形）を作る

[参考動画](https://youtu.be/TkgnA-reQLc?si=MJ3TLEAfmir6pHCa)

[参考資料](https://docs.djangoproject.com/ja/4.1/intro/tutorial01/#creating-the-polls-app)


### 2-1 `python manage.py startapp アプリ名`


```bash
# pwdコマンドで（外側の）myappnに居ることを確認
pwd # 例~/source/youtube/web-life-ch/myapp

# まずは、accountsアプリを作る
python manage.py startapp accounts

# 続いて、postsアプリを作る
python manage.py startapp posts
```

### 2-2 appひな形を登録

ファイル`myapp/myapp/settings.py`を編集

```python
(略)
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'accounts',    # <---- 追記
    'posts',       # <---- 追記
]
(略)
```

## ３ 管理者ユーザー（SuperUser）の作成

### 3-1 準備

#### 3-1-1 外側の`myapp`に居ることを確認してから`python manage.py runserver`でローカルの開発サーバーを起動する

下記のエラーメッセージが出ていることを確認する

`You have 18 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.`

#### 3-1-2 `python manage.py migrate`でマイグレートを実行する

`control+c`で開発サーバーを終了させて、エラーメッセージの中にある指示に基づいてマイグレートする

```zsh
python manage.py migrate
```

### 3-2 createsuperuserコマンドを実行

下記は実行例です。

```python
python manage.py createsuperuser
Username (leave blank to use 'hoge'): test@test.com
Email address: test@test.com
Password: testtest
Password (again): testtest
The password is too similar to the username.
This password is too common.
Bypass password validation and create user anyway? [y/N]: y
Superuser created successfully.
```

### 3-3 ローカル開発サーバーを起動して確認する

`python manage.py runserver`を打ってサーバーを起動して、ブラウザから「 http://127.0.0.1:8000/admin/ 」にアクセスして、管理者ユーザーでログインできるか確認してみる。

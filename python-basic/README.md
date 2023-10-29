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



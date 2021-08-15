# bbs_local
アプリ名

## 対象OS
Windows10

## セットアップ方法

1. postgresを構築します

	[参考URL]  
	https://lets.postgresql.jp/documents/tutorial/windows/1

1. アプリのDBを作成します
	1. SQL Shell(psql)を起動し、案内に従い入力  
	
	```
	
	Server [localhost]:						#何も入力しない  
	Database [postgres]:					#何も入力しない
	Port [5432]:							#何も入力しない
	Username [postgres]:					#何も入力しない
	Client Encoding [SJIS]:					#何も入力しない
	ユーザ postgres のパスワード:			#インストール時に入力したパスワード
	psql (13.3)
	"help"でヘルプを表示します。
	
	postgres=#
	
	```  
	
	2. 以下のコマンドを実行  
	
	```
    
	create database bbs;
    create user python with password '任意のパスワード';
    GRANT ALL ON DATABASE bbs TO python;
    \q
	
    ```
	
    上記、実行後ログインできるか確認してください  
    SQL Shell(psql)を起動し、  
    
    ```
	
    Server [localhost]:               #何も入力しない
    Database [postgres]:bbs          
    Port [5432]:                      #何も入力しない
    Username [postgres]:python
    Client Encoding [SJIS]:           #何も入力しない
    ユーザ python のパスワード:		  #先ほど入力したパスワード
    psql (13.3)
    "help"でヘルプを表示します。

    bbs=#
    
	```

1. 環境変数を設定します
	1. コマンドプロンプトを起動し、以下のコマンドを実行します
    
	```
	
	setx DATABASE_USER python
    	setx DATABASE_PASS __任意のパスワード__　        #2.iiで入力したパスワード
    	setx DATABASE_HOST localhost
    	setx DATABASE_NAME bbs
    	setx FLASK_SECRETKEY __任意のシークレットキー__  #例　\xr4\xh6\x9bc\xt4\xa8\xdb\xaa\x3g\xe3\x98SR\xda\xb2@\x45\x52\xw4nB\xda\xu4\x84

	```

1. pythonのインストール  
	[参考URL]	  
	https://www.python.jp/install/windows/install.html  


1. アプリの実行
	1. githubからソースコードをダウンロードし、コマンドプロンプトでインストールしたフォルダを開きます
	2. pip install -r requirements.txt　と入力しエンターキーを押下します
	3. パッケージがインストールされることを確認します
	4. python app\run.py　と入力しエンターキーを押下します
	5. webブラウザで　localhost:5050　にアクセスします

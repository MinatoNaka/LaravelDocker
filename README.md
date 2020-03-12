docker-compose settings for laravel

* このリポジトリをcloneする  
* `source` ディレクトリを作成
* `docker-compose up -d` を実行
* `docker exec -it {php-fpmのコンテナ名} bash` でコンテナにログイン
* `composer create-project --prefer-dist laravel/laravel ./` でLaravelプロジェクト作成
* http://localhost でアクセスしたらホーム画面が表示される

DBに接続するための.env設定
```
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel_db
DB_USERNAME=laravel_user
DB_PASSWORD=password
```

Redisを利用するための.env設定
```
CACHE_DRIVER=redis
SESSION_DRIVER=redis
REDIS_HOST=redis
REDIS_PASSWORD=
REDIS_PORT=6379
```

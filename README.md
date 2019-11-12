docker-compose settings for laravel

* このリポジトリをcloneする  
* `source` ディレクトリを作成
* `docker-compose up -d` を実行
* `docker exec -it {php-fpmのコンテナ名} bash` でコンテナにログイン
* `composer create-project --prefer-dist laravel/laravel ./` でLaravelプロジェクト作成
* http://localhost でアクセスしたらホーム画面が表示される


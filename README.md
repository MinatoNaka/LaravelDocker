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

minioを利用するための設定
.env
```
# AWS config
AWS_URL=http://minio:9000
AWS_ACCESS_KEY_ID=s3id
AWS_SECRET_ACCESS_KEY=s3secret
AWS_DEFAULT_REGION=us-east-1
AWS_BUCKET=laravel-bucket
AWS_PATH_STYLE_ENDPOINT=true
```

パッケージインストール  
`composer require league/flysystem-aws-s3-v3`

config/filesystems.php
```$xslt
's3' => [
    'driver' => 's3',
    'key' => env('AWS_ACCESS_KEY_ID'),
    'secret' => env('AWS_SECRET_ACCESS_KEY'),
    'region' => env('AWS_DEFAULT_REGION'),
    'bucket' => env('AWS_BUCKET'),
    'url' => env('AWS_URL'),
    'use_path_style_endpoint' => env('AWS_PATH_STYLE_ENDPOINT', false),
    'endpoint' => env('AWS_URL'),
],
```

tinkerでアップロード確認
```
$ php artisan tinker
>>> Storage::disk('s3')->put('hello.json', '{"hello": "world"}')
=> true
```
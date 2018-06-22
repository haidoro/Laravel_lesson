# Laravel 開発ノート
## MacにComposerを導入
Homebrewが導入済みであること。
Composerを探します。
```
brew search composer
```
Composerの導入。
```
brew install composer
```
Composerバージョン確認
```
composer -V
```
最初にComposerを使用し、Laravelインストーラをダウンロードします。
```
composer global require "laravel/installer"
```
ターミナルでComposerのcreate-projectコマンドを実行し、Laravelをインストール
この場合はblogフォルダにlaravel5.5をインストール
```
composer create-project --prefer-dist laravel/laravel blog "5.5.*"
```
`cd`でblogフォルダに移動して次のコマンドで「http://localhost:8000/」で初期画面が表示
```
php artisan serve
```
artisan serveを停止するには「コントロールキー＋C」

## Reactの導入

以下コマンド実施
```
php artisan preset react
```

`Please run "npm install && npm run dev" to compile your fresh scaffolding.`と表示されるので、以下コマンドを実施。
```
npm install
```
```
npm run dev
```
## viewの作成
blog/resources/views/にreact_sample.blade.php
```
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>React Sample</title>
</head>
<body>
<div id="example"></div>
<script src="{{asset('/js/app.js')}}"></script>
</body>
</html>
```

## ルーティングの作成
 blog/routes/web.php
 ```
 Route::get('sample/react', 'SampleController@react');
 ```
この段階で`http://localhost:8000/sample/react`とアドレスを入れても「Class App\Http\Controllers\SampleController does not exist」とlaravelのエラー表示がされます。

## コントローラーの作成
コントローラーの作成は以下のコマンド
```
php artisan make:controller SampleController
```
blog/app/Http/Controllers/SampleController.php
```
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class SampleController extends Controller
{
  public function react()
  {
    return view('react_sample');
  }
}
```

## ビルド設定
laravel/webpack.min.js
```
let mix = require('laravel-mix');

/*
 |--------------------------------------------------------------------------
 | Mix Asset Management
 |--------------------------------------------------------------------------
 |
 | Mix provides a clean, fluent API for defining some Webpack build steps
 | for your Laravel application. By default, we are compiling the Sass
 | file for the application as well as bundling up all the JS files.
 |
 */

mix.react('resources/assets/js/components/Example.js', 'public/js/app.js');

```

## ビルドを実行する

```
npm run dev
```

動作確認
```
php artisan serve
```
http://localhost:8000/test/react


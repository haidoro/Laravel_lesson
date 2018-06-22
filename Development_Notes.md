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

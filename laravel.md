# Laravel  
## php artisan
* アルチザン。Laravelで使われるCLI
* php artisan migrate
  * Laravelのマイグレーション機能では、まずマイグレーションファイルというphpファイルを作成して、その中にアプリケーションで利用したいテーブルの定義（カラムの名前・データ型・制約など）を記述します。
  * マイグレーションファイルはデータベースの設計書のようなもので、設計書を記述し終わった後でArtisan migrateコマンドを実行すると、Laravelがその内容をもとに自動でデータベースを構成します。
  * --create=テーブル名
  * upはマイグレーションを実行する時の処理、downはマイグレーションをロールバックする時に実行される処理です。
* php artisan make:seeder
  * DB のテーブルを作成したらテストでサンプルデータをいれる。Laravel においてシーダーとはデータベースにテストデータを一斉に挿入する処理を指します。EloquentかDBファサードでデータを入れる。
  * php artisan db:seed コマンドで DatabaseSeeder.php 内のrunメソッド が実行されるようになります。
* php artisan make:model
  * make:model はEloquentモデルの自動生成コマンドです。
  * MVCアーキテクチャの「M」にあたる部分で、主にデータベースとの連携を行います。LaravelにおけるModelは、Eloquent（DBのデータを操作する実装）の機能とビジネスロジックを持ったクラスです。
  * 基本的には1つのテーブルに1つのModelが存在します。（中間テーブルなどModelを持つ必要がないケースもあります）
  * Eloquent Modelのfillableとguardedの違い
    * fillableはホワイトリスト(指定した属性のみ代入可能)で、guardedはブラックリスト（指定した属性は代入不可能）です。例えばidや作成日は変更できないほうがいい。
* php artisan make:controller
  * LaravelではHTTPリクエストがあった場合に、routes/web.phpやroutes/api.phpのルーティング確認して、リクエストが何処に振り分けられるか決まります。
    * web.phpには画面のフォームからのリクエストを処理するルーティングを書きます。
    * api.phpにはSPAなど、ajax通信で通信する場合のルーティングを書きます。
  * このルーティングファイルにコントローラーとメソッドを指定します。POSTリクエストやGETリクエストでリクエストがあった場合に、指定されたコントローラーで処理されるといった感じです。
    * Route::get('/test', 'TestController@test');
  * それぞれのメソッドでCRUDを実現
    * index	一覧表示(Read)
    * create	新規作成のためのフォーム表示(Create)
    * store	新規作成のためのデータ保存(Create)
    * show	1件の詳細表示(Read)
    * edit	既存レコードの変更のためのフォーム表示(Update)
    * update	既存レコードの変更のためのデータ保存(Update)
    * destroy	既存レコードの削除(Delete)

## Eroquent
* Eloquentとはデータベースとモデルを対応づける機能です。事前にモデルModelを作成して登録できる項目を宣言しておく必要があります。
* EloquentのDB挿入更新メソッド saveとupdateは処理が異なる
  * save(): 更新データとの差分を見てないで更新 -> updated_atのカラムが更新されない
  * update(): 更新データとの差分を見て更新するか決めてる -> updated_atのカラムが更新される
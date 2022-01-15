# Docker
## 3層アーキテクチャのコンテナの構築
* Web Server  
  * nginx, Apache
    * HTTP Requestに対する静的コンテンツ配信サーバを構築
    * Nginx の方が処理が軽く大量のリクエストを処理するのに向いていおり、さらにリバーシプロキシ機能までついているおまけ付きであり、現在では Nginx の方が人気らしい
* Application Server  
  * PHP, ruby
    * nginxを経由してPHPを動作させるアプリケーションサーバを構築
    * PHPパッケージ管理ツールComposerのインストール
* DB server  
  * MySQL
## Dockerfile  
* Dockerのイメージを作成する際に実行するコマンドをコード化して、一つのファイルにまとめたものです
* image:  
  * ymlに指定：コンテナを起動させるイメージを指定します。
  * 公式のnginxイメージをそのまま利用しています。(Dockerfileは不要)
## Docker Compose
複数のコンテナで構成されるアプリケーションについて、Dockerイメージのビルドや各コンテナの起動・停止などをより簡単に行えるようにするツール  
イメージはコンテナのスナップショットで、コンテナは走らせているイメージのインスタンス、ということになるのでしょうか。（dockerのイメージをdockerfileから組み立てて、そのイメージを走らせるとコンテナになると）  
![image](https://hacknote.jp/wp-content/uploads/2020/03/docker_image_container-500x248.png)
* docker compose build
  * サービスのビルドを実行します。サービスとは「web」や「db」のことを指します。ビルドとは、構築するimageはdocker-compose.ymlファイルに定義されているもの、またはDockerfileを参考にして構築します。（コンテナは作成しません）
  * docker-compose run web rails s
* docker compose run
  * 引数で指定したサービスのコンテナを作成してから、コンテナ内でコマンドを実行します。
  * docker-compose run web rails s
* docker compose up
  * イメージ＆コンテナ作成＆起動
  * オプションで-dをつけることでバックグラウンドで実行することができます。またオプションで--buildをつけることで起動前にイメージも構築します。
* docker compose exec
  * 既に立ち上がっているコンテナでコマンド実行します。
  * docker compose exec mysql echo 'hello'
* docker compose down
  * コンテナを破棄
aaa      aaaaaaaa  
a  
aa  

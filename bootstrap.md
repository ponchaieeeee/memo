# bootstrap
Twitter社が開発しているCSSフレームワーク
## Grid System
* レイアウトを格子状に分解して配置するデザイン手法。パソコンやスマホなど画面幅が異なってもレイアウトを組み替えやすくなり、複雑なレイアウトでも簡単にレスポンシブにできます。
* Bootstrapでは横幅を12分割したグリッドシステムを採用
  * class = “container”（固定枠）または”container-fluid”（流動枠）の中に書く
    * 画面幅	Extra small	Small	Medium	Large	Extra large .container幅	auto	576px	720px	940px	1140px
    * レイアウトが切り替わる画面幅をブレイクポイントといいます。Bootstrapでは5つのブレイクポイントがある
    * .container-fluidは、ブラウザのウィンドウ幅いっぱいに広がります。ウィンドウのサイズを狭くしたり広くしたりすると、.container-fluidの幅も流動的に変化します。
  * class = “row”の中に書く
  * class = “col-{prefix}-{columns}”の形で書く
    * columnsは合計が12になるようにする
    * 合計12より少ない場合、左詰め
    * 合計12より大きい場合、改行
  * 各カラムに対してスマホ（極小＝xs）とパソコン（大＝lg）のクラスを記述すればOKです。1行で横並びするカラムの合計グリッド数に気をつけます。12をこえると、画面上でカラムは次の行へ下ります。  
  div class="container  
    div class="row"  
      div class="col-xs-6 col-lg-4"  
      div class="col-xs-6 col-lg-4"  
      div class="col-xs-12 col-lg-4"  

* a
# React
Reactで作られるアプリケーションは、すべて『コンポーネント（Component）』の組み合わせで構成

## Fundamental thought
基本的にルートポイントとなるスクリプト（例：app.js）を用意して、そこからまたルートとなる Component（Container とも呼ばれる）を呼んだり、Redux の Store を作って Provider と合体させたりというのがセオリーらしい。

## ReactDOM.render()
呼び出した HTML の決められた箇所に DOM ツリーを出力

## Material UI
* Material-UI には Theme という概念があります。（「Theming」と呼ばれているようです。）よくあるテーマってやつだね
  * Theme により色や配置などのデザインが決まる。
  * 何もしなくてもデフォルトの Theme が適用される。Theme を使うときは makeStyles の引数が必要になります。 
  * margin: theme.spacing(1, 1.5), UIの要素間に一貫した間隔を作成します。4つのまでの引数を受け入れます。
  * theme という引数（型は Theme なので theme: Theme と書いている）を指定すると、現在適用される Theme を利用されることになります。 theme をどこかで定義する必要はありません。
* Hooks式
  * @material-ui/core/stylesのmakeStylesを使います。「クラス名とスタイル定義をマッピングしたものを返す関数」を生成するので、あとはその関数をコンポーネント側で使用して取り出し。従来の HTML・CSS でクラスをあてるように、各要素に割り当てていく方式です。
  * Button variant="contained" className={classes.button}


## React Router
Routerの中にRouteを書き、パスとマッチしたときにレンダリングされる要素を指定します。
RouteをSwitchで囲んだ場合は「初めにマッチしたもの」がレンダリングされる、囲まない場合は「マッチするものが全部」レンダリングされます。
* Routeのpathに:（コロン）をつけると、URLパラメータとして使える。match.params.hogeでURLパラメタの内容を取得できる。
* Routeにexactをつけると、設定しているpathが完全一致の場合のみマッチしたことになる




## React Hooks
### useEffect
* useEffectに渡された関数はレンダーの結果が画面に反映された後に動作します。つまりuseEffectとは、「関数の実行タイミングをReactのレンダリング後まで遅らせるhook」です。
* 初回レンダリング時のみ副作用関数を実行させる
  * 副作用関数を初回レンダリング時の一度だけ実行させたい場合、第2引数に空の依存配列[]を指定します。この場合、初回レンダリング時のみ副作用関数が実行され、document.titleは更新されません。
  *  useEffect(() => { dousa wo kaku }, [ ] )
# Phoenixで Error: Node Sass does not yet support your current environmentになった話

## 先日phoenixでphx.servreしたらこんなエラーがでた
```
ERROR in ./css/app.scss
Module build failed (from ./node_modules/mini-css-extract-plugin/dist/loader.js):
ModuleBuildError: Module build failed (from ./node_modules/sass-loader/dist/cjs.js):
Error: Node Sass does not yet support your current environment: OS X 64-bit with Unsupported runtime (88)
For more information on which environments are supported please see:
https://github.com/sass/node-sass/releases/tag/v4.14.1
......
......
......
```

今までこんなエラーは出たことなかったのでびっくりした...
nodeのバージョンがサポートされてない？？

## 心当たり
強いて言えば、この間vueの勉強をしようとしてnode.jsを入れた。バージョンを見てみる。
```
node -v
15.x.x
```
おそらくバージョンが高すぎてだめなのだろう。
ダウングレートするしかないな。

## どうせならバージョン管理したいな

### *[この記事良さそう](https://qiita.com/1000ch/items/41ea7caffe8c42c5211c)*

この記事通りにnodenvを入れます。
<br>
次に
```
nodenv install 14.x.x
nodenv rehash
```
<br>
それからそのプロジェクト内で

```
nodenv local 14.x.x
```
<br>
最後に

```
mix phx.server
```
すれば上手くいくと思います。
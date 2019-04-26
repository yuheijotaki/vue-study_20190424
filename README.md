# Vue.js / JSON から情報を引っ張ってくる その14

ポートフォリオサイト 前回の続き

**やったこと**

- デザインいれる
- レスポンシブ
- ソース整理

Github Pages: https://yuheijotaki.github.io/vue-study_20190424/
リポジトリ: https://github.com/yuheijotaki/vue-study_20190424

### Vue.js で変数や mixin を使う

[Vue.jsでSassを使う時にグローバル変数を読み込む方法 - Goota](https://gootablog.com/vuejs-sass-globalvariables) の通りなのですが、 `sass-resources-loader` を npmインストールして、`/build/utils.js` のなか、

```javascript
...
  scss: generateLoaders('sass'),
...
```

を

```javascript
...
  scss: generateLoaders('sass').concat(
    {
      loader: 'sass-resources-loader',
      options: {
        resources: path.resolve(__dirname, '../src/sass/_base.scss')
      }
    }),
...
```

とする

## まとめ

**やりたい（やりたかった）こと**

- 初回ローディング時には `No posts` は非表示
- ヘッダーのチェックボックスのカテゴリーを動的出力 or ループ処理
- 詳細ページの作成

WordPress のテーマ側に組み込むには下記などが参考になりそう
- [wordpress で SNS や SEO に優しい簡単 SPA 作り - Qiita](https://qiita.com/d2cd-kimura/items/c8283849c4dff245d219)
- [WordPressで全面的にVue.jsを導入してみた(SPA実装ではない) - 超空洞](http://itaoyuta.hatenablog.com/entry/2017/12/28/152338)

GWになるので、一回やること整理しつつ次の課題やっていきたいと思います。


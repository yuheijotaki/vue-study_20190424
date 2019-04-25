# Vue.js / JSON から情報を引っ張ってくる その13



[【学習メモ】Vue.js のツボとコツがゼッタイにわかる本 その3](https://yuheijotaki.hatenablog.com/entry/2019/04/05/101951) のデモをベースにしてポートフォリオサイトを作り直す。

Github Pages: https://yuheijotaki.github.io/vue-study_20190424/  
リポジトリ: https://github.com/yuheijotaki/vue-study_20190424



### ファイル構成

```
/src/
└ App.vue
└ main.js
└ /components/
  └ work-header.vue
  └ work-list.vue
  └ work.vue
```

`App.vue` ファイルにて `axios` を使ってJSON取得、 表示判定は `work-list.vue` で行う。  
`work-header.vue` からチェックボックス状態のプロパティと値を `props` して  `work-list.vue` で表示判定  
`work.vue` はアイテム1つ単位の表示専用コンポーネント



### いじった所

WordPress の REST API で取得できるカテゴリーが

```json
[
  0: {
    ...
    category_name: "Front-end ,WordPress"
    ...
  },
  ...
]
```

というオブジェクトになるので、

```javascript
  methods: {
    request: function(){
      axios.get( 'https://works.yuheijotaki.com/wp-json/wp/v2/posts?per_page=100' )
      .then( response => {
        this.works = response.data; // JSONデータの取得
        let obj = this.works;
        Object.keys(obj).forEach((key) => {
          const catName = obj[key].category_name; // この投稿が属するカテゴリー
          if (catName.includes('Front-end')) {
            obj[key].isCatFrontEnd = true;
          } else {
            obj[key].isCatFrontEnd = false;
          }
  ...
```

のように `isCatFrontEnd` のプロパティと `true` or `false` の値をつけた。  
`work-list.vue` の `computed` でこの処理やったほうがスマートそうですが、できるかよく分からずJSONに書き足す形になっちゃいました。



### 残り

- 記述の整理
  - ファイルやパーツ命名のリファクタリング
  - コンポーネントの分け方も見直しをする

- スタイリング
  - 見た目整える
  - レスポンシブ








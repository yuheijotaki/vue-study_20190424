<template>
  <div id="app">
    <work-list v-bind:works="works"></work-list>
  </div>
</template>

<script>
import "normalize.css";
import axios from "axios";
import workList from './components/work-list.vue';

export default {
  name: 'App',
  components: {
    'work-list': workList
  },
  data: function () {
    return {
      works: [],
      // 初回読み込み用のフラグ
      isLoading: false,
      // isLoading: {
        // type: Boolean,
        // default: true
      // },
    }
  },
  created: function(){
    this.request();
  },
  methods: {
    request: function(){
      this.isLoading = true;
      console.log(`timing1:${this.isLoading}`);
      axios.get( 'https://works.yuheijotaki.com/wp-json/wp/v2/posts?per_page=100' )
      .then( response => {
        this.works = response.data; // JSONデータの取得
        let obj = this.works;
        Object.keys(obj).forEach((key) => {
          const catName = obj[key].category_name; // この投稿が属するカテゴリーを判定、オブジェクトに追加
          if (catName.includes('Front-end')) {
            obj[key].isCatFrontEnd = true;
          } else {
            obj[key].isCatFrontEnd = false;
          }
          if (catName.includes('WordPress')) {
            obj[key].isCatWordPress = true;
          } else {
            obj[key].isCatWordPress = false;
          }
          if (catName.includes('Web Design')) {
            obj[key].isCatWebDesign = true;
          } else {
            obj[key].isCatWebDesign = false;
          }
          if (catName.includes('Tumblr')) {
            obj[key].isCatTumblr = true;
          } else {
            obj[key].isCatTumblr = false;
          }
        });
        // console.table(obj);
        this.isLoading = false;
        console.log(`timing2:${this.isLoading}`);
      })
      .catch( error => {
        console.log(error);
      });
    }
  }
}
</script>

<style lang="scss">
html,* {
  margin: 0;
  padding: 0;
}
h1,h2,h3,h4,h5,h6 {
  margin: 0;
  padding: 0;
}
#app {
  font-family: -apple-system, 'BlinkMacSystemFont', Helvetica Neue, Helvetica, Arial, 'Hiragino Kaku Gothic ProN', Meiryo, sans-serif;
  -webkit-text-size-adjust: 100%;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
  font-feature-settings : "palt";
  color: #222;
  font-size: 14px;
  line-height: 1;
  letter-spacing: 0.02em;
}
</style>

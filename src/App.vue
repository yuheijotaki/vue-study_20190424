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
      // 商品リスト
      works: [],
      hoge: [
        {
          id: '01',
          name: '紫いものビスケット',
          price: 1580,
          image: require("./assets/work/01.jpg"),
          isSale: true
        },
        {
          id: '02',
          name: '豆乳のビスケット',
          price: 2480,
          image: require("./assets/work/02.jpg"),
          isSale: false
        },
        {
          id: '03',
          name: 'かぼちゃのビスケット',
          price: 480,
          image: require("./assets/work/03.jpg"),
          isSale: false
        },
        {
          id: '04',
          name: 'カップケーキ',
          price: 1280,
          image: require("./assets/work/04.jpg"),
          isSale: true
        },
        {
          id: '05',
          name: 'トマトのカップケーキ',
          price: 2880,
          image: require("./assets/work/05.jpg"),
          isSale: false
        },
        {
          id: '06',
          name: 'プルーンのカップケーキ',
          price: 2280,
          image: require("./assets/work/06.jpg"),
          isSale: false
        },
        {
          id: '07',
          name: 'ミルクのビスケット',
          price: 2380,
          image: require("./assets/work/07.jpg"),
          isSale: false
        },
        {
          id: '08',
          name: '黒糖のビスケット',
          price: 1680,
          image: require("./assets/work/08.jpg"),
          isSale: true
        },
        {
          id: '09',
          name: 'コーンのラスク',
          price: 1480,
          image: require("./assets/work/09.jpg"),
          isSale: false
        },
        {
          id: '10',
          name: '黒糖のラスク',
          price: 1480,
          image: require("./assets/work/10.jpg"),
          isSale: false
        },
        {
          id: '11',
          name: 'みどりのラスク',
          price: 980,
          image: require("./assets/work/11.jpg"),
          isSale: true
        },
        {
          id: '12',
          name: 'きいろのラスク',
          price: 280,
          image: require("./assets/work/12.jpg"),
          isSale: false
        }
      ]
    }
  },
  created: function(){
    this.request();
  },
  methods: {
    request: function(){
      axios.get( 'https://works.yuheijotaki.com/wp-json/wp/v2/posts?per_page=100' )
      .then( response => {
        this.works = response.data;
        this.works[0].hoge = "fuga";
        console.table(this.works);
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
  font-family: Helvetica Neue, Helvetica, Arial, 'Hiragino Kaku Gothic ProN', Meiryo, sans-serif;
  -webkit-text-size-adjust: 100%;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
  font-feature-settings : "palt";
  color: #444;
  font-size: 12px;
  letter-spacing: .01em;
  line-height: 1.4;
}
</style>

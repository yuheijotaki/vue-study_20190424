<template>
  <div class="wrapper">
    <work-header
      v-bind:count="filteredList.length"
      v-bind:showCatWordPressItem="showCatWordPressItem"
      v-bind:showCatWebDesignItem="showCatWebDesignItem"
      v-bind:showCatTumblrItem="showCatTumblrItem"
      v-on:showCatWordPressItemChanged="showCatWordPressItem=!showCatWordPressItem"
      v-on:showCatWebDesignItemChanged="showCatWebDesignItem=!showCatWebDesignItem"
      v-on:showCatTumblrItemChanged="showCatTumblrItem=!showCatTumblrItem"
    >
    </work-header>
    <main>
      <p :is-loading="true">loading...</p>
      <p v-if="noEntry">Post not found.</p>
      <div class="list">
        <work
          v-for="work in filteredList"
          v-bind:work="work"
          v-bind:key="work.id">
        </work>
      </div>
    </main>
  </div>
</template>

<script>
import workHeader from './work-header.vue';
import work from './work.vue';

export default {
  name: 'workList',
  props: ['works','isLoading'],
  // props: {
    // works: Array,
    // isLoading: Boolean,
    // isLoading: Boolean,
    // isLoading: {
      // type: Boolean,
      // default: false,
      // default: undefined
    // }
  // },
  components: {
    'work-header': workHeader,
    'work': work,
  },
  data: function () {
    return {
      // 各カテゴリーのチェック状態（true:チェックあり、false:チェックなし）
      showCatWordPressItem: false,
      showCatWebDesignItem: false,
      showCatTumblrItem: false,
      // 絞り込み後の投稿が0件用のフラグ
      noEntry: null
    }
  },
  computed: {
    // 絞り込み後の投稿リストを返す算出プロパティ
    filteredList: function () {
      // 絞り込み後の投稿リストを格納する新しい配列
      var newList = [];
      for (var i=0; i<this.works.length; i++) {
        // 表示対象かどうかを判定するフラグ
        var isShow = true;
        // i番目の投稿が表示対象かどうかを判定する
        if (this.showCatWordPressItem && !this.works[i].isCatWordPress) {
          isShow = false;
        }
        if (this.showCatWebDesignItem && !this.works[i].isCatWebDesign) {
          isShow = false;
        }
        if (this.showCatTumblrItem && !this.works[i].isCatTumblr) {
          isShow = false;
        }
        if (isShow) {
          newList.push(this.works[i]);
        }
      }
      if ( newList.length === 0 ) {
        this.noEntry = true;
      } else {
        this.noEntry = false;
      }
      // 絞り込み後の投稿リストを返す
      console.log(`timing3:${this.isLoading}`);
      return newList;
    }
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 50px;
  @include mq() {
    padding: 0 20px;
  }
}
main {
  margin: 50px 0 80px;
  @include mq() {
    margin: 30px 0 40px;
  }
}
.list {
  display: flex;
  flex-wrap: wrap;
}
</style>

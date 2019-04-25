<template>
  <div class="wrapper">
    <work-header
      v-bind:count="filteredList.length"
      v-bind:showCatFrontEndItem="showCatFrontEndItem"
      v-bind:showCatWordPressItem="showCatWordPressItem"
      v-bind:showCatWebDesignItem="showCatWebDesignItem"
      v-bind:showCatTumblrItem="showCatTumblrItem"
      v-on:showCatFrontEndItemChanged="showCatFrontEndItem=!showCatFrontEndItem"
      v-on:showCatWordPressItemChanged="showCatWordPressItem=!showCatWordPressItem"
      v-on:showCatWebDesignItemChanged="showCatWebDesignItem=!showCatWebDesignItem"
      v-on:showCatTumblrItemChanged="showCatTumblrItem=!showCatTumblrItem"
    >
    </work-header>
    <div class="list">
      <work
        v-for="work in filteredList"
        v-bind:work="work"
        v-bind:key="work.id">
      </work>
    </div>
    <template v-if="noEntry">
      <p>no posts</p>
    </template>
  </div>
</template>

<script>
import workHeader from './work-header.vue';
import work from './work.vue';

export default {
  name: 'workList',
  props: ['works'],
  components: {
    'work-header': workHeader,
    'work': work,
  },
  data: function () {
    return {
      // 「セール対象」のチェック状態（true:チェックあり、false:チェックなし）
      showCatFrontEndItem: false,
      showCatWordPressItem: false,
      showCatWebDesignItem: false,
      showCatTumblrItem: false,
      noEntry: false
    }
  },
  computed: {
    // 絞り込み後の商品リストを返す算出プロパティ
    filteredList: function () {
      // 絞り込み後の商品リストを格納する新しい配列
      var newList = [];
      for (var i=0; i<this.works.length; i++) {
        // 表示対象かどうかを判定するフラグ
        var isShow = true;
        // i番目の商品が表示対象かどうかを判定する
        if (this.showCatFrontEndItem && !this.works[i].isCatFrontEnd) {
          isShow = false;
        }
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
      // 絞り込み後の商品リストを返す
      return newList;
    }
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  max-width: 1200px;
  margin: 0 auto;
  padding: 40px 20px;
}
.list {
  margin-top: 40px;
  display: flex;
  flex-wrap: wrap;
}
</style>

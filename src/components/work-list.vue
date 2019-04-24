<template>
  <div class="wrapper">
    <work-header
      v-bind:count="filteredList.length"
      v-bind:showCatWpItem="showCatWpItem"
      v-on:showCatWpItemChanged="showCatWpItem=!showCatWpItem">
    </work-header>

    <div class="list">
      <work
        v-for="work in filteredList"
        v-bind:work="work"
        v-bind:key="work.id">
      </work>
    </div>
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
      showCatWpItem: false,
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
        if (this.showCatWpItem && !this.works[i].isCatWp) {
          // 「セール対象」チェックありで、セール対象商品ではない場合
          isShow = false; // この商品は表示しない
        }
        if (isShow) {
          newList.push(this.works[i]);
        }
      }
      // 絞り込み後の商品リストを返す
      return newList;
    }
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  max-width: 800px;
  margin: 0 auto;
  padding: 40px 20px;
}
.list {
  margin-top: 40px;
  display: flex;
  flex-wrap: wrap;
}
</style>

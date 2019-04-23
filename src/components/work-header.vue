<template>
  <header>
    <div class="result">
      検索結果：<span class="count">{{count}}</span> 件
    </div>
    <div class="condition">
      <div class="target">
        <label>
          <input type="checkbox"
            v-bind:checked="showSaleItem"
            v-on:change="$emit('showSaleItemChanged')"
          > セール対象 <code>{{showSaleItem}}</code></label>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'workHeader',
  props: ['count','showSaleItem']
}
</script>

<style lang="scss" scoped>
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  line-height: 1;
}
</style>

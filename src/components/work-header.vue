<template>
  <header>
    <div class="result">
      検索結果：<span class="count">{{count}}</span> 件
    </div>
    <div class="condition">
      <div class="target">
        <label>
          <input type="checkbox"
            v-bind:checked="showCatWpItem"
            v-on:change="$emit('showCatWpItemChanged')"
          > WordPress <code>{{showCatWpItem}}</code></label>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'workHeader',
  props: ['count','showCatWpItem']
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

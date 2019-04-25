<template>
  <header>
    <h1 class="header_logo">works.yuheijotaki.com</h1>
    <div class="condition">
      <div class="result">
        検索結果：<span class="count">{{count}}</span> 件
      </div>
      <div class="filter">
        <p>filter</p>
        <label>
          <input type="checkbox"
            v-bind:checked="showCatFrontEndItem"
            v-on:change="$emit('showCatFrontEndItemChanged')"
          > Front-End
        </label>
        <label>
          <input type="checkbox"
            v-bind:checked="showCatWordPressItem"
            v-on:change="$emit('showCatWordPressItemChanged')"
          > WordPress
        </label>
        <label>
          <input type="checkbox"
            v-bind:checked="showCatWebDesignItem"
            v-on:change="$emit('showCatWebDesignItemChanged')"
          > Web Design
        </label>
        <label>
          <input type="checkbox"
            v-bind:checked="showCatTumblrItem"
            v-on:change="$emit('showCatTumblrItemChanged')"
          > Tumblr
        </label>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'workHeader',
  props: [
    'count',
    'showCatFrontEndItem',
    'showCatWordPressItem',
    'showCatWebDesignItem',
    'showCatTumblrItem'
  ]
}
</script>

<style lang="scss" scoped>
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  line-height: 1;
}
.header_logo {
  font-size: 12px;
  line-height: 1;
}
.condition {
  display: flex;
}
.result {
}
.filter {
  display: flex;
}
</style>

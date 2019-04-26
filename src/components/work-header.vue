<template>
  <header>
    <h1 class="logo">works.yuheijotaki.com</h1>
    <div class="filter">
      <p class="label">Filter:</p>
      <div class="check">
        <p>
          <input type="checkbox"
            id="check02"
            v-bind:checked="showCatWordPressItem"
            v-on:change="$emit('showCatWordPressItemChanged')"
          >
          <label for="check02">WordPress</label>
        </p>
        <p>
          <input type="checkbox"
            id="check03"
            v-bind:checked="showCatWebDesignItem"
            v-on:change="$emit('showCatWebDesignItemChanged')"
          >
          <label for="check03">Web Design</label>
        </p>
        <p>
          <input type="checkbox"
            id="check04"
            v-bind:checked="showCatTumblrItem"
            v-on:change="$emit('showCatTumblrItemChanged')"
          >
          <label for="check04">Tumblr</label>
        </p>
      </div>
    </div>
    <div class="result">
      <p>Result <span class="count">{{count}}</span> posts</p>
    </div>
  </header>
</template>

<script>
export default {
  name: 'workHeader',
  props: [
    'count',
    'showCatWordPressItem',
    'showCatWebDesignItem',
    'showCatTumblrItem'
  ]
}
</script>

<style lang="scss" scoped>
header {
  margin-top: 50px;
  display: flex;
  align-items: center;
  line-height: 1;
  @include mq() {
    margin-top: 30px;
    display: block;
  }
}
.logo {
  width: 20%;
  color: #222;
  font-size: 14px;
  line-height: 1;
  font-weight: normal;
  @include mq() {
    width: auto;
    text-align: center;
  }
}
.filter {
  width: 60%;
  display: flex;
  justify-content: center;
  @include mq() {
    width: auto;
    margin-top: 20px;
  }
  .label {
    margin-right: 20px;
    @include mq() {
      display: none;
    }
  }
}
.check {
  display: flex;
  p {
    margin-right: 16px;
    &:last-child {
      margin-right: 0;
    }
    input[type=checkbox] {
      display: none;
    }
    label:focus,
    label:active,
    input:checked + label {
      color: #444;
    }
    label:focus:before,
    label:active:before,
    input:checked + label:before {
      border: #444 1px solid;
      background: #fff;
    }
    label {
      padding-left: 20px;
      position: relative;
      display: block;
      cursor: pointer;
      white-space: nowrap;
      text-overflow: ellipsis;
      background: #fff;
    }
    label:before {
      position: absolute;
      top: 1px;
      left: 0;
      width: 11px;
      height: 11px;
      content: '';
      border: #ccc 1px solid;
      border-radius: 1px;
    }
    input:checked + label:before {
      border: #444 1px solid;
      background: #444;
    }
  }
}
.result {
  width: 20%;
  text-align: right;
  @include mq() {
    display: none;
  }
}
</style>

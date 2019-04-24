<template>
  <div class="item">
    <ul class="icon">
      <template v-if="work.isCatWp">
        <li class="catWp"><span>WordPress</span></li>
      </template>
    </ul>
    <figure>
      <img v-bind:src="work.images.full">
    </figure>
    <div class="meta">
      <p v-html="work.id"></p>
      <p v-html="work.date"></p>
      <p v-html="work.slug"></p>
      <p v-html="work.title.rendered"></p>
      <p v-html="work.acf.post_url"></p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'work',
  props: ['work']
}
</script>

<style lang="scss" scoped>
.item {
  width: 25%;
  padding: 50px 10px 20px;
  border: #ddd 1px solid;
  border-right: 0;
  box-sizing: border-box;
  position: relative;
  &:last-child,
  &:nth-child(4n) {
    border-right: #ddd 1px solid;
  }
  &:nth-child(n+5) {
    border-top: 0;
  }
  figure {
    text-align: center;
    img {
      max-width: 120px;
      height: auto;
      border-radius: 4px;
    }
  }
  .icon {
    position: absolute;
    top: 4px;
    left: 4px;
    display: flex;
    list-style: none;
    li {
      color: #fff;
      font-size: 11px;
      line-height: 1;
      font-weight: bold;
      border-radius: 2px;
      margin-right: 4px;
      &:last-child {
        margin-right: 0;
      }
      span {
        display: inline-block;
        padding: 5px 7px;
      }
      &.catWp {
        background: rgb(240, 53, 53);
      }
    }
  }
  .meta {
    margin-top: 4px;
    text-align: center;
    h2 {
      color: #666;
      font-size: 12px;
    }
    h3 {
      font-size: 16px;
    }
  }
}
</style>

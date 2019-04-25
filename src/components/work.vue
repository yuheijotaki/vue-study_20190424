<template>
  <div class="item"><a v-bind:href="work.acf.post_url" target="_blank">
    <div class="thumbnail">
      <figure class="image"><img v-bind:src="work.images.full"></figure>
    </div>
    <ul class="category">
      <template v-if="work.isCatFrontEnd">
        <li class="catFrontEnd"><span>Front-End</span></li>
      </template>
      <template v-if="work.isCatWordPress">
        <li class="catWordPress"><span>WordPress</span></li>
      </template>
      <template v-if="work.isCatWebDesign">
        <li class="catWebDesign"><span>Web Design</span></li>
      </template>
      <template v-if="work.isCatTumblr">
        <li class="catTumblr"><span>Tumblr</span></li>
      </template>
    </ul>
    <p class="title" v-html="work.title.rendered"></p>
  </a></div>
</template>

<script>
export default {
  name: 'work',
  props: ['work']
}
</script>

<style lang="scss" scoped>
.item {
  width: 22%;
  margin-top: 2%;
  margin-right: 4%;
  &:nth-child(-n+4) {
    margin-top: 0;
  }
  &:nth-child(4n) {
    margin-right: 0;
  }
  a {
    text-decoration: none;
    display: block;
  }
}
.thumbnail {
  position: relative;
}
.image {
  text-align: center;
  font-size: 0;
  line-height: 0;
  img {
    max-width: 200px;
    height: auto;
    box-shadow: 0 0 20px rgba(0,0,0,0.1);
    border-radius: 2px;
  }
}
.category {
  margin-top: 15px;
  list-style: none;
  display: flex;
  justify-content: center;
  li {
    border: #ccc 1px solid;
    padding: 4px 5px;
    margin-right: 5px;
    color: #999;
    font-size: 10px;
    line-height: 1;
    border-radius: 2px;
    background: #fff;
    &:last-child {
      margin-right: 0;
    }
  }
}
.title {
  margin-top: 10px;
  text-align: center;
  color: #222;
  font-size: 13px;
  line-height: 1.4;
}
</style>

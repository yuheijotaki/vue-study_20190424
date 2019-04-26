<template>
  <div class="item"><a v-bind:href="work.acf.post_url" target="_blank">
    <div class="thumbnail">
      <figure class="image"><img v-bind:src="work.images.full"></figure>
    </div>
    <div class="meta">
      <ul class="category">
        <template v-if="work.isCatFrontEnd">
          <li class="catFrontEnd">Front-end</li>
        </template>
        <template v-if="work.isCatWordPress">
          <li class="catWordPress">WordPress</li>
        </template>
        <template v-if="work.isCatWebDesign">
          <li class="catWebDesign">Web Design</li>
        </template>
        <template v-if="work.isCatTumblr">
          <li class="catTumblr">Tumblr</li>
        </template>
      </ul>
      <p class="title">{{work.title.rendered}}</p>
    </div>
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
  width: 20%;
  margin-top: 3%;
  margin-right: 6.6666666666667%;
  &:nth-child(-n+4) {
    margin-top: 0;
  }
  &:nth-child(4n) {
    margin-right: 0;
  }
  @include mq() {
    width: 32%;
    margin-top: 4%;
    margin-right: 2%;
    &:nth-child(-n+4) {
      margin-top: 4%;
    }
    &:nth-child(4n) {
      margin-right: 2%;
    }
    &:nth-child(-n+3) {
      margin-top: 0;
    }
    &:nth-child(3n) {
      margin-right: 0;
    }
  }
  a {
    text-decoration: none;
    display: block;
    &:hover {
      .image {
        transform: scale(.975);
        transform-origin: center;
        @include mq() {
          transform: none;
        }
      }
    }
  }
}
.thumbnail {
}
.image {
  text-align: center;
  font-size: 0;
  line-height: 0;
  transition: .075s linear;
  @include mq() {
    transition: none;
  }
  img {
    max-width: 100%;
    height: auto;
    box-shadow: 0 0 20px rgba(0,0,0,0.15);
    border-radius: 2px;
  }
}
.meta {
  margin-top: 10px;
  .category {
    font-size: 0;
    line-height: 0;
    list-style: none;
    display: flex;
    justify-content: center;
    @include mq(xl) {
      display: none;
    }
    li {
      color: #aaa;
      font-size: 10px;
      line-height: 1;
      display: inline-block;
      position: relative;
      padding-right: 4px;
      &:after {
        content: '/';
        padding-left: 4px;
      }
      &:last-child {
        padding-right: 0;
        &:after {
          content: '';
          padding-left: 0;
        }
      }
    }
  }
  .title {
    margin-top: 4px;
    color: #222;
    font-size: 16px;
    line-height: 1.4;
    text-align: center;
    @include mq() {
      margin-top: 0;
      font-size: 12px;
    }
  }
}
</style>

<style lang="scss" scoped>
  @import 'common/scss/index';
  .tab {
    display: flex;
    width: 100%;
    height: 40px;
    line-height: 40px;
    @include border-1px(rgba(7, 17, 27, 0.1));
    .tab-item {
      flex: 1;
      text-align: center;
      a {
        display: block;
        font-size: 14px;
        color: rgb(77, 85, 93);
        &.active {
          color: rgb(240, 20, 20);
        }
      }
    }
  }
</style>

<template>
  <div>
    <v-header :seller="seller"></v-header>
    <div class="tab">
      <div class="tab-item">
        <router-link to="/goods">商品<i class="icon-check_circle"></i></router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <keep-alive>
      <router-view :seller="seller"></router-view>
    </keep-alive>
  </div>
</template>

<script>
  import header from './components/header/header'
  import axios from 'axios'

  export default {
    data() {
      return {
        seller: {}     
      }
    },
    created() {
      axios.get('static/data.json').then((res) => {
        this.seller = res.data.seller;
      })
    },
    methods: {
    },
    components: {
      'v-header': header
    }
  }
</script>



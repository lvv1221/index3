<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tab border-1px">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <keep-alive>
    <router-view :seller="seller" ></router-view>
    </keep-alive>
  </div>
</template>

<script type="text/ecmascript-6">
  import header from './components/header/header.vue'
  import axios from 'axios'
  import {urlParse} from './common/js/util'
  const ERR_OK = 0
  export default {
    name: 'app',
    components: {
      'v-header': header
    },
    data: function () {
      return {
        seller: {
          id: (() => {
            let queryParam = urlParse()
            // console.log(JSON.stringify(queryParam))
            return queryParam.id
          })()// 立即执行函数
        }
      }
    },
    created: function () {
      axios.get(`/api/seller?id=${this.seller.id}`).then((res) => {
        if (res.data.errno === ERR_OK) {
         // this.seller = res.data.data
          this.seller = Object.assign({}, this.seller, res.data.data)
         // console.log(this.seller)
        }
      })
    }
  }
</script>

<style type="text/stylus" lang="stylus" rel="stylesheet/stylus">
  @import "./common/stylus/mixin.styl"

  #app
    .tab
      display: flex
      width: 100%
      height: 40px
      line-height: 40px
      border-1px(rgba(7, 17, 27, 0.1))
      .tab-item
        flex: 1
        text-align: center
        & > a
          display: block
          font-size: 14px
          color: rgb(77, 85, 93)
          &.router-link-active
            color: rgb(240, 20, 20)
</style>

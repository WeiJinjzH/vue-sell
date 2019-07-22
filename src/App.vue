<template>
  <div>
    <div class="header">
      <v-header></v-header>
    </div>
    <div class="tab">
      <div class="tab-item">
        <a v-link="{path: '/goods'}">商品</a>
      </div>
      <div class="tab-item">
        <a v-link="{path: '/ratings'}">评论</a>
        </div>
      <div class="tab-item">
        <a v-link="{path: '/seller'}">商家</a>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
  import header from 'components/header/header'
  export default {
    components: {
      'v-header': header
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
    .tab
      display: flex
      width: 100%
      height: 40px
      line-height: 40px
      .tab-item
        flex: 1
        text-align: center
        & > a
          display: block
          text-decoration: none
          color: #7e8c8d
          font-size: 14px
          color: rgb(77, 85, 93)
          &.active
            color: rgb(240, 20, 20)
</style>

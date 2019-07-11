
<template>
    <div>
      <div class="title">热销推荐</div>
      <ul>
          <router-link :to="'detail/'+item.id" tag="li" class="item border-bottom" v-for="(item, index) in list" :key="index">
              <img class="item-img" :src="item.imgUrl" alt="">
              <div class="item-info">
                  <p class="iten-title">{{item.title}}</p>
                  <p class="item-desc">{{item.desc}}</p>
                  <button class="item-button">查看详情</button>
              </div>
          </router-link>
      </ul>
    </div>
</template>

<script>
    export default {
        props:{
            list:{
                type: Array
            }
        }
    }
</script>

<style lang="stylus" scoped>
    @import '~styles/mixins.styl';
    .title
        padding-left: .2rem
        height: .8rem
        color: #212121
        font-size: .32rem
        line-height: .8rem
        text-align left 
        background #eee
    .item
        padding .1rem
        display flex
        .item-img
            width 1.7rem
            height 1.7rem
        .item-info
            flex 1
            min-width 0
            padding-left .2rem
            text-align left 
            .iten-title
                line-height .54rem;
                font-size .32rem
                ellipsis()
            .item-desc
                line-height .4rem;
                color #ccc
                ellipsis()
            .item-button
                line-height .4rem
                background #ff9300
                padding 0 .2rem
                border-radius .06rem
                color #fff
                border none

</style>
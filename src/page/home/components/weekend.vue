
<template>
    <div>
      <div class="title">周末去哪</div>
      <ul>
          <li class="item border-bottom" v-for="(item, index) in list" :key="index">
              <img class="item-img" :src="item.imgUrl" alt="">
              <div class="item-info">
                  <p class="iten-title">{{item.title}}</p>
                  <p class="item-desc">{{item.desc}}</p>
              </div>
          </li>
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
        background #fff;
        padding 0rem
        margin-bottom .1rem
        .item-img
            width 100%
        .item-info
            min-width 0
            padding .1rem .2rem
            text-align left 
            .iten-title
                line-height .54rem;
                font-size .32rem
                ellipsis()
            .item-desc
                line-height .4rem;
                color #555
                ellipsis()
         

</style>
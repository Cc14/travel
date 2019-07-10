<template>
    <div class="header">
        <div class="header-left">
            <span class="iconfont">
                &#xe624;
            </span>
        </div>
        <div class="header-input">
            <span class="iconfont">
                &#xe632;
            </span>
            请输入城市景点游玩主题
        </div>
        <router-link to="/city">
            <div class="header-right">     
                {{this.city}}
                <span class="iconfont">
                    &#xe64a;
                </span>
            </div>
        </router-link>
    </div>
</template>

<script>
    import {mapState} from 'vuex'
    export default {
        computed:{
            ...mapState(['city'])
        }
    }
</script>

<style scoped lang="stylus">
    @import '~styles/varibles.styl';
    .header
        display flex
        line-height .86rem
        background $bgColor
        color #fff
        .header-left
            width .64rem
            float left
        .header-input
            flex 1
            margin .12rem .2rem 0 0
            line-height .64rem
            height .64rem
            background #ffffff
            border-radius 5px
            color #ccc
        .header-right
            min-width 1.24rem
            float right
            text-align center
            color #fff
            .iconfont
                font-size 16px
</style>
<template>
    <div class="header">
        城市选择
        <div class="head-back">
            <router-link to="/">
                <span class="iconfont">
                    &#xe624;
                </span>
            </router-link>
        </div>
    </div>
</template>

<script>
    export default {
        name:'CityHeader',
    }
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';
    .header
        position relative
        overflow hidden
        height .86rem
        line-height .86rem
        text-align center
        color #fff
        background $bgColor
        font-size .32rem
        color #fff
        .head-back
            position absolute 
            left 0
            top 0
            width .64rem;
            font-size .4rem
            text-align center
            .iconfont
                color #fff
</style>
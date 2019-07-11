<template>
    <div>
        <div class="banner">
            <img class="banner-img" :src="this.bannerImg" alt="">
            <div class="banner-info">
                <div class="banner-title">{{this.sightName}}</div>
                <div>
                    <span class="icon-font"></span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props:{
            bannerImg:String,
            sightName:String
        }
    }
</script>

<style lang="stylus" scoped>
    .banner
        overflow hidden
        height 0
        padding-bottom 55%
        .banner-img
            width 100%
</style>
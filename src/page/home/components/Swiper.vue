<template>
    <div class="wrapper">
        <swiper :options="swiperOption" v-if="isShow">
            <swiper-slide v-for="(item, index) in list" :key="index">
                <img class="swiper-img" :src="item.imgUrl" alt="">
            </swiper-slide>
            <!--swiper-options-->
            <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
        
    </div>
</template>
 
<script>
    export default {
        props:{
            list:{
                type: Array
            }
        },
        data() {
            return {
                swiperOption:{
                    pagination: '.swiper-pagination',
                    loop: true
                }
            }
        },
        computed:{
            isShow() {
                return this.list.length
            }
        }
    }
</script>

<style scoped lang="stylus">
.wrapper >>> .swiper-pagination-bullet
    margin 0 5px
.wrapper >>> .swiper-pagination-bullet-active
    background #fff
.wrapper
    padding-bottom 31%
    overflow hidden 
    width 100%
    height 0
    font-size 0
    .swiper-img
        width 100%
    .swiper-pagination
        width 100%
        
</style>
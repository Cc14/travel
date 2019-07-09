<template>
    <div class="list" ref="wrapper">
        <div>
            <div class="area">
                <div class="title border-topbottom">当前城市</div>
                <div class="button-list">
                    <div class="button-wrapper">
                        <div class="button">
                            北京
                        </div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">热门城市</div>
                <div class="button-list">
                    <div class="button-wrapper" v-for="(item, index) in hotCities" :key="index">
                        <div class="button">
                            {{item.name}}
                        </div>
                    </div>
                </div>
            </div>
            <div class="area" v-for="(item, key) in cities" :key="key" :ref="key">
                <div class="title border-topbottom">{{key}}</div>
                <div class="item-list" v-for="innerItem in item" :key="innerItem.id">
                    <div class="item border-bottom">{{innerItem.name}}</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import Bscroll from 'better-scroll'
    export default {
        props:{
            cities: Object,
            hotCities: Array,
            letter:String,
            val:String
        },
        mounted() {
            
            this.scroll = new Bscroll(this.$refs.wrapper)
        },
        watch:{
            letter(){
                if(this.letter){
                    let element=this.$refs[this.letter][0]
                    this.scroll.scrollToElement(element)
                }
            },
            val() {
                if(this.val){
                    let element=this.$refs[this.val][0]
                    this.scroll.scrollToElement(element)
                }
            }
        }
        
    }
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';
    .border-topbottom
        &:before
            border 1px solid #ccc
    .list
        overflow hidden
        position absolute 
        top 1.58rem
        left 0
        right 0
        bottom 0
        .title
            padding-left .2rem
            height .54rem
            line-height .54rem
            text-align left 
            background #eee
        .button-list
            overflow hidden
            background #fff
            padding .1rem .6rem .1rem .1rem
            .button-wrapper
                float left 
                width 33.333%     
                .button
                    margin .1rem
                    border .02rem solid #ddd
                    border-radius .06rem
        .item-list 
            background #fff
            .item
                padding-left .2rem
                height .64rem
                line-height .64rem
                text-align left 
</style>
<template>
    <div>
        <div 
            class="item" 
            v-for="(item, index) in list" 
            :key="index"
        >
            <div class="item-title border-bottom">
                <span class="item-icon"></span>
                {{item.title}}
            </div>
            <div v-if="item.children" class="item-children">
                <detail-list :list= "item.children"></detail-list>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name:'detailList',
        props:{
            list:Array
        },
    }
</script>

<style lang="stylus" scoped>
.item   
    text-align left
    padding:0 .2rem
    background url()
    .item-title
        line-height .86rem
        .item-icon
            display: inline-block;
            position: relative;
            width: .36rem;
            height: .36rem;
            top: .1rem;
            left: .15rem;
            background: url(//s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat;
            margin-right: .1rem;
            background-size: .4rem 3rem;
</style>
<template>
    <div>
        <Header></Header>
        <home-swiper :list='swiperList'></home-swiper>
        <Icons :iconList='iconList'></Icons>
        <Recommend :list='recommendList'></Recommend>
        <Weekend :list='weekendList'></Weekend>
    </div>
</template>

<script>
    import Header from './components/Header';
    import HomeSwiper from './components/Swiper'
    import Icons from './components/Icons'
    import Recommend from './components/Recommend'
    import Weekend from './components/Weekend'
    import axios from 'axios'
    export default {
        data() {
            return {
                iconList: [],
                recommendList:[],
                swiperList:[],
                weekendList:[]
            }
        },
        components:{
            Header, HomeSwiper, Icons, Recommend, Weekend
        },
        mounted() {
            this.getHomeInfo()
        },
        methods: {
            getHomeInfo(){
                axios.get('/api/index.json')
                    .then((res)=>{
                        let data = res.data.data
                        this.iconList = data.iconList
                        this.recommendList = data.recommendList
                        this.swiperList = data.swiperList
                        this.weekendList = data.weekendList

                    })
            }
        }
    }
</script>

<style scoped>

</style>
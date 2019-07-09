<template>
    <div>
        <city-header></city-header>
        <city-search :cities="cities"></city-search>
        <city-list :cities="cities" :hotCities="hotCities" :letter="letter"></city-list>
        <city-alphabet @changeKey="handelLetterChagne" :cities="cities"></city-alphabet>
    </div>
</template>

<script>
    import CityHeader from    './components/Header'
    import CitySearch from    './components/Search'
    import CityList from    './components/List'
    import CityAlphabet from    './components/Alphabet'
    import axios from 'axios';
    export default {
        data() {
            return {
                cities: {},
                hotCities:[],
                letter:''
            }
        },
        mounted() {
            this.getCityList()
        },
        components:{
            CityHeader,
            CitySearch,
            CityList,
            CityAlphabet
        }, 
        methods:{
            getCityList(){
                axios.get('./api/city.json')
                    .then((res)=>{
                        let data = res.data.data
                        if(res.status==200 && res.statusText){
                            this.cities = data.cities
                            this.hotCities = data.hotCities
                        }
                    })
            },
            handelLetterChagne(letter){//letter接收从子组件传递过来的数据
                //console.log('我是从子组件传递过来的'+letter)
                this.letter = letter
            }
        }
    }
</script>

<style lang="stylus" scoped>
</style>
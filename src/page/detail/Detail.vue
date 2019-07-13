<template>
    <div>
        <detail-banner 
            :bannerImg="bannerImg"
            :sightName="sightName"   
            :gallaryImgs="gallaryImgs"  
        ></detail-banner>
        <detail-header></detail-header>
        <div class="content">
            <detail-list :list="categoryList"></detail-list>
        </div>
        <div style="height:1000px;"></div>              
    </div>
</template>

<script>
import axios from "axios";
import DetailBanner from "./components/Banner";
import DetailHeader from "./components/Header";
import DetailList from "./components/List";

export default {
  name: "Detail",
  data() {
      return {
          bannerImg: '',
          sightName: '',
          gallaryImgs:[],
          categoryList:[],
          boxShow:false
      }
  },
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
    
  },
  methods: {
      getDetailInfo() {
          axios.get('/api/detail.json')
               .then((res)=>{
                    res=res
                   if(res.status==200 && res.statusText){
                       let data= res.data
                       console.log(data)
                       this.bannerImg=data.data.bannerImg
                       this.sightName=data.data.sightName
                       this.gallaryImgs=data.data.gallaryImgs
                       this.categoryList=data.data.categoryList
                   }
                })
      }
  },
  mounted() {
      this.getDetailInfo()
  }
};
</script>

<style lang="stylus" scoped>

</style>
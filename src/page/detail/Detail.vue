<template>
    <div>
        <detail-banner 
            :bannerImg="bannerImg"
            :sightName="sightName"   
            :gallaryImgs="gallaryImgs"  
        ></detail-banner>
        <!-- <detail-header
            
        ></detail-header> -->
        

    </div>
</template>

<script>
import axios from "axios";
import DetailBanner from "./components/Banner";
import DetailHeader from "./components/Header";

export default {
  name: "Detail",
  data() {
      return {
          bannerImg: '',
          sightName: '',
          gallaryImgs:[]
      }
  },
  components: {
    DetailBanner,
    DetailHeader
    
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
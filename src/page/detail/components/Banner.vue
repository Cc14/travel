<template>
    <div>
        <div class="banner" @click="handleBannerClick">
            <img class="banner-img" :src="this.bannerImg" alt="">
            <div class="banner-info">
                <div class="banner-title">{{this.sightName}}</div>
                <div class="banner-number">
                    <span class="iconfont">&#xe6ac;</span>
                    39
                </div>
            </div>
        </div>
        <fade-animation>
            <gallery     
                :list="gallaryImgs"
                v-show="showGallery"
                @close="handleGalleryClose"
            ></gallery>
        </fade-animation>
    </div>
</template>

<script>
import Gallery from "comment/gallery/Gallery";
import FadeAnimation from "comment/fade/FadeAnimation";
export default {
  props: {
    bannerImg: String,
    sightName: String,
    gallaryImgs: Array,
    
  },
  data() {
    return {
      showGallery: false
    };
  },
  components: {
    Gallery,
    FadeAnimation
  },
  methods: {
    handleBannerClick() {
      this.showGallery = true;
    },
    handleGalleryClose() {
        this.showGallery = false
    }
  }
};
</script>

<style lang="stylus" scoped>


.banner {
    position: relative;
    overflow: hidden;
    height: 0;
    padding-bottom: 55%;

    .banner-img {
        width: 100%;
    }

    .banner-info {
        padding: 0.1rem 0.2rem;
        position: absolute;
        left: 0;
        right: 0;
        bottom: 0;
        display: flex;
        color: #fff;
        text-align: left;

        .banner-title {
            flex: 1;
        }

        .banner-number {
            padding: 0 0.4rem;
            background: rgba(0, 0, 0, 0.8);
            line-height: 0.32rem;
            height: 0.32rem;
            border-radius: 0.2rem;
            font-size: 0.24rem;

            .iconfont {
                display: inline-block;
                position: relative;
                top: 0.02rem;
                font-size: 0.26rem;
            }
        }
    }
}
</style>
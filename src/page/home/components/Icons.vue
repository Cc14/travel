<template>
    <div class="icons">
        <swiper>
            <swiper-slide v-for="(page, index) in pages" :key="index">
                <div class="icon" v-for="(item, index) in page" :key="index">
                    <div class="icon-img">
                        <img class="icon-img-content" :src="item.imgUrl" alt="">
                    </div>
                    <p class="icon-desc">{{item.desc}}</p>
                </div>
            </swiper-slide>
        </swiper>
    </div>
</template>

<script>
export default {
  props:{
    iconList:{
      type : Array
    }
  },
  data() {
    return {  
    }
  },

  computed: {
    pages() {
      const pages = [];
      this.iconList.forEach((item, index) => {
        const page = Math.floor(index / 8);
        if (!pages[page]) {
          pages[page] = [];
        }
        pages[page].push(item);
      });
      return pages;
    }
  }
};
</script>

<style scoped lang="stylus">
@import '~styles/varibles.styl';

.icons {
    padding-top .1rem;
    overflow: hidden;
    height: 0;
    padding-bottom: 45%;
    .icon {
        padding-top .1rem;
        position: relative;
        overflow: hidden;
        float: left;
        width: 25%;
        height: 1.5rem;
        .icon-img {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0.44rem;
            .icon-img-content {
                width 1.1rem;
                height: 1.1rem;
            }
        }
        .icon-desc {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            height: 0.44rem;
            line-height: 0.44rem;
            color: $darkTextColor;
        }
    }
}
</style>
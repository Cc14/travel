<template>
    <div class="header">
        <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
            <span class="iconfont header-abs-back">&#xe624;</span>
        </router-link>
        <div 
            class="header-fixed" 
            v-show="!showAbs"
            :style="opacityStyle"
        >
            <span class="iconfont header-fixed-back">&#xe624;</span>
            景点详情
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    };
  },
  methods: {
    handleScroll() {
      const top = document.documentElement.scrollTop;
      console.log(top)
      if (top > 60) {
        let opacity = top / 140;
        opacity = opacity >1 ? 1 : opacity 
        this.opacityStyle = {opacity}
        this.showAbs = false;
      } else {
        this.showAbs = true;
      }
    }
  },
  activated() {
    window.addEventListener("scroll", this.handleScroll);
  }
};
</script>

<style lang="stylus" scoped>
@import '~styles/varibles.styl';

.header-abs {
    position: absolute;
    left: 0.2rem;
    top: 0.2rem;
    line-height: 0.8rem;
    width: 0.8rem;
    height: 0.8rem;
    border-radius: 0.4rem;
    background: rgba(0, 0, 0, 0.7);
    text-align: center;

    .header-abs-back {
        color: #fff;
    }
}

.header-fixed {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    text-align: center;
    color: #fff;
    line-height: 0.86rem;
    background: $bgColor;
}
</style>